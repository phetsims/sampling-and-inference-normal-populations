# Sampling and Inference: Normal Populations - Model Description

This document is a high-level description of the model used in Sampling and Inference: Normal Populations. It is
intended for teachers and students who want to know what the simulation computes and what it simplifies.

## Populations

Every population in the simulation is a normal distribution described by two parameters: its mean, μ, and its standard
deviation, σ. A population is a theoretical, infinite population. The simulation never stores a list of "everyone in
the population"; it only draws samples from the distribution. The curve shown for a population is the normal density
with that μ and σ.

Because μ and σ belong to the population, they are called **parameters** and they never change from sample to sample.
The mean and standard deviation of a sample are called **statistics**, and they change every time a new sample is
taken.

## Samples

A sample of size n is n values drawn independently and at random from a population. For each sample the simulation
computes:

- the sample mean, x̄, the average of the values;
- the sample standard deviation, s, using n − 1 in the denominator;
- the standard error of the mean, SE = s / √n, which estimates how much x̄ would vary from sample to sample.

A sample of one value has a mean but no standard deviation, so no standard error, p-value, interval or effect size is
shown for it.

The histogram groups values into bins of a fixed width. A value that falls exactly on a bin edge is counted in the bin
to its right.

## Comparing two samples

All comparisons are made as sample 1 minus sample 2 (on the experiment screens, control minus treatment).

- **Standard error of the difference** (unpooled): SE = √( s₁²/n₁ + s₂²/n₂ ).
- **Degrees of freedom**: the Welch–Satterthwaite approximation, which does not assume the two populations have the same
  spread.
- **p-value**: the two-sided p-value of Welch's t-test, t = (x̄₁ − x̄₂) / SE. A small p-value means a difference this
  large would rarely happen by chance if the population means were equal.
- **Confidence interval**: (x̄₁ − x̄₂) ± t* · SE, where t* (shown as the "number of standard errors") is the critical
  value of the t distribution for the chosen confidence level and degrees of freedom.
- **Effect size** (experiment screens): Cohen's d, the distance between the group means measured in pooled standard
  deviations.

The simulation shows evidence on a scale from "weaker" to "stronger" rather than declaring a result significant or not,
because whether a p-value is small enough depends on the context and the field.

## The contexts

| Screen | Context | Quantity | Units |
|---|---|---|---|
| Intro | Heights of children and adults | height | inches or centimeters |
| Sampling | Animal weights | weight | pounds or kilograms |
| Sampling | Reaction times | time | milliseconds |
| Sampling | Blood pressure | systolic pressure | mmHg |
| Sampling | Custom | value you set | none |
| Assignment, Experiments | Mice completing a task | time | seconds |

Height data are typical values for each group. The mystery populations are real groups whose identity the
simulation does not reveal. The Sampling contexts' values are illustrative.

## The experiment

On the Assignment and Experiments screens, each experimental unit is a mouse, and the response is the time it takes the
mouse to complete a task. Mice in the control group have times drawn from a normal distribution with μ = 50 s and
σ = 4 s. Mice given a treatment have times drawn from that treatment's distribution at the chosen dose:

- **Treatment A** lowers the mean time steadily as the dose increases and leaves the spread unchanged.
- **Treatment B** barely changes the mean time but makes times more variable at high doses.
- **Treatment C** helps most at a low dose and makes times longer at high doses.
- **Custom Treatment** (Experiments screen) uses a mean and standard deviation you choose.

At a dose of 0 mg every treatment is identical to the control.

## Simplifications

- Populations are exactly normal; real height, weight and reaction-time data are only approximately normal.
- Draws are independent, as if sampling with replacement from an infinite population.
- Random assignment on the Assignment screen moves the selected mice into groups at random. Because every mouse's
  response is drawn fresh from its group's distribution, which mouse lands in which group does not change the
  statistics; it shows the process.
- The heights in centimeters are converted from inches.
