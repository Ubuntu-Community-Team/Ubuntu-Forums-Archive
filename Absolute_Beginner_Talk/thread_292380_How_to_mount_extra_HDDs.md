---
title: "How to mount extra HDDs"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Schammy on 2006-11-03
I have three other HDDs that I want to mount.  I used GParted to partition them with ext3.  

I just did a clean install of Edgy (used to have Dapper).  I don't see the "Disk" admin utility that I used to see in Dapper.  In the past I used that to mount my disks.

How do I simply mount a disk in Edgy?? ](*,) 

Thanks!

---

### Post by bodhi.zazen on 2006-11-03
> **Schammy said:**
> I have three other HDDs that I want to mount.  I used GParted to partition them with ext3.  

I just did a clean install of Edgy (used to have Dapper).  I don't see the "Disk" admin utility that I used to see in Dapper.  In the past I used that to mount my disks.

How do I simply mount a disk in Edgy?? ](*,) 

Thanks!

Connect them up.

sudo fdisk -l

or 

ls /dev/disk/by-uuid

to list the partitions.

mount <device> <mount_point> -t ext3 -o <options>

Or add an entry in [/etc/fstab](http://ubuntuforums.org/showthread.php?t=283131) and (sudo) mount -a

---

### Post by Schammy on 2006-11-03
Thanks.  I can definitely follow those steps but isn't there a graphical way of doing it?  I'm surprised that ubuntu wouldn't have some facility built into it that would facilitate mounting of hard drives.

---

### Post by bodhi.zazen on 2006-11-03
What's a graphical tool? :lol:

---

### Post by Schammy on 2006-11-03
Sorry, by graphical tool I mean a tool with a GUI.  In Dapper, Gnome had a utility called "Disk" available from the System > Administration menu.

Is there an equivilent available in Edgy or something I could add?

Thanks.

---

### Post by bodhi.zazen on 2006-11-03
I was joking... ;)

I don't know about a GUI tool for edgy. I would think there would be one. Perhaps someone else can help.

I find graphical tools are limited and fail. That's why I CLI (self defense aginst gui failure). Once you learn a few tricks, it (CLI) is easier. 

[Intro to CLI](http://doc.gwos.org/index.php/CommandLineBeginners)

8)

---

### Post by Schammy on 2006-11-04
Thanks!

Can anyone point me to a GUI tool for mounting hard drives??

---

### Post by ChadMMc on 2006-11-04
Hi,
 I saw your question and yea, I liked the 'disks' in the admin menu and was sorry to see it go.
As far as mounting and unmounting disks. I have a USB HDD and I just plug it in and the system automatically mounts it. to unmount it I open 'Computer' in the Places menu and right click the drive and choose eject.
I assume though you are talking of an internal drive. I looked around Synaptic and came across 'gtkdiskfree', looked at the description and had the synaptic install it.
I pressed Alt-F2 and typed in gtkdiskfree and ran it....It seems that gtkdiskfree can mount and unmount disks. (as well as give you a good look on usage.
I hope this helps.

---

### Post by Schammy on 2006-11-04
Thanks a million.  That sounds like just the thing I'm looking for.  I'll give it a try.

And yes, I'm trying to mount internal drives that I just formatted with GParted.

---

