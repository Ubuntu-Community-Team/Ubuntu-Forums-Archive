---
title: "fdisk -l readout is different from reality"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Delirious on 2007-06-29
In reality the live cd recognized the drive my OS's are on as sda and my data drive as sdb. After installing fdisk says its the other way around. The icons for a few sda partitions on my desktop are correctly labeled and point to the correct drive like they should. 

Gparted and Fdisk -l both arent reading it right.

I dont get it?

[IMG]http://i4.photobucket.com/albums/y147/Typicalsloan/Screenshot-rootUbuntu1.png[/IMG]

---

### Post by kidders on 2007-06-30
Hi there,

The /dev node names of block devices are essentially arbitrary, and don't make any real difference to anything. For instance, there is no particular reason why /dev/sda *must* point to the same physical device in two different environments (eg a LiveCD and a proper Linux installation).

Are you having a problem of some kind?

---

### Post by Delirious on 2007-07-01
> **kidders said:**
> Hi there,

The /dev node names of block devices are essentially arbitrary, and don't make any real difference to anything. For instance, there is no particular reason why /dev/sda *must* point to the same physical device in two different environments (eg a LiveCD and a proper Linux installation).

Are you having a problem of some kind?

No everything is good, just wondering why it wasnt consistent.

---

### Post by kidders on 2007-07-01
There could be lots of reasons, really. Most have to do with what your BIOS tells your OS, and how it interprets & applies that information. You can *enforce* consistency if you want to though, by setting up udev rules to name devices the way you like them.

---

