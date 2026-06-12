---
title: "dual boot issue"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by kcbear on 2007-05-04
VERY new to linux.setting up dual boot. xp pro on slave and ubuntu on master using ubuntu 6.0.6
have altered menu.lst with the following

title windows xp
root (hd1.0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

when starting up it comes up with the menu listing os's. when i selected windows it came up with

booting windows xp
root (hd1,0)
filesystem type unknown partition type 0x7
makeactive
map (hd0) ( hd1)
error 11 unrecognised device string

appreciate any help

---

### Post by louieb on 2007-05-04
I have the same setup on one machine here is my xp entry
```

title Win XP Home
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1
      boot


```
[Nuts on Grub]("http://louboldt.com/ilinuxgrub.htm")

---

### Post by jerrylamos on 2007-05-04
Well, Microsoft expects Windows to be on the first partition on the first hard drive.  Period.  Ubuntu can be somewhere else, but expects to run from the same place it was installed on.

I don't change any of the menu.lst lines but I do move the groups of lines around so the default image is first.  It's O.K. to add some explanation on the title lines.

This is a quad boot system I'm posting from, Windows followed by Ubuntu 6.06.1 Dapper on the 1st hard drive, 2nd hard drive first Ubuntu is partly migrated to Ubuntu Gutsy 7.10 and then Ubuntu Feisty 7.04.  I can select any of the images at boot time; the default is the Feisty.  This post is from the Gutsy.

And by the way the menu.lst that is active is in the last Ubuntu to be installed.

Cheers, Jerry

---

### Post by louieb on 2007-05-05
> **jerrylamos said:**
> Well, Microsoft expects Windows to be on the first partition on the first hard drive.  Period.  
Not quite true.  I found XP run quite happily from any primary partition.  Even some  OEM installs put a recovery system on 1st partition. The map commands are to fake out XP to make it think its on the 1st drive.
> **jerrylamos said:**
> 
Ubuntu can be somewhere else, but expects to run from the same place it was installed on.
True. 
> **jerrylamos said:**
>  This is a quad boot system ....This post is from the Gutsy.
Quad boot here too XP, Dapper,Feisty,PCLinuxOS. All on a single drive. Going to get rid of Feisty and PCLinuxOS. How does Gutsy look?

---

