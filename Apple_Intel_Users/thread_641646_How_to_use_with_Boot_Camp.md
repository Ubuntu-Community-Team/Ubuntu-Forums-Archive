---
title: "How to use with Boot Camp"
date: 2007-12-15
forum: Apple Intel Users
---

### Post by braveryonions on 2007-12-15
I want to install Ubuntu, but I don't want to delete Leopard, or any of my apps/files. I tried using Boot Camp, put in the Ubuntu disk, and restarted. I got to the install part where you select the drive/partition to install to, and I don't know which one is the one I made in Boot Camp. Can anyone help me?

Yes, I am a n00b to Linux.

---

### Post by cyberdork33 on 2007-12-16
1. Install rEFIt in OSX
2. Boot the Ubuntu Live CD
3. Start the Partition Editor from the Admin menu
4. Delete the last partition on the disk (FAT32)
5. Start Ubuntu installer
6. When it ask where to install to, choose "Free space"

Enjoy

---

### Post by braveryonions on 2007-12-16
What's this partition I am deleting?

---

### Post by tiiim on 2007-12-16
> **braveryonions said:**
> What's this partition I am deleting?

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
Also refit is optional.

---

### Post by braveryonions on 2007-12-16
That link doesn't answer my question, and the installation instructions are much more complicated, and aren't the same as the ones cyberdork33 gave me. I just want to know what that is that I deleting? And how much space will be left on my Leopard partition?

btw, I am using a Mac Mini.

---

### Post by tiiim on 2007-12-16
> **braveryonions said:**
> That link doesn't answer my question, and the installation instructions are much more complicated, and aren't the same as the ones cyberdork33 gave me. I just want to know what that is that I deleting? And how much space will be left on my Leopard partition?

btw, I am using a Mac Mini.

The partition section on that link should be same regardless of mac... the documentation literally walks you through by the hand. Delete the fat 32 partition, ignore the first 2 partitions, one will be efi, and the other is a HFS+ these are both Apple's. You do have the option of of install rEFIt instead of Apple's EFI but this is not required if your just dabbing into linux.

Usually you should delete /dev/sda3 and /dev/sda4 if they exist and then create a partition for root / and then a small partition for swap.

Swap should be just bigger than the amount of RAM in your machine.

NOTE: By creating two partitions bootcamp will no longer help restore your mac to normal if you desire. It is is quite simple to get it back to normal but it wont be via boot camp.

Make sure you dont delete the first 2 partitions as you will loose your data.

If your still unsure please post your partitions here.

you could look at this; [https://help.ubuntu.com/community/Mac_mini](https://help.ubuntu.com/community/Mac_mini) but is for 7.04

---

### Post by cyberdork33 on 2007-12-16
> **braveryonions said:**
> That link doesn't answer my question, and the installation instructions are much more complicated, and aren't the same as the ones cyberdork33 gave me. I just want to know what that is that I deleting? And how much space will be left on my Leopard partition?

btw, I am using a Mac Mini.

Just follow my advice. It is not that complicated. rEFIt is not required, but it makes this more intuitive. It does not replace anything you already have on your machine, it just adds a menu to choose the OS you want on startup.

The partition you are deleting is the windows partition that you create with bootcamp. The amount of space left depends on how much you use to make the bootcamp partition and how big your hard drive is to begin with. Deleting it leaves "free space" so that you can let the ubuntu installer create the needed partitions for you. You don't need to worry about sizing the partitions and making partitions yourself.

---

### Post by tiiim on 2007-12-16
> **cyberdork33 said:**
> Just follow my advice. It is not that complicated. rEFIt is not required, but it makes this more intuitive. It does not replace anything you already have on your machine, it just adds a menu to choose the OS you want on startup.

The partition you are deleting is the windows partition that you create with bootcamp. The amount of space left depends on how much you use to make the bootcamp partition and how big your hard drive is to begin with. Deleting it leaves "free space" so that you can let the ubuntu installer create the needed partitions for you.

agreed follow his advise its a lot easier than mine, but if you want to do things by hand follow mine.

If your still unsure please post us with more info:)

To delete the fat32 partition, open up a terminal type sudo gparted and simply select the fat32 partition, delete and apply then start the ubuntu installer... just dont delete the mac partitions!

---

### Post by braveryonions on 2007-12-16
I deleted FAT32 like cyberdork33 said, but when I tried to install into the free space, it said there was no root filesystem. What do I do now?

Edit: I got it working, I'm in Ubuntu right now. Thanks for your help.

---

### Post by aliyanage on 2007-12-31
@ braveryonions, what exactly did you have to do to pass by the message no rootsystem?
Just trying to install ubuntu gutsy on my new mac book and having a bit of a struggle :-(

regards
aliyanage

---

