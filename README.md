# DPYD HapB3 HRM analysis

Analysis code for the manuscript *Blinded Cross-Institutional Validation of a
DPYD HapB3 HRM Assay Using Dried Blood Spots*.

The notebook reads the raw melting data directly from the Rotor-Gene 6000 run
file and reproduces Figures 3 and 4 of the paper. A `.rex` file is plain XML, so
no instrument software is needed.

## Contents

| File | Description |
|---|---|
| `hrm_analysis.ipynb` | Analysis notebook: reads the run file, normalises the melt curves, and writes both figures |
| `Mamandi_raw_file.rex` | Raw Rotor-Gene 6000 run file (72 positions, 36 loaded) |
| `Figure3_synthetic_controls.svg` | HRM profiles of the synthetic GG, GA and AA controls |
| `Figure4_clinical_samples.svg` | HRM profiles of the clinical DBS samples |

## Method

Curves are normalised by setting the mean fluorescence between 74.0 and 76.0 °C
to 100% and between 82.5 and 84.5 °C to 0%, which removes differences in the
amount of PCR product between tubes. Derivative curves are obtained by
Savitzky-Golay differentiation over a 1.0 °C window. Difference plots are each
normalised curve minus the mean normalised wild-type curve.

Samples are considered evaluable if the raw melt fluorescence range exceeds
25 units; tubes below that threshold are reported as amplification failures and
are not assigned a genotype.

## Running it

```
pip install numpy scipy matplotlib
jupyter notebook hrm_analysis.ipynb
```

Run the cells top to bottom. Both SVG figures are written to the working directory.

## Data

The run file contains anonymised position numbers only. It holds no patient
identifiers.

## Licence

MIT (see `LICENSE`).
