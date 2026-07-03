WORK IN PROGESS

# Climate, importation, and immunity shape chikungunya transmission across emerging and endemic settings

Analysis code for a comparative study of chikungunya virus (CHIKV) transmission in an
emerging setting (metropolitan France, 2025) and an endemic setting (Brazil, 2014–2024).
The study asks which constraint: environmental suitability, importation pressure, or
population immunity, limits local transmission in each setting, and how that constraint
shapes the response to 2050 climate, vaccination, and importation scenarios.

---

## Overview

Local transmission is modelled with a semi-mechanistic renewal framework in
which the effective reproduction number is factored into three interpretable components:

```
Reff(t) = α · Renv(t) · S(t)
```

- **α** — a time-invariant, per-setting calibration scalar (estimated on training data only).
- **Renv(t)** — a climate-driven environmental suitability index, mapped onto the
  reproduction-number scale by a calibration constant κ estimated from epidemic take-off windows.
- **S(t)** — time-varying population susceptibility.

This factorisation places importation pressure, environmental suitability, and immunity on a
single transmission scale, allowing the dominant constraint to be identified in each setting
and varied in counterfactual scenarios. Generalised additive models (GAMs) are used to rank
drivers; the renewal model is used for forward simulation, validation, and counterfactuals.

**Settings.** France uses the published *Aedes albopictus* suitability surface (Perkins et al.,
2015) and a hurdle GAM (a binomial gate for whether local transmission occurs and a negative
binomial amplification component). Brazil uses a setting-specific *Ae. aegypti* suitability
surface and a pooled negative binomial GAM across the 133 intermediate geographic regions.

---

## Repository structure

To be added
---

## Data sources

| Domain | Source | Use |
|---|---|---|
| CHIKV cases, France & Réunion | Santé Publique France | Locally acquired and imported case series |
| CHIKV cases, Brazil | InfoDengue | Weekly municipality-level case counts |
| Regional geography, Brazil | IBGE | 133 intermediate geographic regions |
| Air mobility, Brazil | ANAC (via the `flightsbr` R package) | Domestic flight-stage passenger flows |
| Bus mobility, Brazil | ANTT | Intercity passenger boardings |
| Climate reanalysis | ERA5 (Copernicus Climate Change Service) | Observed temperature and precipitation |
| Climate projections | CESM2 SSP2-4.5 | 2050 temperature counterfactuals |
| Population | WorldPop | Population-weighted spatial aggregation |
| Immunity / susceptibility, Brazil | Cortes-Azuero et al., 2025 (*Lancet Infect Dis*) | Age-structured serocatalytic immunity estimates |
| Generation interval | Riou et al., 2017 (Brazil); add (France) | Renewal infectiousness kernel |
| Suitability formulation | Perkins et al., 2015 | *Ae. albopictus* log-suitability surface (France) |

---

## Authors

Rhys P. D. Inward, Cathal Mills, Bernardo Gutierrez, Moritz U. G. Kraemer
Department of Biology and Pandemic Sciences Institute, University of Oxford.

```
