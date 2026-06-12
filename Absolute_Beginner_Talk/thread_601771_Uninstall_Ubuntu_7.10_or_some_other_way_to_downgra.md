---
title: "Uninstall Ubuntu 7.10 or some other way to downgrade"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Kurenai0h on 2007-11-03
I've found out that Ubuntu 7.10 got to much of things that dont work that I want to downgrade to Feisty Fawn, its just HOW? I though of just removing the ubuntu and then just install the other version, but the problem is, I dont know where ubuntu is. You see I get 3 partitions, HP Recovery that got 7.59 GB, OS (C:) That got 141GB and Data (D:) that got 85.1GB 
So, when I installed Ubuntu I told it to install on the biggest partition that I expected to be DATA cos it had the most space and it was not where Vista was. Cos DATA was all empty but on OS where all the Vista stuff was had used 89.7GB of it 141GB. But when I click on the DATA on my computer when I run vista its nothing there and it even with Ubuntu installed, it says that it is all empty (85.0GB free of 85.1GB actually) and I see no sign of Ubuntu anywhere else! What to do?
If there is anyother methods that a complete newbie could understand please scream out.

---

### Post by defrex on 2007-11-03
I'm not sure I quite followed all that about your partitions. But installing feisty on the partition you have gutsy on will overwrite it.

As to finding out which partition it's on. When you boot the live CD, open up gparted (administration>gnome partition editor) and look for the partition formatted as ext3 (rather then NTFS or fat32). That'll be Ubuntu.

---

### Post by rickycodie on 2007-11-03
the easiest way to find out where ubuntu is installed is to use gparted on the live cd. look for the ext 3 that's ubuntu
EDIT:
shoot beaten to it.

---

### Post by Kurenai0h on 2007-11-04
I downloaded Feisty Fawn and got it on cd and tried to install but I just got a error like thing with alot of X I think or something arround with a message about something working with X.... I believe I saw something of the same stuff earlier on this forum. And to uninstall ubuntu I need the Vista install cd something that I didnt get when I bought my pc:S I got the recovery and **** on a partition but no option to just simply repair, so I cant get back the old boot loader for then removing Ubuntu.

---

### Post by duffrecords on 2007-11-05
> **Kurenai0h said:**
> But when I click on the DATA on my computer when I run vista its nothing there and it even with Ubuntu installed, it says that it is all empty (85.0GB free of 85.1GB actually) and I see no sign of Ubuntu anywhere else!
You won't be able to see the Ubuntu installation while you're in Vista, because Windows can't read Ubuntu's file system (ext2 or ext3) without some special workaround.  That's why defrex and rickycodie suggested booting from the Ubuntu live CD.

> **Kurenai0h said:**
> And to uninstall ubuntu I need the Vista install cd something that I didnt get when I bought my pc:S I got the recovery and **** on a partition but no option to just simply repair, so I cant get back the old boot loader for then removing Ubuntu.
So are you saying you want to completely remove Ubuntu?  If that's the case do a Google search for "fix vista master boot record" but be sure to read everything completely before you attempt it.

If, on the other hand, you just want to try installing Ubuntu from scratch, you may want to format the partition during the installation process to make sure everything's clean.  As for the error message about X, you'll need to write it down and post it here so we can understand what the problem is.

---

