---
title: "on which file system i must install ubuntu?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by 3enith on 2007-07-15
on which file system i must install ubuntu?

---

### Post by Vajra Vrtti on 2007-07-15
Ubuntu uses the *ext3* file system by default.

---

### Post by 3enith on 2007-07-15
but does ubuntu make it automatically one on a ntfs partition ?

---

### Post by Vajra Vrtti on 2007-07-15
I suppose you have a Windows machine and is thinking about trying Ubuntu. You probably have only one NTFS partition in your disk. 

When you install Ubuntu, the installer will resize that partition to make room for Ubuntu and create an ext3 partition for it (plus a swap partition). It will install the Grub boot manager, so that when you boot the system you will have a new screen where you will be able to choose Ubuntu or Windows.

But you may try Ubuntu just booting the Live CD, without installing it.

---

### Post by 3enith on 2007-07-15
i have 2 HDD  160gb with three partitions C,D,E [windows xp installed] and other 80gb with two partitions H,I i want to install ubuntu on my 80gd HDD on partition (H) and format partition (I) to a ubuntu file system(without lossing xp) now what i must do ??? (thanx)

---

### Post by ReaderRat on 2007-07-15
Try this to see if it fits:

[[color=blue]Dual-Boot (2 Hdds)[/color]](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by Vajra Vrtti on 2007-07-15
> **3enith said:**
> i have 2 HDD  160gb with three partitions C,D,E [windows xp installed] and other 80gb with two partitions H,I i want to install ubuntu on my 80gd HDD on partition (H) and format partition (I) to a ubuntu file system(without lossing xp) now what i must do ??? (thanx)
I can see partitioning is not a problem for you. I suggest the following schema for you secondary 80GB disk:
[LIST=1]
[*]10GB ext3 Ubuntu partition.
[*]swap partition, twice the size of your RAM.
[*]ext3 data partition (60+MB).
[/LIST]
Some people would recommend you to put your */home* directory in the 3rd partition. I don't do that. I keep */home* in the root partition and use it only for storing application settings. I keep my data isolated in the other partition, so that I can reinstall the system without worrying about backups. That and more a few tricks about Firefox and Thunderbird.

---

### Post by Vajra Vrtti on 2007-07-15
To follow my suggestions (or something like that) you have to chose the manual partitioning during Ubuntu installation.

---

### Post by duydaniel on 2007-07-17
> **Vajra Vrtti said:**
> I can see partitioning is not a problem for you. I suggest the following schema for you secondary 80GB disk:
[LIST=1]
[*]10GB ext3 Ubuntu partition.
[*]swap partition, twice the size of your RAM.
[*]ext3 data partition (60+MB).
[/LIST]
Some people would recommend you to put your */home* directory in the 3rd partition. I don't do that. I keep */home* in the root partition and use it only for storing application settings. I keep my data isolated in the other partition, so that I can reinstall the system without worrying about backups. That and more a few tricks about Firefox and Thunderbird.

Hi there. Just curious, but what is swap partition use for? I thought it was something like windows pagefile in XP. Do I need swap if I have 2GB ram? :confused: since I disable Vista pagefile on the same machine.

---

### Post by rillip on 2007-07-17
Swap is essentially the same as the pagefile.  I would not recommend disabling it, however.  Even if it's never strictly needed, i.e. you're not running out of RAM, each OS anticipates that paging will be done at some point.  It may use it as a way to keep RAM arranged and non fragmented. By disabling it you might actually be hurting system performance in the long run.  This is all just supposition, of course.

---

### Post by forestpixie on 2007-07-17
Yes you're right it is - but the sizing issue is a bit different I believe. Mine is 1Gb with 1Gb physical - the swap does get used sometimes - but then Ubuntu (and I assume Linux in general) actually uses your physical memory befor it gets to the swap (I think)

I'd be inclined to have a swap but change the size. I'm sure someone else will look and comment.

If you look around the forum you'll find plenty to read - :)

EDIT - bit slow I think ;)

---

### Post by Vajra Vrtti on 2007-07-17
> **duydaniel said:**
> Do I need swap if I have 2GB ram?
I agree with rillip. I think I've read something about problems with some applications if you have no swap at all, but I don't remember where. 
I'd recommend at least a small swap, just in case. You can also use a swap file instead of a swap partition, but I've never done that.

---

