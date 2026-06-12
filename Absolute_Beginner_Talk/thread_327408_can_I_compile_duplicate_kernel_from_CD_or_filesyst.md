---
title: "can I compile duplicate kernel from CD or filesystem?"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by directcharitycontribution on 2006-12-29
Using Edgy 6.10 I want to try an a more specific kernel configuration to the system hardware while keeping an original current generic kernel configuration. 

As this is preparatory to making the networking working I want to know if and how I can do this from the current files on PC or with the install CD.

---

### Post by neowolf on 2006-12-29
Using the Install CD as a repo do 'apt-get install build-essential'.
Then download a kernel bzip from kernel.org, transfer it to the computer in question, unpack it and so make menuconfig to configure and compile your new kernel, the default kernel from Ubuntu will stay on the system and in the GRUB menu unless you remove it.

---

### Post by directcharitycontribution on 2006-12-29
hi thanx for that reply. 

glad it may be a matter of addition and option. but why, as the current kernel assumedly is at stasis, cant the extant kernel be duplicated and MODIFIED to produce an secondary alternatively configured kernel?

what is kernel bzip? which one should be used?

is make menuconfig already 'in system'?

is there any way to get there without any further downloadings?

---

### Post by directcharitycontribution on 2006-12-29
can it be done from the already available resources? no further downloads. 

the internet went slow in asia because of the earthquake breaking the connection so linux updating if not necessary would be preferable.

---

### Post by directcharitycontribution on 2006-12-30
what about detailing for modules?

---

### Post by psycho78 on 2006-12-30
If I understand you right, you only want to change the existing kernel a little? Then you will find anything on CD. You can install linux-source and / or linux-headers from cd, after installing you will find everything you need under /usr/src .... then you can follow a howto to copy the .config from the original kernel and change your settings with make menuconfig... this is too much to explain here for me.. :) but you can search for building custom kernel "the debian way..." this is how i do it and this is pretty easy... you also need to install the  "kernel-package" for this...

regards,
psycho78

---

### Post by directcharitycontribution on 2006-12-30
> **neowolf said:**
> Using the Install CD as a repo do 'apt-get install build-essential'.
Then download a kernel bzip from kernel.org, transfer it to the computer in question, unpack it and so make menuconfig to configure and compile your new kernel, the default kernel from Ubuntu will stay on the system and in the GRUB menu unless you remove it.
this is done in what locations?

---

### Post by directcharitycontribution on 2007-01-02
> **psycho78 said:**
> If I understand you right, you only want to change the existing kernel a little? Then you will find anything on CD. You can install linux-source and / or linux-headers from cd, after installing you will find everything you need under /usr/src .... then you can follow a howto to copy the .config from the original kernel and change your settings with make menuconfig... this is too much to explain here for me.. :) but you can search for building custom kernel "the debian way..." this is how i do it and this is pretty easy... you also need to install the  "kernel-package" for this...

regards,
psycho78

Hi. Thank for reply.

Yeah like take me straight to QueenB OK. I only want .... to change kernel configuration .... ENOUGH. With minimal process. I need this setup to go ontheline and the desktop CD ISO is deficient of some useful packages!

---

### Post by MrHorus on 2007-01-02
> **directcharitycontribution said:**
> 
glad it may be a matter of addition and option. but why, as the current kernel assumedly is at stasis, cant the extant kernel be duplicated and MODIFIED to produce an secondary alternatively configured kernel?


Because once something is compiled it is changed from the sourcecode and cannot be modified.

The only way to "change" an already compiled kernel is with the use of kernel modules, otherwise you have to upgrade the whole thing or compile from source.

---

### Post by directcharitycontribution on 2007-01-02
this point I want from A to B.

A current resources system not working
B current resources system working

which would be most effective and stable, new kernel or kernel modulation?

---

