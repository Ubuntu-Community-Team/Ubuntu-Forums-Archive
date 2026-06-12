---
title: "How to create a partition so I can run both Windows and Ubuntu"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by jbellefeuille.com on 2007-12-16
Hello,

I would like to know how to run Ubuntu as a partition with Windows still on my computer.

I want to start learning more about this and would like to know all tips or tricks..

---

### Post by dummyhead3 on 2007-12-16
Greetings!
You must do the following:
Remove some space (min. 2 GB) from your Windows partition. It's file system should be ntfs. With that, you need to make a partition where the file system is ext3. also you need a small partition (twice your RAM for a maximum of 1.5 GB  is pretty good).

---

### Post by thedrizz on 2007-12-16
heya,

When i dual booted, i ran perfectdisk (a defragmentation program) like 6 times in order to make a continuous space of 60 gigs at the end of my hard drive

Than i booted ubuntu off the live disk, went to the install icon, and used the top option(i think it says install on a new partition or something). You can drag the slider until you find the size you want for linux (i did 20 gigs)

than go through and install. Should work like a charm.

There are better guides out there, however. Google if you wanna see them i guess

---

### Post by thelatinist on 2007-12-16
Unless you're using Vista, the Ubuntu Live CD should be able to take care of all that for you.  Just make sure you defragment your windows drive several times and make sure there's nothing at the end of it before you try to install.

---

### Post by nar321 on 2007-12-16
Unless i misunderstand what is meant by partition. You can easially run both Ubuntu and Windows. With windows already installed just do a install of Ubuntu. It finds the Windows install, has GRUB create the ability to boot into either Windows or Ubuntu and you can then run either Windows or Ubuntu depending on which you booted into . It will help if you defrag Windows before doing the Ubuntu install and Windows may want to check the disk after you booted into it for the first ttime after the install. Let Windows do the check, it's just being cranky.

---

