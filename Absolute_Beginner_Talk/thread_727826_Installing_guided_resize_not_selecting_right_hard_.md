---
title: "Installing: guided resize not selecting right hard drive"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by eightphases on 2008-03-18
Hi, I'm completely new to this, and don't really understand much about partitioning and stuff. I've look around for answers, but if I missed something obvious, don't get too mad >_<

I'm trying to install Ubuntu 7.10. I have three hard drives, but I want to install Ubuntu on the hard drive with my Windows XP installation and dual boot.

While trying to install Ubuntu, when I get to the partitioning section, there's the options:
guided: resize
guided: use entire disk
manual

I want to use the resize section to do this (since I have no idea how to do it manually), but it doesn't bring up the resize option for the hdd I want to install on. It wants to resize one of my other hdds, with no option to choose a different one to resize. Is there any way you can change it so it will let me resize the hard drive of my choice? Or will I have to do it elsewhere?

Thank you

---

### Post by bumanie on 2008-03-18
What can do is to download a gparted live cd and shrink your xp with that. Leave the freed up area as 'unallocated' space. After that you should be be able to choose manual at the partitioning stage of your next ubuntu install and install ubuntu onto the unallocated portion of the hard drive. Assuming your xp is on the first hard drive, the partitioner will label it as hda1 or sda1. Gparted is a graphical based and easy to use with sliders etc. Get gparted here [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Before you shrink xp; back up just in case something goes wrong. You should also defrag windows first.

---

### Post by eightphases on 2008-03-18
We tried using partition magic in winxp to split the hd in two and then install ubuntu on the unused partition. We had to manually make the partitions for ubuntu in the install. When doing this winxp would boot (which of course doesn't support dualboot). 

The help file for th installer said ubuntu would automatically boot and use grub to let you pick between which os to load. I figured it had something to do with the installer. I'm a bit stuck here :(

---

### Post by hyper_ch on 2008-03-18
and before you resize the windows partition defragment it 2-3 times

---

