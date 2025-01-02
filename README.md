### Abstract
I utilize the Polya tree method to implement a nonparametric Bayesian test. This approach allows us to compare galaxy properties between dense regions (voids) and less dense regions (walls) identified by two void-detection algorithms, VoidFinder and V², using data from the SDSS catalog and the DESI DR1 catalog.

## Background
Galaxies in the universe are distributed in a web-like structure and they are constantly being influenced by their surroundings. I'm especially interested in studying the properties of galaxies in different regions of the sky: in dense regions (“walls”) where galaxies interact, causing accelerated evolution; and in sparse regions (“voids”), where galaxies evolve in relative isolation and are observed to have delayed evolution. Studying galaxies in these populations provides critical hints about the processes that drive their evolution. 

## Nonparametric Bayesian Method
I consider a robust quantity, the Bayes factor, which takes into account both the null hypothesis H0 (single parent) and the alternative hypothesis H1 (two-parent). Given data D, the Bayes Factor is the ratio of the marginal likelihoods of D given each hypothesis and measures the strength of the evidence against the null hypothesis. 

$$ B_{01} = \frac{\Pr(\mathbf{D} \mid H_0)}{\Pr(\mathbf{D} \mid H_1)}. $$

| Value of $$\ B_{01} \$$      | Value of $$\ log(B_{01}) \$$  | Evidence against $$\ H_0 \$$               |
|-----------------------------|--------------------------|------------------------------------------|
| 1 to 0.32                   | 0 to -1/2               | Not worth more than a bare mention      |
| 0.32 to 0.1                 | -1/2 to -1              | Substantial                             |
| 0.1 to 0.01                 | -1 to -2                | Strong                                  |
| < 0.01                      | < -2                    | Decisive                                |


I aim to apply the non-parametric two-sample Bayesian test in this project. Pólya tree prior, a prior distribution that constructs probability distributions through recursive partitioning, can be used to derive the Bayes factor of the non-parametric test. It can accommodate known uncertainty in the form of the underlying sampling distribution and provides an explicit posterior probability measure of both dependence and independence. 

Pólya tree prior parameters:

𝞱: the probability of turning left.  𝞱 ~ 𝑩𝒆𝒕𝒂(𝞪₀, 𝞪₁), where 𝑩𝒆𝒕𝒂(𝞪₀, 𝞪₁) = Γ(𝞪₀) Γ(𝞪₁) / Γ(𝞪₀ + 𝞪₁)

𝞪: constant at level 𝞪₀ = 𝞪₁ = 𝒄𝒎²

𝒎: depth of the tree

𝒄:  free variable, ideally between 1 and 10. A larger 𝒄 reduces variance, forcing distributions more similar

## Getting the Dataset
I use the SDSS NSA (NASA-Sloan Atlas) catalog and a version of the DESU DR1 catalog called the FastSpecFit Iron VAC. 

[Description of NSA](http://www.nsatlas.org/data)

[Description of FastSpecFit](https://fastspecfit.readthedocs.io/en/latest/fastspec.html).

Access FastSpefit through NERSC: `/global/cfs/cdirs/desi/public/dr1/vac/dr1/fastspecfit/iron/v2.1`

## Conclusion
Log Bayes factors for various galaxy properties in my study $$\(c = 1, m = 8\)$$

|                | Stellar Mass | g-r   | u-r   | Magnitude | SFR   | sSFR  |
|----------------|--------------|-------|-------|-----------|-------|-------|
| **VoidFinder** | -3896        | -3847 | -3608 | -2901     | -895  | -3247 |
| **V²**         | -280         | 123   | 80    | -547      | -58   | 161   |

Using 𝐕², I observe little differences between the properties of void and wall galaxies, particularly regarding color distributions (g-r, u-r) and specific star formation rates sSFR. 

Conversely, the 𝐕𝐨𝐢𝐝𝐅𝐢𝐧𝐝𝐞𝐫 catalog shows that the property distributions of void galaxies are significantly different from those in denser regions. 

## Tools I Use

<div>
  <img src="https://github.com/devicons/devicon/blob/master/icons/python/python-original-wordmark.svg" title="Python" alt="Python" width="40" height="40"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/jupyter/jupyter-original-wordmark.svg" title="Jupyter" alt="Jupyter" width="40" height="40"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/r/r-original.svg" title="R" alt="R" width="40" height="40"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/anaconda/anaconda-original-wordmark.svg" title="Java" alt="Java" width="60" height="60"/>&nbsp;
</div>

