---
title: "Virtualbox harddrive help"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by ssc351 on 2007-04-10
Yo,

So I installed Virtualbox on my machine and its awesome...I made the Virtual OS 15gb with winxp sp2.  However, after installing acrobat pro and going through all the updates  virtualbox said that I was out of space and ubuntu also slowed down tremendously and said i needed to free up resources.  

Where does the Virtual OS actuall install (ie what partition?)  I only have about 15gb dedicated for ubuntu, but I have another 60gb free in a fat32 partition.  

Did I do something wrong on the original mount of the  virtual os?  Do I (can I) need to merge more space from the fat32 partition to my linux partition? 

I am running fiesty 2.6.20-14-generic

---

### Post by xpod on 2007-04-10
You dont install your virtual XP to any actual partitions you create a VDI(virtual disk image) when you set up your VM which is stored in " home>.virtualbox>VDI".:) 

If you`ve allocated 15g of virtual diskspace to your XP vm when you only have an actual 15g partition allocated to ubuntu in the first place then thats why you dont have no space left.

You should have just made the XP vdi 5g or something.:)

---

### Post by ssc351 on 2007-04-10
If I only make it 5gb, won't i run out of space fairly quickly once i start installing apps?

Should I give linux more space?

---

### Post by steve.horsley on 2007-04-10
Yes. If you're going to be keeping large disk images on Linux, it will need a large disk of its own. Once you start playing with VMs, it's scary how fast your disk space gets eaten up!

---

### Post by ssc351 on 2007-04-10
So I currently have a swap, home, and main (not sure the name) partition for linux...and then a 30gb windows xp partition and a 60gb fat32. For the linux partitions what sizes do you recommend?

---

### Post by bodhi.zazen on 2007-04-10
Unless you have a lot of HD space ....

1. Run Live from .iso as much as possible.

2. Look for light weight virtual machines. Fluxbuntu, DSL, puppy, AUSTRUMI, etc. Not only will this save on HD space, but also improve performance.

3. If you must "HD install" use 4 Gb "test" partitions.

4. IMO 10 Gb should be plenty of space for most distors + extra software, excessive even, maybe 7 Gb ...

5. Configure a nfs share for data ...

See these links :  

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

The gwos link is down, but you will find I added some how-to's to enable USB devices and network shares with Virtual Box there.

---

