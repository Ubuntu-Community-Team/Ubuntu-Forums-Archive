---
title: "Phatch Gui"
date: 2009-11-08
forum: Art &amp; Design
---

### Post by Rodney9 on 2009-11-08
G'Day, 
I installed Phatch, but it does not show in the 'Applications Menu' anywhere.
If I try to run it in a terminal I get the following -

> $ phatch
Only the command line package 'phatch-cli' seems to be installed.
Please install the graphical user interface package 'phatch' as well.

How do you use it ?

Thanks, Rodney

PS: is there any exif viewers out there, Gimp seemingly can't show them.

---

### Post by stani on 2009-11-08
> **Rodney9 said:**
> G'Day, 
I installed Phatch, but it does not show in the 'Applications Menu' anywhere.
If I try to run it in a terminal I get the following -



How do you use it ?

Thanks, Rodney

PS: is there any exif viewers out there, Gimp seemingly can't show them.
This is a bug in the software centre:
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/461334](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/461334)

Please subscribe to the bug or check "affects me too".

You can install phatch by:
```
sudo apt-get install phatch
```

or from Synaptic.

Phatch has a built in exif viewer, just drag and drop image file(s) to the image inspector (under Tools menu).

---

### Post by Rodney9 on 2009-11-09
Thank You Stani, > sudo apt-get install phatch did fix it all.

Rodney

---

