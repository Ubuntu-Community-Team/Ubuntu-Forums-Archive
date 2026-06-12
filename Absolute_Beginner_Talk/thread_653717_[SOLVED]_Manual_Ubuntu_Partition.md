---
title: "[SOLVED] Manual Ubuntu Partition"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by skaldicpoet9 on 2007-12-30
I am new to using Ubuntu/Linux and have a question about manual partitioning. I am trying to install Ubuntu on my girlfriend's laptop but unfortunately she doesn't have enough space available for the automatic partition. Right now the laptop has about 21gb of free space available. I am wanting to install Ubuntu on a 5gb partition. However, when I get to the partition screen on install I am not quite sure what to do. It says I need at least 2gb of space for install and a 256mb swap partition? I don't know what to do here and would appreciate if anyone could help me out. My girlfriend will kill me if I screw up XP so I think I will probably need someone to help me with backing up my XP files as well.

---

### Post by LaRoza on 2007-12-30
First, don't alter the partitions without having backups.

Then, tell us the specs of this computer so we can tell if Ubuntu will run on it well enough to make installling worth it.

---

### Post by skaldicpoet9 on 2007-12-30
Gateway 
MX6429
AMD Turion(tm) 64 Mobile
Technology ML-32
1.79ghz 1.43 GB Ram

And yes, I was not about to install without backups. But I need some help backing up my the files since I have never done it before.

---

### Post by LaRoza on 2007-12-30
Can you make recovery disks?

Even if the computer didn't come with them, the option to make them is usually there.

---

### Post by meindian523 on 2007-12-30
No problemo,

1]Backup her XP files.
2]Boot into Ubuntu CD and at the partitioning step,select Manual partitioning.
3]Create an extended partition of the 21 GB and within that,you can create new partitions using partitions>>new
4]Create 1st partition within the extended partition of about 8GB and format it as file system:ext3 and mount point "/"
5]Create 2nd partition of size=(2*RAM,subject to maximum of 700 MB) within the extended and format it as filesystem:linux-swap and mount point would be greyed out.
6] Create a 3rd partition within the extended and allow it to use whatever part of the 21 GB is left,format as filesystem:ext3 and mount point as "/home"

Click apply and the rest of the installation process is easy.

edit:Saw system specs,you don't need a swap partition,though you might make a 512MB space for it at your option

---

### Post by rahimveron on 2007-12-30
When on the partition page, Choose Manual Partition: From your free space
1.Create a 5 GB ext3 partition and Choose Mount Point on /.  The "/" (forward slash) is Root Parition where Ubuntu filesystem will be installed. I would recommend 10 GB / (root partition).
2.Create a 512 MB Swap partition and choose Swap in the mount point option.
The setup will install Grub and you will be able to DUAL-BOOT with XP & Brown Freind.

---

### Post by skaldicpoet9 on 2007-12-30
Ok, I am going to go try and see how it works.

brb..

---

### Post by meindian523 on 2007-12-30
What about backing up?!

---

### Post by skaldicpoet9 on 2007-12-30
lol I am doing that right now

---

### Post by rahimveron on 2007-12-30
> **skaldicpoet9 said:**
> Ok, I am going to go try and see how it works.

brb..

Believe me its simple. Good Luck.

---

### Post by skaldicpoet9 on 2007-12-30
Should I defragment my drive before I backup my Windows files and install Ubuntu?

---

### Post by LaRoza on 2007-12-30
> **skaldicpoet9 said:**
> Should I defragment my drive before I backup my Windows files and install Ubuntu?

It helps. It makes it safer and faster for resizing the partition.

---

### Post by ajgreeny on 2007-12-30
Make sure you defrag the windows partition, probably twice in succession, before installing ubuntu, and make sure there is enough space left for windows to work if it is still needed.  You should leave a minimum of about half the size of the already used space in the windows partition, and then use the rest for ubuntu.

EG. If your whole disk is 40GB and windows at present uses 12GB, allow at least 6GB extra for that, ie a total of 18GB.  The remaining 22GB (actually less because of the way sizes are shown or calculated by OSs) can be used ubuntu with either the default partition setup which happens automatically at install, or using a separate /home partition if you want to do it that way.

Good luck and welcome.

---

### Post by skaldicpoet9 on 2007-12-30
Ok will do then.

Looks like it will be a little while before I am back here lol.

Btw...When I went to the Backup Wizard it said that after it was done backing up the files I would need to insert a floppy disk to use for recovery later. Can I just use a regular blank DVD? I ask because this laptop doesn't have a floppy disk drive.

---

### Post by skaldicpoet9 on 2007-12-30
Hmm, Windows is using 56% of the disk right now. So if I need 50% does that mean I am screwed? I have a 49gb hd and 28gb of that is being used for Windows. Leaving me with 21gb of freespace left.

*edit* oops did you mean half of what Windows is using? So that would be 14gb?

I am a little bit lost here...

---

### Post by rahimveron on 2007-12-30
^ Yes Windows System files and not your My Documents stuff. Just leave 6 GB for WIndows to work, it will be fine.

---

### Post by ajgreeny on 2007-12-30
Yes, should be fine.  The problem with windows and lack of space is really only when you want to do any more defragging, when free space is required to allow files to be moved etc etc.  My guess is that once you are used to ubuntu you will hardly ever use windows and therefore the need to defrag will be reduced to almost never.

---

### Post by skaldicpoet9 on 2007-12-30
Well actually I will probably not use Windows for everyday computing but I play a lot of games on Windows so I don't think I will be abandoning it all together due to the fact that game support for Linux is still severly lacking.

---

### Post by skaldicpoet9 on 2007-12-30
Ok, so I got Ubuntu installed only I have one problem. The driver for my wireless card is a restricted driver and I can't seem to enable it through the restricted drivers wizard. This is the message that I am getting: "The software source for the package bcm43xx-fwcutter is not enabled." Anyways, I would really like to be able to connect Ubuntu to my wireless (right now I am plugged into the wall).

---

### Post by meindian523 on 2007-12-30
Ok,open System>>Administration>>Software Sources.

Enable the universe and multiverse repositories and then allow the index files to reload.Then try installing the restricted driver again.

---

### Post by meindian523 on 2007-12-31
Ok,please mark the thread solved,looking as to you have started separate threads for your wireless problems and for "the mistake of the partitions",which would have not occurred if you had just done the partitioning manually.

---

### Post by skaldicpoet9 on 2007-12-31
?

The reason I didn't do the manual part was because it turned out that I could use the guided part and being a newbie I prefered installing Ubuntu that way.

I made a seperate thread because this is a seperate problem. I don't see what that has anything to do with the dilema at hand though...

---

### Post by meindian523 on 2007-12-31
Well,I'm not poking mistakes that you should have not made a thread,etc,just saying that Ubuntu has been only my second installation of Linux(Mandriva 2007 was the first) and both times I used Manual since I know what's happening to my HDD and don't lose any stuff.Just my choice,you might have your own logic for selecting guided,and that's what Linux is about,about having a choice.

---

