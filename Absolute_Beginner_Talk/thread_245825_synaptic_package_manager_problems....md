---
title: "synaptic package manager problems..."
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by theadventuresofanidealist on 2006-08-28
in my status menu i get a choice of :

installed
not installed
installed (local or obsolete) what does this mean?
should i remove these packages?

---

### Post by elettronicha on 2006-08-28
"installed (local or obsolete)" packages are:
1- those installed with other methods than apt-get or synaptic, e.g. those you compile and install on your own (local). 
2- those not present in your current repositories, but in older ones (obsolete).

You don't have to remove them.

---

### Post by Omnios on 2006-08-28
> **theadventuresofanidealist said:**
> in my status menu i get a choice of :

installed
not installed
installed (local or obsolete) what does this mean?
should i remove these packages?

 In synaptic installed is all the files installed with the synaptic package manager which is all files intalled and updated with install and synaptic.

 not installedare packages are packages in synpaptic that are not intalled yet.
 Local and obsolete are packages that where intalled with dpkg -i command, in other words downloaded deb packages. 

 ALso there is broken wich are intalls that when't wrong. Proken packages should be removed but the others are ok.

---

### Post by theadventuresofanidealist on 2006-08-28
thanks for the help :)

---

