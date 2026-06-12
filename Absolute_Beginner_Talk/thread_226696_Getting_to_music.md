---
title: "Getting to music"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by joethesupercow on 2006-07-31
Hi everyone! I've just started using Ubuntu but I've been very pleased with the expirience. I'm currently running a dual-boot system (Breezy Badger and Windows XP Home) and i was wondering if there's anyway to access the music in my windows partition from linux. In other words is the only way to get all of my music onto linux to burn a ton of disks and then rip it all?

---

### Post by carlosqueso on 2006-07-31
It's actually not too hard to do that.  First you need to find out the name of your windows partition.  you can do that by opening a terminal and typing sudo fdisk -l and looking for which partition says NTFS.  Then create a mountpoint for it by typing ```
sudo mkdir /media/windows
``` open up your fstab file by typing ```
sudo gedit /etc/fstab
``` and adding the following line to the bottom ```
<partition name>   /media/windows  ntfs  umask=0222 0 0
``` Finally type ```
sudo mount -a
``` into a terminal and it should work.  Let me know if you run into any problems.

---

### Post by x64Jimbo on 2006-07-31
You can mount your windows partitions pretty easily in Ubuntu. Getting your mp3s to play is a slightly different issue though. You have to get the codecs installed. 
Check out this page for that info, and a lot more:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

