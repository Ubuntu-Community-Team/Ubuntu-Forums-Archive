---
title: "Python 3 and non 3 designated libraries"
date: 2012-11-09
forum: Any Other OS
---

### Post by kiwi9 on 2012-11-09
I have been attempting to set up Python 3 as an alternate to Python 2.7. Linux Mint 13, Cinnamon (Ubuntu 12.04 derivative).

I go fine with the Py3 denoted packages (Numpy3, Scipy3, iPython3) but despite days of searching and breaking my install several times I can't get Py3 to use:
= matplotlib
= pandas
= statsmodels.

Pandas and statsmodels are fully 3 compatible and I've tried matplotlib 1.2 ([http://ubuntuforums.org/showthread.php?t=2010200&highlight=python+3+matplotlib](http://ubuntuforums.org/showthread.php?t=2010200&highlight=python+3+matplotlib))

I have experimented with virtualenv, and after installing Python 3.3 tried the newer venv using the raring depostiories. I've used pip and easy_install from within virtual environments but I hit failures at each point. I've searched forums and the internet. I am obviously not getting "it."

I feel that there must be something simple that I'm not doing.

Can someone please advise:
- how do I force the install of non-3 packages into the 3 environment rather than the default 2.7 environment (as well as is fine)?

Thanks,
A very recent deserter from the MS ship.

---

### Post by MadCow108 on 2012-11-09
I don't know how venv in python3.3 is supposed to work, but python3.2 still works fine (likely even works better because its not brand new)

```
 # needed for scipy which is needed for statsmodels
sudo apt-get install libatlas-dev liblapack-dev gfortran
virtualenv -ppython3 folder/bin/activate
source folder
easy_install numpy
easy_install scipy
easy_install pandas
easy_install statsmodels
easy_install matplotlib
```

matplotlib with python3 support was only released this week, it may have not shown up on pypi yet
you may have to install it manually until its there

---

### Post by kiwi9 on 2012-11-10
Thanks Madcow

---

