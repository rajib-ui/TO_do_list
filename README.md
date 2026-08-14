# Experiment 3 — Sampling, Aliasing and Reconstruction

## 📌 Overview

This experiment demonstrates the **Sampling Theorem, aliasing, and signal reconstruction using sinc interpolation**.

A two-tone signal is sampled at three different sampling rates:

* Above the Nyquist rate
* At the Nyquist rate
* Below the Nyquist rate

The original and reconstructed signals are analyzed in both the **time and frequency domains**.

OUTPUT LINK: https://colab.research.google.com/drive/1baBsgCoLmyjHJSoI8wKHvpBh_yTwdWR2#scrollTo=nvSbCn0Nx5yG&fullscreenOutput=true

## 🎯 Objectives

* Verify the Sampling Theorem.
* Visualize aliasing.
* Reconstruct the sampled signal using sinc interpolation.
* Calculate reconstruction error.
* Identify and verify the aliased frequency.

## 📐 Signal Used

[
x(t)=\sin(2\pi f_1t)+0.5\sin(2\pi f_2t)
]

Parameters:

* (f_1 = 10) Hz
* (f_2 = 30) Hz
* (f_{max} = 30) Hz
* Nyquist rate = (2f_{max}=60) Hz

### Sampling Cases

| Case          | Sampling Rate | Condition     |
| ------------- | ------------: | ------------- |
| Above Nyquist |        100 Hz | (f_s > 60) Hz |
| At Nyquist    |         60 Hz | (f_s = 60) Hz |
| Below Nyquist |         40 Hz | (f_s < 60) Hz |

## 🔄 Sinc Reconstruction

The sampled signal is reconstructed using:

[
x_r(t)=\sum_n x[n],
\mathrm{sinc}\left(\frac{t-nT_s}{T_s}\right)
]

where (T_s=1/f_s).

## ⚠️ Aliasing Validation

For the undersampled case:

[
f_s=40\text{ Hz}
]

The 30 Hz component aliases to:

[
f_{alias}=|30-40|=\boxed{10\text{ Hz}}
]

The calculated 10 Hz alias is verified using the simulated magnitude spectrum.

## 📊 Visualizations

The program generates:

* Reference and sampled signals
* Sinc-reconstructed waveform
* Magnitude spectra
* Reconstruction error

## 💻 Implementation

The simulation is implemented in **Python** using:

* NumPy
* Matplotlib

The physical sampling rate is kept separate from the high-resolution plotting grid used for visualization.

## 🔍 Expected Results

* **100 Hz:** No aliasing and good reconstruction.
* **60 Hz:** Theoretical Nyquist boundary; numerical reconstruction error may occur.
* **40 Hz:** Aliasing occurs and the 30 Hz component appears at 10 Hz.

## 📁 Files

```text
Experiment-3/
│
├── experiment3.py
├── README.md
└── results/
    ├── sampling_100Hz.png
    ├── sampling_60Hz.png
    └── sampling_40Hz.png
```

## ✅ Conclusion

The experiment verifies that a signal must be sampled at or above twice its highest frequency for ideal reconstruction. When the sampling frequency falls below the Nyquist rate, **aliasing occurs**, causing irreversible frequency distortion.
