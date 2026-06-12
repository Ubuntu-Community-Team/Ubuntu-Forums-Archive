---
title: "Filesystems"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by jonathanc88 on 2005-10-17
Recently, I have installed Kubuntu 5.10 (Breezy Badger). Everything works fine, except that I made a mistake during installation. Now, the installation program has deleted the entire system, and I can only start-up Kubuntu. I tried to install Mac OS X Panther again (my operating system), but it did not work. I guess it has to do with the file system, since Mac OS X 10.3 uses HFS+ and not the Linux format. Can somebody help how I can "lay down the filesystem" (I heard reformat is not the correct terminology) the hard drive? If it is possible, I want it to have 2 partitions, one for Linux and one for Mac OS X. I heard you can use fdisk, but I am a little scared of the terminal... Could somebody explain me how to do change the filesystem?

---

### Post by DJ_Max on 2005-10-17
The way I'm familar with requires you to start over and reformat your HD.

Install Panther first, 
Create two (2) partitions. One for your HFS+ partition. Leave one *free space*.
Boot Ubuntu, have Ubuntu use the exsisting *free space*.

It will then install Ubuntu along side OS X.

---

### Post by jonathanc88 on 2005-10-18
Thanks for your reply. Although it is a little bit more complicated, at another (the Kubuntu forum) I discovered you need to select the 'Disk Utility' when starting from your Mac OS X CD. To do this simply click on the installer menu and select 'Disk Utility'. Then you are able to format your drive.

---

### Post by DJ_Max on 2005-10-18
[QUOTE=jonathanc88]Thanks for your reply. Although it is a little bit more complicated, at another (the Kubuntu forum) I discovered you need to select the 'Disk Utility' when starting from your Mac OS X CD. To do this simply click on the installer menu and select 'Disk Utility'. Then you are able to format your drive.[/QUOTE]
Yes, that's the partitioning tool in OS X.

---

