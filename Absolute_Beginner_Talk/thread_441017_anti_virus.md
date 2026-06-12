---
title: "anti virus"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-05-12
Hi guys, i need an anti virus that will scan windows partitions and run on Ubuntu or Kubuntu live CD

---

### Post by hyper_ch on 2007-05-12
Download one from the repositories :)

---

### Post by 3rdalbum on 2007-05-12
I'd suggest downloading the KlamAV package on the Live CD; this will install ClamAV and the best graphical frontend for it. Unfortunately, it will pull in some KDE dependencies too which will take up some bandwidth, but it's worth it.

You might want to consider using Reconstructor to create a customised Live CD with the KlamAV package preinstalled.

---

### Post by Pistolla on 2007-05-12
the clamAV works both under (K)(X)Ubuntu and Windows. At the same time, if i read what you are sayin', i don't know. I dual-boot. Since, i guess ther's a possobility that a virus can migrate to the Linux system, i better consider it my self. Normally, in my case, i do windows stuff undwer windows and linux stuff under linux with little or no fear. If you dual-boot then have an AV on each as i do. i hardly if ever use windows my wife does use it. She has gotten better over the past month or so and is using linux. 
Back to what i was sayin use clamAV and it should have the option to check the partition.
i haven't seen clam on the reos, per se, but there many place/programs here on the forums that you can find it easily. i use Automatix ([http://www.getautomatix.com/](http://www.getautomatix.com/)) and it carries all the repos stuff and it integates nicely with the Ubuntu system. It works w/out messing anything up. There are also other 3rd party stuff on the forums (aooropriately under 3rd party) and ther are threads/links to how to get the AV and stuff. i think you find help under the UDSF section on this forum fromt page.
Hope this helps and happy \puting

---

### Post by Wiebelhaus on 2007-05-12
I"m using [F-prot]("http://ubuntuforums.org/showthread.php?t=88357&highlight=install+f-prot") for this very thing.

---

### Post by Najand on 2007-05-12
F-prot can be installed through multiverse/utils repository; Enable it and:
```

sudo apt-get install f-prot-installer

```

---

