---
title: "A small help needed on partition not showing"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-04-21
I installed Feisty, the Gparted is now a bit different, and I marked about 8 GB for
ext3 format as  /documents.
This partition does not show up on desktop.

---

### Post by steve.horsley on 2007-04-21
First, does the directory /documents exist? If not., create it with the command:
sudo mkdir /documents

Secondly, is the partition actually mounted? The command 
**df -h **
will tell you. If it's not listed there, pleas post the output of these two commands:
[B]sudo fdisk -l
cat /etc/fstab[/B]
and we'll try and sort it out.

Thirdly, if it is mounted and you are just missing the desktop icon, then this si probably the easiest thing to do: Open a nautilus file explorer, go up  to the top folder and then drag /documents to your desktop using the middle mouse button (scroll wheel - if you don't have a scroll wheel, drag it with both the left and right buttons held down). You get a menu asking whether to move, copy or link - choose to link here.

---

### Post by dptxp on 2007-04-21
It shows in fdisk -l , it shows in etc/fstab, it shows in File Systems as a directory with the space given to it.
It exists, and I think like /home it has got absorbed in the File Systems.

Is there a way I can have this directory on desktop ?

You have given some option, I am checking meanwhile.

Thanks.

---

### Post by dptxp on 2007-04-21
It is a laptop, felt lazy to get amouse, pressed both buttons and dragged to desktop.
Selected Link and the job is done. Thanks

I have allotted 8192 MB (8 GB) to root. Only 5.1 GB left after installation. They say that
2 GB is needed for installation. 2.9 GB of mine has been consumed, why ?

Is 8 GB adequate since I shall be loading compilers, not many though. I shall not be saving
data in this partition. I have just installed yesterday, I can reinstall, later it may become
difficult though next 2 GB is for swap which can be moved if needed and this partition can be
resized.

I am yet to come in terms with Linux file management, got to study a bit.

---

### Post by steve.horsley on 2007-04-22
That's odd. My installation only occupies 2G so far (plus another 6.4G for UT and UT2004). I guess you have installed some other stuff besides the default install. I don't think 2G is really enough, and they should say 3G minimum. But 8G will easily be enough, however many compilers you install.

---

### Post by dptxp on 2007-04-22
It is funny that when check in Ubuntu, it says 5.1 GB free out of 8 GB (I click on a folder in File Systems to see properties) , but when I put the Kubuntu CD and started partitioning (plan to use both), it says that about 2 GB is being used.

---

