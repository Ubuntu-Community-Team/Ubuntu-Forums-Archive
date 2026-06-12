---
title: "&quot;Disks&quot; missing in 6.10"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by chochem on 2007-03-13
Actually it's two questions:

1) Swap file management: I have a suspicion (filed in [another thread]("http://ubuntuforums.org/showthread.php?t=383056") which hasn't succeeded in attracting much attention) that my 1Gb swap drive is not being utilised by Ubuntu. However, I can't seem to find any way of checking swap file settings in Ubuntu preferences or management. Can anybody tell me how to check up on this?

2) As an answer to my own question I went looking for a program simply termed "Disks" which I used in 6.06 (I have recently upgraded to 6.10) However, this is no longer available (or if so, not in the place and/or shape it used to) Can anybody tell me where to find it or a suitable alternative? Searching the package manager for "disks" isn't very effective....

---

### Post by El_Matthews on 2007-03-13
> **chochem said:**
> Actually it's two questions:

1) Swap file management: I have a suspicion (filed in [another thread]("http://ubuntuforums.org/showthread.php?t=383056") which hasn't succeeded in attracting much attention) that my 1Gb swap drive is not being utilised by Ubuntu. However, I can't seem to find any way of checking swap file settings in Ubuntu preferences or management. Can anybody tell me how to check up on this?
open a terminal a use the command top, here you can see how much memory/swap is used. You have the system monitor in administration also that could help you out.

> 
2) As an answer to my own question I went looking for a program simply termed "Disks" which I used in 6.06 (I have recently upgraded to 6.10) However, this is no longer available (or if so, not in the place and/or shape it used to) Can anybody tell me where to find it or a suitable alternative? Searching the package manager for "disks" isn't very effective....
what do you whant to do with your disk. to format it you could install gparted

---

### Post by chochem on 2007-03-14
> **El_Matthews said:**
> what do you whant to do with your disk. to format it you could install gparted

It provided a GUI for seeing what was mounted and where and changing those settings.

---

### Post by El_Matthews on 2007-03-15
The only app I found doing this is pysdm. Have a look at it but be careful because this could make your system un-bootable. 
You can always type in a command prompt
```
mount
```and this will show you everything mounted on your pc. edit your fstab as root
```
gedit /etc/fstab
```
after saving your modifs 
```
mount -a
```to mount everything

---

### Post by chochem on 2007-03-16
Ok, I'll try that. Thanks, El_Matthews.

---

### Post by anaconda on 2007-03-16
1.  open a terminal and type "free" and it will show you how much swap you have. If "free" shows that you have swap, but it isn't used much, that isn't a problem.. usually swap is used only if you run out of RAM.  If free gives total swap as 0 then you dont have any swap..

---

