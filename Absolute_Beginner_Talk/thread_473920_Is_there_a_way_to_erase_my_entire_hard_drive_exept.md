---
title: "Is there a way to erase my entire hard drive exept fiesty"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-14
had install problems got it to work, but only have 14 gigs left on 40 gig hard drive. and when I boot I get the option of booting like 5 ubuntus and a pclinux i want to recover this disc space. Can someone help please? Thanks

---

### Post by original_jamingrit on 2007-06-14
The 5 ubuntus that show up are all pointed towards the same partition, for kernel and recovery purposes.  As for the pclinux, I'm not sure.

---

### Post by OldTimeTech on 2007-06-14
have you tried gparted on your installation disk

---

### Post by phr0ze on 2007-06-14
Yes, I'm curious to see your partition sizes. There may be a partition in there that is left over from a previous try.

---

### Post by swoll1980 on 2007-06-14
how do i see my patition sizes?

---

### Post by drs305 on 2007-06-14
```
sudo fdisk -l
```
small L, not a 1

---

### Post by swoll1980 on 2007-06-14
oops

---

### Post by drs305 on 2007-06-14
Note it's a small L, not a One

---

### Post by swoll1980 on 2007-06-14
oops

---

### Post by swoll1980 on 2007-06-14
ok used " fdisk -l " and got 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2264    18185548+  83  Linux
/dev/sda2            4560        4863     2441880   82  Linux swap / Solaris
/dev/sda3   *        2265        4466    17687565   83  Linux
/dev/sda4            4467        4559      747022+   5  Extended
/dev/sda5            4467        4559      746991   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by drs305 on 2007-06-14
I have one more request and then have to go. Others can help you out.

The good news is we can recover space on your hard drive.

From terminal, start gparted and answer a few questions:
```
sudo gparted
```


Which partition has the root partition ( the one with the mount point of / )?
Do you have a partition listed as 'home'?  Probably not unless you asked the installation disk to set it up.

If you know how to take a picture of the gparted screen and post it here that would be helpful.

---

### Post by swoll1980 on 2007-06-14
ok ill do that

---

### Post by swoll1980 on 2007-06-14
how do I post my gparted snap shot

---

