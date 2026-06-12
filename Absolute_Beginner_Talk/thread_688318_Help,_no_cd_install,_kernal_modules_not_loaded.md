---
title: "Help, no cd install, kernal modules not loaded?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Hokum15 on 2008-02-05
I've followed the instructions here, [http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093) but when i get past the ISO part it says that my kernal modules are not loaded and the install will fail (which it does) i tried NO then it doesnt see my network card (pcmcia addon so fair enough) then it seems to bomb at the hard drive detection screen?  This is when trying to install Xubuntu 7.10 and 7.04.

Help?

---

### Post by rkd on 2008-02-05
Which step number are you at when you run into that problem?

---

### Post by Hokum15 on 2008-02-05
Hi if you mean on the walk though i guess step 11, IE i have the ISO, but it says that the modules are not loaded.
Something like the version of linux used to install is not the same as the version being installed?

I'm rather new to linux...

---

### Post by Hokum15 on 2008-02-05
The Error verbatim
[B]!! load installer components from an installer ISO

No kernal modules were found. This probably is due to a mismatch between the kernel used by this version of the installer and the kernel version available in the archive.

If youre installing from a mirror, you can work around this problem by choosing to install a different version of ubuntu. The install will probably fail to work if you coninue without kernal modules.
Continue the install without loading kernal modules?

<go back>                                          Yes                NO[/B]


This is the message i have...

---

### Post by Hokum15 on 2008-02-06
Anyone?

---

### Post by Hokum15 on 2008-02-06
No one able to help?

---

### Post by rkd on 2008-02-07
I don't know anything about this method of installing, so I probably won't be of much help.

I notice that in the HOWTO, it says to be careful to get the vmlinuz and initrd.gz that match the version of the .iso that you are trying to install. Are you confident that you did use the vmlinuz and initrd.gz that match your .iso?

The HOWTO also warns to rename other .iso files so the installer won't find them instead of the one you intended it to use. Do you have any other .iso files anywhere on the computer? I get the impression that the installer will look everywhere for an .iso, but I'm not certain of how it works.

And did you get the .iso for the alternate CD, not the Live CD?

I don't know why you are trying to use this rather complicated method. If I were you, I think I would put my energy into getting a working CD reader connected to the computer instead of into getting this HOWTO to work, but maybe there is good reason not to do that. I'll try to help you with this HOWTO if that really is the way you want to go, but if you would like to get a CD drive working, I'll try to help with that, as well.

---

