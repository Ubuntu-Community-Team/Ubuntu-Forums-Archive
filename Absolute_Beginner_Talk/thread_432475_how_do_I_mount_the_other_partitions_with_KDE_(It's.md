---
title: "how do I mount the other partitions with KDE? (It's easy under Gnome!) [Resolved]"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-05-04
Yes, how is it done? I can only seem to find a way to mount media but not other partitions on the same disk, such as my MacOS partition or share partition. I do this all the time under Gnome and it very easy.

---

### Post by chriscando on 2007-05-04
You can do it from the terminal. If you know what partition it is you can use the 'mount' command. For example I have a spare partiton on /dev/sda3, so to mount it to some directory first create the directory and:
```
sudo mount /dev/sda3 /home/me/somedirectory
```
then to unmount it:
```
sudo umount /home/me/somedirectory
```
The key thing is knowing what partition it is (/dev/sdaX)
If you dont know you can try just typing the mount command to see what is already mounted.

---

### Post by Xarok on 2007-05-04
Well I must say, that is rather dumb that you have to do that through the terminal.


If you have Gnome Partition Editor installed it can show you which partitions you have, so you don't have to just *guess*.

Well, your method worked!

Thanks for the help

Oh, is there a way to make it run this command on boot-up?

PS
I think you mean "hda3". lol

---

### Post by aysiu on 2007-05-04
Well, I can assure you this isn't a Gnome/KDE thing but a Ubuntu/Kubuntu thing.

Knoppix and Mepis are both KDE distros and have easy point-and-click mounting of partitions--even easier than Ubuntu's.

---

### Post by Xarok on 2007-05-04
> **aysiu said:**
> Well, I can assure you this isn't a Gnome/KDE thing but a Ubuntu/Kubuntu thing.

Knoppix and Mepis are both KDE distros and have easy point-and-click mounting of partitions--even easier than Ubuntu's.

Oh shi... the distros are *that* different?

I should check other ones out... hmm. if they could use CD's to install instead of DVD's... gosh darn it. If only I had a comp that could write DVD's.

---

### Post by aysiu on 2007-05-04
Yes, they're that different. In Knoppix, for example, all partitions and drives start off unmounted and show up as icons on the desktop. You click a drive icon, and it mounts and opens. You right-click it and can make it read/write instead of read-only.

---

### Post by Xarok on 2007-05-04
> **aysiu said:**
> Yes, they're that different. In Knoppix, for example, all partitions and drives start off unmounted and show up as icons on the desktop. You click a drive icon, and it mounts and opens. You right-click it and can make it read/write instead of read-only.

What!? That's so damn useful! Can this be set up in Ubuntu or Kubuntu?
Are they things you change in the configuration editor? Similar in the way that you can show trashcan and computer icons on the desktop?

---

### Post by aysiu on 2007-05-04
> **Xarok said:**
> What!? That's so damn useful! Can this be set up in Ubuntu or Kubuntu?
Are they things you change in the configuration editor? Similar in the way that you can show trashcan and computer icons on the desktop?
I don't know how to set that up in Ubuntu or Kubuntu. I've often wondered why such a thing isn't implemented in Ubuntu/Kubuntu, seeing as how Knoppix is open source.

---

### Post by Xarok on 2007-05-04
I just figured out that you can set up mounting and automatic mounting of partitions in the System Settings > Advanced > Disk & Filesystems > Administator Mode > *right-click"Modify"* > *fill out mount point* > *check "enable at start-up"*

---

