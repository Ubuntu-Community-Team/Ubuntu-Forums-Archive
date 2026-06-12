---
title: "Ubuntu 6.06 Gparted No devices Detected, (Can't install)"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Ryugin on 2007-04-02
Hi, I'm trying to convert from Windows Vista Home Basic to Ubuntu 6.06 LTS

I'm using the Live CD.
For some reason when I get to step 5 of 6 the installer stops, It just sit there with the spinning circle cursor. Also when I run Gparted, It say the "No devices detected" at the bottom.

I'm running:
 
Compaq Computer
Intel Celeron D Processor 356
512 RAM
120GB Hard Drive
Ati Radeon Xpress 1100

I've already searched the forum, and the only thing I found was to help a Dell 1505...

I already added pci=nomsi
Here are some screenshots

---

### Post by Ryugin on 2007-04-02
I'm using Gparted 0.1

---

### Post by Gilgad Drumheller on 2007-04-02
Your drives are sata, i assume?
I'm having a similar problem, with no drives showing up in gparted.
I was using the fiesty herd5 cd, which i've been told has a wonky partitioner.  I'm hoping the beta will do a better job, but from what you say, it doesn't seem hopeful.

I'm sure its one of the boot options, but i've tried quite a few and no dice.

---

### Post by jerryrw on 2007-04-02
Open a terminal on the live cd and post the results of:

sudo fdisk -l

thats a lowercase ell

---

### Post by Gilgad Drumheller on 2007-04-02
For me at least, sudo fdisk -l prints nothing but an endline.
Additionally, my /etc/fstab shows:
```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nouid,nodev 0 0
```
I assume these are the ramdrives set up by the liveCD

---

### Post by Ryugin on 2007-04-02
Nothing happens when I use, "sudo fdisk -l" or "fdisk -l"

---

### Post by jerryrw on 2007-04-02
I haven't used Vista since beta, but I know that then it was doing some very unfriendly things to disks.  I'm just making some trouble shooting guess work here SO....

Can you manually mount any HD partitions using sudo mount -t ntfs /dev/sda1 /mnt/vista
Can you run the stand alone GParted CD that is at sourceforge?
Can you access the HD from another LiveCD distro?
There may be kernel options that you need to pass especially if this is a lappy.
Is your hard disk controller a raid controller?  If so you may need drivers

Hope something here helps

---

### Post by Ryugin on 2007-04-02
> **jerryrw said:**
> I haven't used Vista since beta, but I know that then it was doing some very unfriendly things to disks.  I'm just making some trouble shooting guess work here SO....

Can you manually mount any HD partitions using sudo mount -t ntfs /dev/sda1 /mnt/vista
Can you run the stand alone GParted CD that is at sourceforge?
Can you access the HD from another LiveCD distro?
There may be kernel options that you need to pass especially if this is a lappy.
Is your hard disk controller a raid controller?  If so you may need drivers

Hope something here helps

Excluding the first thing you said. I have no idea what you're talking about.
I tried the first thing it came out:

ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda1 /mnt/vista
mount: mount point /mnt/vista does not exist
ubuntu@ubuntu:~$

---

### Post by jerryrw on 2007-04-02
try mounting directly to /mnt :sorry been a while since I've worked a LiveCd

sudo mount -t ntfs /dev/sda1 /mnt

also try replacing that 1 with a 2

The other options are if you can download a GParted Live disk from [http://sourceforge.net/projects/gparted/](http://sourceforge.net/projects/gparted/)  and see if that can identify your drive

The other LiveCD option is if you download something like the Knoppix Live Cd and try that to see if it can ID the disks.

The other thing is on some machines you have to pass options to the kernel at boot time  such as pci=noacpi and such there are many options for this

To enter these options: On the first boot screen (the one giving you boot options) press F6 to edit the boot options line. And add the option.

Another thing to look at is to use Vista to find out the specs of your hardware.  As I have been using *nix alot lately my vista skills are rusty, but I know it can be done.

Hope I'm helping a little here

---

### Post by jerryrw on 2007-04-02
Also found this link describing boot parameters
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/boot-parms.html]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/boot-parms.html")

---

### Post by Gilgad Drumheller on 2007-04-02
In terms of helping Ryugin, there is a file on your comp (/etc/fstab) that lists hard drives linux "knows of", but has not mounted.  However, i bet its similar to mine, being that our problems are pretty much identical.  You can view it with:

ls /etc/fstab (i think, or just do it graphically).

I'm betting it will be the same as mine.  If the drive isn't listed there, no number of mount comands will make it appear (as far as i know, anyway)

---

### Post by Ryugin on 2007-04-29
So, there's nothing I can do?

---

