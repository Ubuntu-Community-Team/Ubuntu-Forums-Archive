---
title: "Add printing to server install w/ XFCE4"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by BirdZerk on 2007-07-03
I have a P3 667mhz (128mb ram) that I just brought back to life with the mini CD server install.  I chose XFCE4 as my DE and it is running great, the only thing I am not quite sure of yet is how to get the printing working.  I have seen that XFCE has there own printer GUI called xfprint, but again I am not sure how to set any of it up.  What I need to know is what to install and what needs to be entered to be able to print.

---

### Post by moore.bryan on 2007-07-03
*use the cups interface ([localhost:631]("http://localhost:631"))... to read a little more, check the [cups documentation]("http://www.cups.org/documentation.php").*

---

### Post by BirdZerk on 2007-07-04
When I type [http://localhost:631/](http://localhost:631/), nothing happens.  As I thought, with a server installation there is no printing software installed.

---

### Post by moore.bryan on 2007-07-04
[I]sorry... i thought since you had xprint installed, cups was autoinstalled.  just install cups and you'll be able to use the localhost config...
```
sudo aptitude install --with-recommends cups
```
[/I]

---

### Post by Brian96 on 2007-07-07
> **moore.bryan said:**
> [I]sorry... i thought since you had xprint installed, cups was autoinstalled.  just install cups and you'll be able to use the localhost config...
```
sudo aptitude install --with-recommends cups
```
[/I]

Not 100% sure, but I think the package is "cupsys" not "cups."

I was able to get mine going with "sudo aptitude install cupsys."

---

### Post by moore.bryan on 2007-07-08
> **Brian96 said:**
> Not 100% sure, but I think the package is "cupsys" not "cups."

I was able to get mine going with "sudo aptitude install cupsys."
[I]that's correct; typo by me.
;-)[/I]

---

### Post by BirdZerk on 2007-07-09
Is there an extra package that needs to be install to add more HP printer drivers?

---

### Post by Brian96 on 2007-07-10
> **BirdZerk said:**
> Is there an extra package that needs to be install to add more HP printer drivers?

Check synaptic, but I think I remember the full Ubuntu having an HP printer utility on it. Do you already have that installed?

---

