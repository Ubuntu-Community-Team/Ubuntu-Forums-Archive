---
title: "Partitioning Drive"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by gharsh on 2007-03-13
Hello,

A very noob here.  I have been working with ubuntu for about a week now and had it installed on my laptop for a day.  I decided that I wanted to have access to windows also so I reinstalled windows.  Now, I want to be able to dual boot and am not sure how to partition my drive to do this.  I lost most of my stuff when I loaded ubuntu the last time so there is not much to lose this time,  but would like to be able to not overwrite windows if at all possible.  I am not sure how to use the gparted program that comes with the livecd.  Is there a step by step walk through somewhere that can walk me through each step in order to have a dual boot?  I have searched and found many articles but nothing that seems to be simple enough for me to follow.  I saw a site with pictures of the various screens using the program, but again, I'm not sure which partition would be used for windows and which would be used for ubuntu.

Any help would be appreciated.

---

### Post by Kobalt on 2007-03-13
I would recommend you to read and follow the very good aysiu's guide on how to install Ubuntu : [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
It's very detailed, it has screenshots for every step and clear explanations.

---

### Post by dstew on 2007-03-13
If you have Windows installed, that is the first step. You need to create room on your disk to put in the linux file system. You may already have the space set aside, left over from your previous intall. Maybe the linux file system is still there, untouched, and all you need to do is set up the boot loader to dual boot.

In order to answer these questions, we need to see what partitions are on your disk. There are two programs on the live CD that will let us see your partitions. Both are partition editors, but for now we just need to see what partitions are there.

The first program is gparted, which you hae seen before. Just open it, and post to this forum the list of partitions as it shows them. The other way to list your partitions using fdisk, will give a text output (easier to post). To list the partitions with fdisk, boot the live CD, open the Terminal (in the applications menu) and type

fdisk -l

Then copy the partition list and post it to this forum.

---

### Post by gharsh on 2007-03-13
Kobalt:  Thanks for the link.  If I read it correctly, I should choose the first option in gparted and it will take care of partitioning the drives for me?  I think that is what I want.  

dstew:  Thanks for your reply.  I will try that option if I don't feel comfortable with the first option.

Thanks.

---

### Post by Kobalt on 2007-03-13
You should chose the first option if you remain with a single hard drive. It will ask you how much space you want to allow to Ubuntu then partition your drive correctly (remember to defragment your disk and make backups before attempting anything).
If you have a second hard drive you want to dedicate to Ubuntu entirely, then chose the second (or third) option that labels 'Erase entire disk <label of the hard drive for Ubuntu>.

---

### Post by gharsh on 2007-03-14
Thanks for the assistance.  I loaded ubuntu and it seems to be working fine.  It asks me which system I want to boot on the startup, which is what I was looking for.  Thanks again.

---

