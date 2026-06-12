---
title: "terminal command for formatting external drive"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by willfriedwald on 2008-03-15
am sure you guys can answer this one in your sleep

I have an external hard drive that's not mounting - gParted says it's unallocated, but for some reason, gP can NOT format it or create a volume on it -

I thought that I would try terminal

am trying to format it into DOS (fat32)

the drive is shown in gP as 
 /dev/sdq

here are the results of my first shot :

will@will-linux:~$ sudo mkfs.FAT32 /dev/sdq
[sudo] password for will:
sudo: mkfs.FAT32: command not found
will@will-linux:~$ sudo mkfs.fat32 /dev/sdq
sudo: mkfs.fat32: command not found
will@will-linux:~$ 

what am I doing wrong?

thanks

w

---

### Post by glennric on 2008-03-15
Try mkfs.vfat
Although, I don't see why that would work if gparted can't do it.

---

### Post by handydan918 on 2008-03-15
Try mkfs.vfat

---

### Post by glennric on 2008-03-15
> **handydan918 said:**
> Try mkfs.vfat

Are you a parrot?

---

### Post by taurus on 2008-03-15
You need to create a partition, /dev/sdq1, first before you can format it.

```
sudo cfdisk /dev/sdq
```

---

### Post by willfriedwald on 2008-03-15
you're right!

will@will-linux:~$ sudo mkfs.vfat /dev/sdq
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: failed whilst writing reserved sector

will try to format it in my mac and see if anything happens....

---------------

thanks for this too -

sudo cfdisk /dev/sdq

I tried it, got the following error message

"fatal error - press any key to exit fdisk"

!!!

oh well - I guess the drive is buggy - I hope the mac can format it... I tend to be dubious!

w

---

### Post by glennric on 2008-03-15
Does the drive have some sort of read-only switch or something?

---

### Post by willfriedwald on 2008-03-15
well it isn't mounting or being read at all!

funny thing - I bought two of these 320 GB drives - 

I plugged 'em both in; one mounted immediately & I have no problem r&w-ing to it - 

the other one is the one that's giving me sirrus!

HOWEVER .... the troublesome one IS actually mounting on the Mac; going to try and format it in DOS on the Mac and see if it can then be read on the linux - if so, then I will reformat it in linux.

w

---

### Post by handydan918 on 2008-03-15
> **glennric said:**
> Are you a parrot?

Squauwck!!

It was posted virtually simul w/ yours, hence my edit.

---

### Post by forrestcupp on 2008-03-15
> **willfriedwald said:**
> 
I have an external hard drive that's not mounting - gParted says it's unallocated, but for some reason, gP can NOT format it or create a volume on it -


Were you using GParted LiveCD, or the GParted that comes with Ubuntu?  If you weren't already, try to use the GParted LiveCD.

---

### Post by willfriedwald on 2008-03-15
oh that's extreme - I guess it's worth a try!

for what it's worth, what are the formats that a PC can read?  Or, to put it another way, formats that both linux-ubuntu and a DOS windows machine can r & w to?

w

---

### Post by handydan918 on 2008-03-18
> **willfriedwald said:**
> oh that's extreme - I guess it's worth a try!

for what it's worth, what are the formats that a PC can read?  Or, to put it another way, formats that both linux-ubuntu and a DOS windows machine can r & w to?

w

If by "DOS Windows" you mean pre-NT architecture, then fat32 it is. If you mean Windows 3.5, 4.0, 2000, and XP, then NTFS can be read and written to by linux as well.

---

