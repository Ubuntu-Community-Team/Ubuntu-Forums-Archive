---
title: "One man writes the original Linux..."
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by the-edmeister on 2008-03-26
and now there are over 100 distros that don't play well together. Newly assembled PC so there are no issues with Windows messing things up.  I originally installed Ubuntu 7.10, then OpenSUSE 10.3 about 2 weeks ago - no problems with those two peacefully coexisting. (on /dev/sda)
I installed a second hard drive (/dev/sdb) and ran GParted to set it up as ext3, for Fedora 8 and probably screwed up by changing the default Fedora install settings to have the boot loader on /dev/sda. Somehow the Fedora LiveCD version of GParted didn't use the existing piece of the hard drive where the GRUB already existed - it took Ubuntu's /home directory, so I have a boot partition of ~2.0GiB and neither Ububtu nor OpenSUSE will load.
```
Booting 'Ubuntu'
rootnoverify (hd 0,4)
chainloader +1 
``` Yeah, /dev/sda4 has disappeared!

---

### Post by Arthur Archnix on 2008-03-26
Sounds like you messed up by attempting to change the default options. Perhaps you've heard the Linux cliche? 
> The great thing about Linux is, if you break it, you get to keep both pieces.
Just to reassure you, it's trivial to have five, six, seven different version of Linux running. The trick is the install, making sure you give them their own slice of the pie, and not having them install overtop of any other partition.

Multiple disks adds to the complexity, especially during the bootloader stage. My personal advice is to never install Grub more than once. So, if I install ubuntu first and it installs grub to the mbr, I would never install grub again despite installing Fedora or Debian. Just edit grub manually.

---

### Post by Jookia on 2008-03-26
Windows is greedy, takes the whole pie and ignores linux's pie.

Linux shares the pie with his children equally. They all get along as long as you don't give too little or too much to one of them. Or the child with too little will scream and fight with the one with a bigger piece of pie.

---

### Post by Junglizer on 2008-03-26
Actually Linus didin't write it all himself...

---

### Post by Junglizer on 2008-03-26
> **Jookia said:**
> Windows is greedy, takes the whole pie and ignores linux's pie.

Linux shares the pie with his children equally. They all get along as long as you don't give too little or too much to one of them. Or the child with too little will scream and fight with the one with a bigger piece of pie.

What? Sorry but that seems like a rather poor analogy. And whats OS X? Cake? Maybe a strudel?

---

### Post by Trail on 2008-03-26
> **the-edmeister said:**
> 
```
Booting 'Ubuntu'
rootnoverify (hd **0,4**)
chainloader +1 
``` Yeah, /dev/**sda4** has disappeared!

I might be totally wrong, but if memory serves right, isn't 0,4 referring to sda5?

---

### Post by Whiffle on 2008-03-26
> **Trail said:**
> I might be totally wrong, but if memory serves right, isn't 0,4 referring to sda5?


Yep.

---

