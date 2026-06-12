---
title: "Can I use a 'real' ubuntu install via VirtualBox?"
date: 2010-12-29
forum: Apple Hardware Users
---

### Post by skullmunky on 2010-12-29
I have a nice OSX/Ubuntu dual-boot set up.  But sometimes I'd like to do one quick task in Ubuntu while booted into OSX, or vice versa.  I don't even know if it's possible to run OSX in virtualization, so we'll skip that for now.  so, first:

I can set up an Ubuntu client in an OSX virtualbox host, no problem.  But is it also possible to boot the 'real' install I have on the other partition already within virtualbox?  Or is that just really a bad idea?

---

### Post by Kirboosy on 2010-12-29
> **skullmunky said:**
> I have a nice OSX/Ubuntu dual-boot set up.  But sometimes I'd like to do one quick task in Ubuntu while booted into OSX, or vice versa.  I don't even know if it's possible to run OSX in virtualization, so we'll skip that for now.  so, first:

I can set up an Ubuntu client in an OSX virtualbox host, no problem.  But is it also possible to boot the 'real' install I have on the other partition already within virtualbox?  Or is that just really a bad idea?

I believe you can do that but you might have to make a hard drive image. I would recommend dd for this. 

```
dd if=/dev/[your ubuntu partition] of=./dev/[your mac partition]/[folder]/MyUbuntu.img
```You might have to adjust the code for your computer but it should work easily. The bigger your  partition the longer it will take.

If anyone knows a different way that might be faster please let him know. I am just making a suggestion. 

**BE CAREFUL WITH DD! IT IS JOKINGLY CALLED 'DISK DESTROYER' BECAUSE IT IS VERY EASY TO DESTROY ALL OF YOUR DATA! JUST TAKE YOUR TIME AND DOUBLE CHECK.**

[http://en.wikipedia.org/wiki/Dd_%28Unix%29]("http://en.wikipedia.org/wiki/Dd_%28Unix%29")

---

### Post by skullmunky on 2010-12-29
thanks for the suggestion, that's an interesting thought.  yes, dd is fun ... in the same way that a persnickety flamethrower is ... 

I'm looking for a way to continue to use the partitioned install, though - use it sometimes by booting into it for real, and sometimes through virtualization.

---

### Post by Kirboosy on 2010-12-29
> **skullmunky said:**
> use it sometimes by booting into it for real, and sometimes through virtualization.

Oh ok I thought you were going to remove the physical partition.

Try this then :D

[http://forums.virtualbox.org/viewtopic.php?t=9697](http://forums.virtualbox.org/viewtopic.php?t=9697)

It says for XP but I have a feeling its Windows compatible in general.

---

### Post by AzN1337c0d3r on 2010-12-30
I believe VMWare Fusion and Parallels Desktop have built-in support for running other partitions as virtual disks.

---

