---
title: "[SOLVED] Format before upgrading gutsy?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by naggis on 2008-04-17
I have been using Gutsy for first time during the last couple of weeks. I guess that the messing about that I have got into will have not had a good effect on the installation of Gutsy. As Hardy will be out in the next couple of weeks, I would like to upgrade. In Windows I would certainly format the drive before reinstalling. Should I do  the same in Ubuntu? Will an upgrade automatically format the drive or do I need to do this some other way.
Sorry about what must be a simple situation - but if you don't know, its a problem!
Thanks for any help

---

### Post by victorgreen on 2008-04-17
If you have gutsy installed and are planning to upgrade through update manager to hardy, it *should* work just fine. Turn on comp, open upgrade manager, tell it you want it to upgrade to next release, and leave it sitting and installing stuff for a couple hours. restart and you should have hardy. Of course this upgrade process does not work equally well for all users. 

For myself personaly, I'll move my large data folders (music etc) to an external, reparition my drive to have a one partition mounted as / and the second one mounted as /home. Here [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) are some instructions on how to make home its own partition. 

I will then wipe the / partition and install a clean copy of hardy on it. Who knows, maybe Ill try the 64 bit version.

---

### Post by naggis on 2008-04-17
thanks victorgreen
I have a separate partition for my files - originally set up to use with windows but now ok for gutsy.  I am still not clear whether formating the drive where gutsy is installed is a good thing at the time of upgrading. I don't know how messed up the installation becomes as you use (and in my case abuse) it. Have you any thoughts on that?

---

### Post by Xbehave on 2008-04-17
im not 100% on this but as long as you've not made any changes to files manually you should be fine, i personally have a separate /home and install to a blank partition on upgrades so that im left with my old install if anything goes wrong, but simply upgrading should work fine too.

---

### Post by naggis on 2008-04-17
maybe I will try setting up a new partition too. At least there will be no problems with formating in that case
Thanks again

---

### Post by aikiwolfie on 2008-04-17
> **victorgreen said:**
> If you have gutsy installed and are planning to upgrade through update manager to hardy, it *should* work just fine. Turn on comp, open upgrade manager, tell it you want it to upgrade to next release, and leave it sitting and installing stuff for a couple hours. restart and you should have hardy. Of course this upgrade process does not work equally well for all users. 

For myself personaly, I'll move my large data folders (music etc) to an external, reparition my drive to have a one partition mounted as / and the second one mounted as /home. Here [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) are some instructions on how to make home its own partition. 

I will then wipe the / partition and install a clean copy of hardy on it. Who knows, maybe Ill try the 64 bit version.
A couple of hours? You must have a seriously slow connection. It took me about 30 minutes to upgrade the last time around. No hard drive reformat required.

---

### Post by zvacet on 2008-04-17
@ **naggis**

If you have separate home partition you don´t have to reformat anything.Maybe you want to try upgrade with alternate CD.

---

### Post by Zralou on 2008-04-17
You could just use gparted to delete the partition, then do an install and point it to the unallocated space, the install will do the rest.

Sara Lou

---

### Post by guj4_n3b3sk4 on 2008-04-17
So, upgrading from 7.10 to 8.04 won't harm any other partitions I have on hard disk? I have divided hard disk on 2 partitions - on linux partition I have 1024MB swap space and about 30G ext3 mounted as /. The rest of the disk is Mac OS X partition. After I upgrade 7.10 to 8.04, will my OS X partition remain untouched?

Thank You for answer.

---

### Post by zvacet on 2008-04-18
>  After I upgrade 7.10 to 8.04, will my OS X partition remain untouched?

Yes!

---

