---
title: "broken package"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by stonecoldjha on 2008-04-16

when i try to use the update manager or synaptic package manager,i get the message that i have a broken package on my system and i should use broken filter to locate it,how do i fix this??where is the broken filter,what is it?and,what does this mean?i am totally new to linux.i am presently using ubuntu ultimate 1.7 edition.

---

### Post by philinux on 2008-04-16
Open synaptic, choose custom filter from bottom left. Click on broken.

[https://help.ubuntu.com/community/SynapticHowto#head-7d9acf78affa92a48849d27c6056d31e796c9a13](https://help.ubuntu.com/community/SynapticHowto#head-7d9acf78affa92a48849d27c6056d31e796c9a13)

---

### Post by thenes on 2008-04-16
The error message often gives you an optional way to install the broken package via terminal. If you cannot figure out the filter in synaptic, it can be just as easy to run the command line that you see in the error message in terminal.

---

### Post by Oldsoldier2003 on 2008-04-16
> **thenes said:**
> The error message often gives you an optional way to install the broken package via terminal. If you cannot figure out the filter in synaptic, it can be just as easy to run the command line that you see in the error message in terminal.

```
sudo dkpg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```
and in 99.9% of cases all will be well. if you have any more troubles just let us know what the error message says.

---

