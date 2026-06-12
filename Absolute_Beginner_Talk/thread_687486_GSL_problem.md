---
title: "GSL problem"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by dgolez on 2008-02-04
HI!
Don't know if this is the right place for this question but still. I'm using Eclipse(CDT) for C programming. Then I tried GSL and I can't compile program:

#include<stdio.h>
#include<gsl/gsl_sf_bessel.h>


int main (void)
{
double x = 5.0;
double y = gsl_sf_bessel_J0(x);
printf("J0(%g) = %.18e\n", x, y);
return 0;
}
There is undefined reference error. But I can compile this without a problem:
 #include<stdio.h>
#include<gsl/gsl_math.h>


int main (void)
{
printf("%f\n", M_E);
return 0;
}

Can anyone help me?? Or is there any good GSL forum where I could ask?
Thanks

---

### Post by rye_ on 2008-02-11
Hi

make sure you install the appropriate libraries;
sudo apt-get install libgsl0 libgsl0-dev


Take it from there.

---

