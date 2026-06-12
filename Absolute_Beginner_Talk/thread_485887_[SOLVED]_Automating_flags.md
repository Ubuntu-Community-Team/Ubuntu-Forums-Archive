---
title: "[SOLVED] Automating flags"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by jdrodrig on 2007-06-27
I am noob to linux, and I have a simple question,

I compile fortran code as follows: 
                        f95 file.f90 -fast -openmp -m32 -xvector=simd -xipo=2

how can I summarize all the flags in one? e.g. I would like just to type
                        f95 file.f90 -superfast (or something)?

thanks,

---

### Post by Cypher on 2007-06-27
At the terminal, do the following
```

export superfast="-fast -openmp -m32 -xvector=simd -xipo=2"

```
Then to compile you'd use
```

f95 file.f90 $superfast

```
BASH will fill in the necessary pieces for you, you can now create a file with more of these definitions and before you compile you'd do
```

. ./compile_defs

```
and those definitions would be available to you in that particular shell window..

---

