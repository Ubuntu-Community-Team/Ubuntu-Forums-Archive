---
title: "2 Beginner Questions"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by SultanTravi on 2006-11-27
I have a couple of problems right now with my Ubuntu.  I'm working on getting Windows back, as it ended up on a hidden partition.

In order to get that hidden partition fixed, I need to install some software.  However, when I try, the ./configure command results in a could not compile C++ error.  

I guess I need a compiler.  I'm using edgy.  I've seen (in searches) a lot about G++ or GC or something like that, but can't find it in add/remove programs. If someone could guide me as to what to install, that'd be great.

Also, I have a window that's stuck open (I can't get it closed).  Is there a terminal command that's similar to ctrl-alt-del in that I could end the process/task? 

Thanks a ton

---

### Post by taurus on 2006-11-27
1.
```
sudo aptitude install build-essential
```

2.  There is a kill command to terminate a process...
```
man kill
```

---

### Post by coder_ on 2006-11-27
g++ is a C++ compiler.
gcc is the other one you are looking for.

xkill lets you kill a window.  But you should use kill.

---

### Post by Foudre on 2006-11-27
well, you can look up gparted, or qtparted. if you can't find it installable you can still find a live cd to boot from i have the disk, i can't remember where the website is, but that would be the easiest way to chance the partition from hidden to not

---

### Post by SultanTravi on 2006-11-27
Thanks guys.. yeah I have Gparted now.. but it says the partition isn't hidden! I may be in trouble. Ugh.

Well, thanks for the advice for installing and especially killing that thing.

---

### Post by taurus on 2006-11-27
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by SultanTravi on 2006-11-27
> **taurus said:**
> What's the output of this command from a terminal?

```
sudo fdisk -l
```

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8617    69216021    7  HPFS/NTFS
/dev/sda2            8618        9637     8193150   83  Linux
/dev/sda3            9638        9729      738990   82  Linux swap / Solaris

```

I need to get that Id on the first partition, number 7, to say 17, to fix it (from what I've seen in searches).

---

### Post by taurus on 2006-11-27
Are you talking about the /dev/sda1 is the hidden partition?

---

### Post by SultanTravi on 2006-11-27
> **taurus said:**
> Are you talking about the /dev/sda1 is the hidden partition?

Hmm.. I opened Gparted, clicked hidden, unclicked hidden, and now I'm posting from my Windows install :D 

Thanks! Major problems have been solved.

---

