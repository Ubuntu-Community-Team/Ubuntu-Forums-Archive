---
title: "Hidden partition - Install worries"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2006-01-02
Hey,

I've a Packard Bell laptop, and I'm ready to switch from Windows to Ubuntu, but, I'm a teeny weeny bit worried about the installation process.

There's a hidden partition with Windows restoration files on it - Packard Bell's way of giving you your Windows CDs.

In the live cd, when I type
```
sudo fdisk -l
```
It says that this hidden partition is /dev/hda1, and the other partition with all my files on is /dev/hda2.

So, I'd obviously want to install Ubuntu on the 'hda2', but I'm not sure about the install process and how it'll handle this.

Also, as I'm on a laptop, should I do the install with the battery plugged in, or not? Would this make a difference?

I'd be really greatful if someone could  explain what'd happen.

Thanks

---

### Post by az on 2006-01-02
[QUOTE=Jimmey]Hey,

I've a Packard Bell laptop, and I'm ready to switch from Windows to Ubuntu, but, I'm a teeny weeny bit worried about the installation process.

There's a hidden partition with Windows restoration files on it - Packard Bell's way of giving you your Windows CDs.

In the live cd, when I type
```
sudo fdisk -l
```
It says that this hidden partition is /dev/hda1, and the other partition with all my files on is /dev/hda2.

So, I'd obviously want to install Ubuntu on the 'hda2', but I'm not sure about the install process and how it'll handle this.

I'd be really greatful if someone could  explain what'd happen.

Thanks[/QUOTE]

The ubuntu installer will offer to split hda2 for you.  Windows will stay there and ubuntu will be on the next partition (hda3 or hda5 depending on whether it creates a logical or extended partition)  Don't worry.

---

### Post by Jimmey on 2006-01-02
So, I could just erase the contents of hda2, and install Ubuntu there?
And should I do the install with the battery plugged in, or not?

---

### Post by Jimmey on 2006-01-02
Anyone?

---

### Post by iand675@gmail.com on 2006-01-02
presumeably, your laptop can be plugged into the wall with the battery still connected. This would be your best option

---

### Post by az on 2006-01-02
[QUOTE=Jimmey]So, I could just erase the contents of hda2, and install Ubuntu there?
And should I do the install with the battery plugged in, or not?[/QUOTE]
You want to install ubuntu and keep that small partition with the windows image?

Because if you just want to erase everything, just pick the option to use the entire disk.  The partition table will be rewritten and you will end up with a straightforward partitioning scheme.

If you want to keep that partition, go into manual partitoining, delete hda2 and that will then show you the one small partition and the rest as FREE SPACE.  Then click guided partitioning and the installer will do all the rest.  Hit yes and you are good to go.  It will create your root and swap partitions using the free space whicl preserving what was already there.

---

### Post by kingsidy on 2006-01-02
usually the hidden partition is at the very beginning of the disk. If you want to dual boot, make sure that you either reformat the whole drive and install, or that if you want to keep things as is, make sure that you do not delete that hidden parttition. I had a hidden partition as well and when i deleted it to make room for ubuntu my system would not boot into windows anymore.

---

