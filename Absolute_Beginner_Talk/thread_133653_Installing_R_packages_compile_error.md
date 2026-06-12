---
title: "Installing R packages compile error"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by myotis on 2006-02-20
I am brand new to Linux, having installed Ubuntu this afternoon.

I have installed R and then tried to add some add-in packages. The initial attempt gave me 16 non-zero exit errors (whatever they are), but when I ran Rcmdr from R the main package I was installing. which is dependent on the other packages, it seemed to re-install several of them but failed with three.

The error message this time was

*installing *source* package 'mvtnorm'...
**libs
/usr/lib/R/bin/SHLIB: line 102:make;command not found
ERROR: complilation failed fro package 'mvtnorm'
**Removing '/usr/local/lib/R/site-library/mvtnorm' 

Can anyone shed any light on this.

Many thanks,

Graham

---

### Post by nickle on 2006-02-20
It appears you have not installed make...

Have you installed the basic development package? It should cover most of the tools you need for compilation

sudo apt-get install build-essential

You may also have to install a specific compiler depending the lagnuage in which the R package you want to install is written. You can search for them in synaptic, the package manager.

Let me know how you get on...

---

### Post by nickle on 2006-02-20
I have just noticed that mvtnorm is also available in the repository. you can install this through synaptic, as well as many other R packages. In synaptic you can scroll through them all; they are located in the mathematics (universe) section. Alternatively you can simply get the package using apt, assuming you already know the exact name of the package:

sudo apt-get install r-cran-mvtnorm


This approach will save you having to compile the packages...

---

### Post by myotis on 2006-02-20
Thanks,

I downloaded build-essential, which didn't solve the problem, but downloading the precompiled versions seem to solve it.

I shall have a look at what is needed to compile the R packages, just in case not all are available in the Ubuntu respostieries.

Very appreciatie of the quick reply :-)

Graham

---

