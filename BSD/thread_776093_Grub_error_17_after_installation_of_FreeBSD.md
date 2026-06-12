---
title: "Grub error 17 after installation of FreeBSD"
date: 2008-04-30
forum: BSD
---

### Post by cdiem on 2008-04-30
Not sure if this is the right place to post. If not, please, let the thread be moved.

I installed FreeBSD together with a Debian install. And then the grub screen says "error 17", and I'm not able to load either system.

My harddisk is partitioned the following way (main partitions):
sda1 | ext3         | /home | 66gb
sda2 | linux-swap   |       | 1gb
sda3 | ext3         | /     | 15gb
sda4 | ufs          | ?     | 30gb

At sda3 there's a label "boot", so I guess there's where grub is installed. 
and sda4 is divided into 5 more partitions (logical) - sda5 till sda9 for the bsd. When I did the installation of the FreeBSD, I used the option "Leave the MBR untouched". 
What I've tried so far:
1. Change something in the BIOS - no result, as I have only one harddisk.
2. From Ubuntu LiveCD I tried to mount /dev/sda3 and change the grub settings; the drive is unmountable. The error message when trying to mount is: 

mount:wrong fs type, bad option, bad superblock on /dev/sda3, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail or so.

When I do a dmesg | tail, it gives:
ufs was compiled with read-only support, can't be mounted as read-write
3. From a Ubuntu LiveCD I tried to lie the system that I'm going to install it and set mountpoints for my partitions; I was amazed to understand, that the LiveCD's installation program actually thinks I have ext3 partition at sda4 and that I do not have a filesystem at sda3! Then I restarted the computer with the FreeBSD installation diskNo1 and at sda4 it recognizes a ufs filesystem! Also, from a LiveCD of Ubuntu I ran Gparted - and thanks to my USB I have some screenshots here to show.
What's strange, the 32GB media is mounted without a problem (there should be ufs on it) and without any files on it (it should be full with the freebsd files)
Could I have messed the installation of FreeBSD so much, that I have installed it on my / partition, or is it just a Grub and MBR error at the disk allocation table? Please, I'm desperate on this.

---

### Post by ibutho on 2008-04-30
It seems like you installed FreeBSD in /dev/sda3. AFAIK FreeBSD can only be installed in primary partitions, so reserving logical partitions for FreeBSD is no good.

---

### Post by cdiem on 2008-04-30
I'm afraid it could be possible that I actually have installed it on my linux (Debian) / partition.
If I make a reinstall, would I be able to install FreeBSD at all (with this disk-partitioning scheme that I have)? I'm sure I told the FreeBSD installer to install at sda4; I also remember it warning me for some strange naming things. How can I (by reinstalling) have the two operating systems together?
If I have just sda1-sda4 (which seem to be logical partitions, as I get it), then is it right, that the only way to get my hands dirty with FreeBSD (after the proper reinstallation of my current system, obviously) is via Virtualbox/Vmware?

---

### Post by ibutho on 2008-04-30
The way you setup your hard drive, /dev/sda1 to /dev/sda4 are primary partitions which is ok if you want to install FreeBSD. What you can do is reinstall Debian in /dev/sda3. After that use fdisk to change the partition type of /dev/sda4 to a FreeBSD partition type (a5 in fdisk) since you want to use it for FreeBSD. This will make it easier for you to recognise the right partition for FreeBSD during the installation.

---

### Post by cdiem on 2008-04-30
I attach here the settings, with which I made the installation of FreeBSD. If you're sure I have installed it on the wrong place, then tomorrow I will be reinstalling it (hopefully right). Thanks very much for your answers.

---

### Post by ibutho on 2008-04-30
Yes, I'm pretty sure you installed it in what Linux would term /dev/sda3. You can double check by running "fdisk -l" or "parted -l" from a linux live disc.

---

