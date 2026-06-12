---
title: "Dos2unix How to?"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by prophet of the pimps on 2007-01-01
i got the latest version of ubuntu and i am ring to install my wifi card on ubuntu using the RT61 driver for D-link DWL-G630

and i can do everything except dos2unix

how do i do dos2unix.

i am still a newbie so yu will have to be patient with me. ;)

---

### Post by kidders on 2007-01-01
Hi there,

The dos2unix tool has nothing to do with wireless LAN cards, I'm afraid. It's used to convert Microsoft's weird 2-character line breaks to normal ones. Eg: **dos2unix -n weird.txt normal.txt**

---

### Post by taurus on 2007-01-01
Maybe you are thinking about ndiswrapper, installing a Windows driver for your wireless card!

---

### Post by kstembri on 2007-03-24
Hi folks, 
I found this thread when I needed to use dos2unix, which is not installed out of the box on Ubuntu. No answer though, so my next stop was Google.

So for the benefit of others, it is part of the tofrodos package which can be installed by Synaptic.

HTH

---

