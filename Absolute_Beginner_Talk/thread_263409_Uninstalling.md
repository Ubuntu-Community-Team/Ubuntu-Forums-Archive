---
title: "Uninstalling"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by Phinks on 2006-09-23
How do I uninstall/format the ubuntu installation? I have 2 harrives, one with WinXP and one with ubuntu. And I can't boot WinXP. I can't even boot any other live disks like the WinXP install disk etc. I would have thought simply changing the HDD boot order would let me choose which OS to boot with-but appearently not.

I can't find any information on uninstalling ubuntu on thw wiki page, or the online help documentation.

---

### Post by Phinks on 2006-09-23
*bump*

---

### Post by someonedumb on 2006-09-23
Uninstalling ubuntu won't fix your problem... You need to have the boot sector on the primary/active partition set up properly.

Does the WinXP disk boot if you disconnect the ubuntu drive?

---

### Post by nts on 2006-09-23
theres no uninstalling as such, you just need to format and install Win XP.

Just boot off the XP disc and follow the steps.

---

### Post by someonedumb on 2006-09-23
Actually, re-reading the symptom about not being able to use winXP CD's leads me to believe the problem could very well be in your BIOS setup.

---

### Post by chrisfay on 2006-09-23
> Actually, re-reading the symptom about not being able to use winXP CD's leads me to believe the problem could very well be in your BIOS setup.

I agree....

---

### Post by bulldog on 2006-09-23
I'm not sure what 'harrives' mean.

If you have two hdd's you have to set the one with grub  as your boot device.

Otherwise grub will not load.

---

### Post by chrisfay on 2006-09-23
> I'm not sure what 'harrives' mean.

Unless you're being facetious, I believe he did mean 'hard drives'.:p

---

### Post by Phinks on 2006-09-23
> **bulldog said:**
> I'm not sure what 'harrives' mean.

If you have two hdd's you have to set the one with grub  as your boot device.

Otherwise grub will not load.

Yes, but if I boot with grub, I can only boot ubuntu.

And yes I meant harddrives. I think the term is 'Anally retentive'

I'm going to try and remove the ubuntu installed hard drive and then boot w/o it. I think I've had enough of ubuntu for one day. Too much like get blood from a stone for my liking.

---

### Post by bulldog on 2006-09-23
> **chrisfay said:**
> Unless you're being facetious, I believe he did mean 'hard drives'.:p

Nope never heard of it for sure,but I'm Dutch.

@TS

When you have the hdd with GRUB set as your boot device you should see a menu with your options,[maybe you have to use ESC to see it]

If GRUB is setup on the hdd with your XP install and Ubuntu is setup on the second hdd it should be allright.

If not and XP is on the second hdd [not the boot device] you have to map your hdd's because windows would like to be the first OS to boot.

If so let me know.

---

### Post by Phinks on 2006-09-23
hmmm interesting. I my second HDD has ubuntu on it and grub was installed on there aswell. My first has winXP on. So i need to map my hdds? I can boot into ubuntu fine. What do I need to do under ubuntu to allow grub to 'see' my WinXP installation on the other HDD?

---

### Post by bulldog on 2006-09-23
If XP is your boot device and Ubuntu and GRUB is on the second hdd[how did you manage that?alternate cd?] then should be booting in XP be no problem,just put the XP disk as boot device and it should run.
Grub hasn't altered it.

If you just have no entry in your grub for XP you can set it there yourself.

gksudo gedit /boot/grub/menu.lst

and put at the end the following lines,

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
(hd0,0) 
rootnoverify (hd0,0)
savedefault
makeactive
chainloader	+1

---

