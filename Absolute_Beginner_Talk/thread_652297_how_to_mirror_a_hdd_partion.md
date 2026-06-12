---
title: "how to mirror a hdd partion?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by akopacsi on 2007-12-28
I have a dual-boot (Windows XP / Ubuntu) system. I reinstall this computer quite often and I hate that it takes ages to download security patches from Microsoft, to install my softwares and to restore my fave settings. So I would like to make a complete copy of my fine-tuned and patched XP system to a disk or an hdd. Is it possible to make a copy that can be loaded back to an empty NTSF partition and started as it was installed from skratch?
I know there is a command called dd... but I am not sure if I could make a working copy of a Windows with this. Any advice?

---

### Post by GGLucas on 2007-12-28
Using dd creates an exact copy of a file (or /dev/sdX or /dev/hdX, etc), it's a very powerful tool that you could very well ruin your system with, but as far as I know it should work for making copies of partitions.
You should find the /dev/ address of your windows partition first, be sure not to enter the wrong one, don't want to overwrite any of your linux partitions.

Please don't try these before anyone aside from me confirms it, I haven't tried it myself and I'd hate to cause an exploding system XD

To backup a partition to a file in your home directory
```
sudo dd if=/dev/PARTITION of=~/windows.backup bs=1024
```

To restore it (WARNING: dangerous)
```
sudo dd if=~/windows.backup of=/dev/PARTITION bs=1024
```

You might be better off getting a graphical app or boot disk for it, though.

---

### Post by zach12 on 2007-12-28
So this command copy's the partion right?

---

### Post by GGLucas on 2007-12-28
It should, yes, byte for byte, it can copy anything really, which makes it very powerful (you could copy /dev/zero into a partition and wipe it out completely).

Read
```
man dd
```

for more information on how to use it.

---

### Post by zach12 on 2007-12-28
Hey 
how long should it take?


Thanks


PS It's a 30gb partion

---

### Post by VorDesigns on 2007-12-28
what I would suggest is to create a Virtual installation of your favorite XP installation; keep a backup.  Reload at need.

---

### Post by GGLucas on 2007-12-28
It would take about the same amount of time as copying a 30gb file from one folder to another would take, I guess, can't take too long, though. Sadly, there is no progress bar, so you'll have to browse to the folder and see the file gradually increase in size to see how far it is.

---

