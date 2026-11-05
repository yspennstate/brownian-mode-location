# The mode of classical and free Brownian motion at large time

Yitzchak Shmalo

Hasebe and Ueda (*Large time unimodality for classical and free Brownian motions with initial distributions*, ALEA 15 (2018) 353-374) proved that if a probability measure mu on the line has a finite exponential quadratic moment, alpha = E exp(eps X^2) < infinity, then mu * N(0, t) is unimodal for t >= 36 log(2 alpha)/eps, with mode in [-sqrt(t)/2, sqrt(t)/2]. Their Problem 4.6 asks where the mode is, and the same for free Brownian motion mu ⊞ S(0, t), which need not be unimodal.

The paper shows that for large t both densities have a unique global maximum, and that both maxima lie within O(1/t) of the mean m of mu:

    M_c(t) = m - mu_3/(2t) + (mu_5 - 6 mu_2 mu_3)/(8 t^2) + O(t^-3),
    M_f(t) = m - 3 mu_3/t  + (5 mu_5 - 22 mu_2 mu_3)/t^2   + O(t^-3),

where mu_k are the central moments. Explicit bounds |M_c(t) - m| <= M_3/t and |M_f(t) - m| <= 64 (B^3 + M_3)/t hold from explicit times on, with constants that can be written in eps and alpha alone. In the free case uniqueness of the global maximum needs only a finite variance v, for t > 7(7 + 4 sqrt 2) v. The free part uses Biane's description of the free convolution with a semicircle law.

## Contents

- `paper/main.tex`, `paper/main.pdf`: the paper.
- `code/checks.py`: for four finitely supported laws, finds both global modes by grid search and Newton's method at 40-digit precision (the free mode through Biane's parametrization), compares them with the two-term expansions for t = 100, ..., 1600, and checks the explicit bounds above their thresholds. Output in `code/checks_out.txt` and `code/checks.json`.
- `lean/Algebra.lean`: the polynomial identity used for concavity in the free case and the coefficient arithmetic of the free expansion, checked with Lean 4 and Mathlib. The analysis is not formalized.

## Running

    cd code
    python checks.py > checks_out.txt

The program needs `mpmath` and takes several minutes. The Lean file compiles inside any Lean 4 project with Mathlib (`lake env lean Algebra.lean`).

## License

Paper: CC BY 4.0. Code: MIT.
