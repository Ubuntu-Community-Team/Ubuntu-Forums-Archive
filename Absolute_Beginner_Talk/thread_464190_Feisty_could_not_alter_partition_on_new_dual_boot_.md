---
title: "Feisty could not alter partition on new dual boot install"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by the_nite_owl on 2007-06-04
Hi All,
I have been trying to setup a dual boot with XP.  
I did a clean install of XP Pro on the system first, one HD with a single partition.
I then booted up the x386 boot CD for Ubuntu 7.01, clicked install on the desktop and ran through the steps.  
Once I reached the section for partitioning the drive I selected a guided setup to repartition the drive.
When it tries to actually repartition it fails saying something to the tune of it could not complete the action.
Attempting to partition manually gave me the same problem.

I have done this before on other computers without much trouble so I wondered if it might be a motherboard or HD related issue others might be familiar with.  
Are there known circumstances under which Ubuntu would not be able to alter the partition info on the drive?  XP installed fine.  The drive was setup as master with a CDROM drive as slave.
I could try swapping the CDROM over to the secondary controller and set the HD as a standalone, that is just the configuration it was in when I went to work on it and did not have a second IDE cable in the box at the time.

Any common issues I can look for?  I do not have a lot of Linux experience but this seemed a pretty basic setup that should have worked.

Thanks.

---

### Post by hitokiri0kenshin on 2007-06-04
I had a similar problem with Sabayan linux. Try unmounting all drives. 
```
sudo umount -a
```
Once unmounted try running the partitioner again.
Hope this helps :p

---

### Post by the_nite_owl on 2007-06-04
> **hitokiri0kenshin said:**
> I had a similar problem with Sabayan linux. Try unmounting all drives. 
```
sudo umount -a
```
Once unmounted try running the partitioner again.
Hope this helps :p

Thanks, I will give it a try.
I first have to fix my video problems.   Trying to get my ATI card working with the instructions in one of the forum sticky's screwed something up and now I cannot get into the GUI.  I assume there is problems in the xorg.conf file but not sure what.  I am about ready to just cleanly reinstall everything fresh.

---

### Post by esavato on 2007-06-04
Previously, I have had the same problem and I just downloaded the alternate install cd, which has a non graphical version of the partitioner.

---

