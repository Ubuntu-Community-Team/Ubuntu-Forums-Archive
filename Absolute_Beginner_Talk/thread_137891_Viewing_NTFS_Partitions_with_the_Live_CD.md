---
title: "Viewing NTFS Partitions with the Live CD"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by WebScud on 2006-02-28
My Windows XP on my primary box installation took a dive about an hour ago.  I'm trying to access the C drive via my Ubuntu Live CD to burn the stuff I don't want to loost to a DVD, but I am having no sucess accessing any of the paritions.

Whenever I start "Disk Manager" it just searches and searches and the mouse remains in the active icon-state.  Any suggestions?  There's a lot of stuff I can't bare to loose.  :-/

---

### Post by Jucato on 2006-02-28
have you tried mounting it?
```
sudo mount /dev/xxx /mnt/xxx
```
I'm not entirely sure about this, though.

How long does your cursor remain in active state? Sometimes the Live CD takes a bit of time to work because it's only running on your PC's RAM and data reading on CDs is generally slow.

---

### Post by Turtle.net on 2006-02-28
Just try [http://ubuntuguide.org/#mountunmountntfs]("http://ubuntuguide.org/#mountunmountntfs")
to mount your NTFS partition.
This guide will certainly help you for lot of things ;)

Good luck

---

### Post by WebScud on 2006-02-28
[quote=Fenyx]have you tried mounting it?
 ```
sudo mount /dev/xxx /mnt/xxx
``` I'm not entirely sure about this, though.
 
How long does your cursor remain in active state? Sometimes the Live CD takes a bit of time to work because it's only running on your PC's RAM and data reading on CDs is generally slow.[/quote] 
 It stayed in the active state for 10+ minutes twice.

[quote=Turtle.net]Just try [http://ubuntuguide.org/#mountunmountntfs]("http://ubuntuguide.org/#mountunmountntfs")
to mount your NTFS partition.
This guide will certainly help you for lot of things ;)

Good luck[/quote] 
Thank you both very much.  I'll be back with my results...

---

### Post by WebScud on 2006-02-28
```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

I did this as outlined in the FAQ with hda1 through hda9, but it said that none of the hard disks existed.  Can that be right?  Should I be using "C" or "System" (what I named the drive) instead of "hda*x*"?

---

### Post by Herman on 2006-02-28
Use the command: ```
sudo fdisk -l 
```to check which partitions are there and identify the proper number like hda1 maybe that you should substitute for 'hdaX'. Maybe it should be 'sda'X?

Maybe try looking at it with GParted on a live CD and seeing what's there. (see my second sig link and download the latest .iso for that) you can actually use GParted to copy your partitions to an external drive too if you need to, or to a new drive in your system. 
I hope this helps (Herman)

---

### Post by WebScud on 2006-02-28
[quote=Herman]Use the command: ```
sudo fdisk -l 
```to check which partitions are there and identify the proper number like hda1 maybe that you should substitute for 'hdaX'. Maybe it should be 'sda'X?

Maybe try looking at it with GParted on a live CD and seeing what's there. (see my second sig link and download the latest .iso for that) you can actually use GParted to copy your partitions to an external drive too if you need to, or to a new drive in your system. 
I hope this helps (Herman)[/quote]

Ooh, it does come up sda1.  Is that because it's a SATA drive?

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      116388      126889    84344761   69  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?      105915      222310   934940732+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?           1           1           0   74  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4               1      213826  1717556736    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

But sda1 through sda 4 didn't work either.

I'm going to try GParted next and see how that works.

---

### Post by Herman on 2006-02-28
>  Ooh, it does come up sda1. Is that because it's a SATA drive?That's right, yes, if it's a sata drive it needs to be addressed as 'sda' instead of the regular 'hda'. Looks like you are doing everything right with the Live CD now.

But I am very worried about the way sudo fdisk -l said your partitions do not end on the cylinder boundaries, and filesystems unknown. I am pretty sure that means your partition table is corrupted (by a virus maybe?) and I don't think GParted will be able to help your there at in this case, unless there is something more here I don't know yet. (That's likely too). GParted is good for rescuing data by copying whole partitions to another drive as long as the partition table is okay. It might still copy your partitions to another (healthy) drive, it would be worth a try. This problem might prove a little more complicated than that though.

Did anything unusual happen before his problem became evident that you can remember? Any error messages in the past day or two? Power problems in your town/lightning storms etc?

---

### Post by WebScud on 2006-02-28
Okay, I'm in GParted, but I can't figure how how to view files on the partition.

---

### Post by WebScud on 2006-02-28
Sorry, I didn't refresh the thread before I posted the my last reply.

The system was running fine up until the NTLDR message I got tonight.  All the HOWTO's I could find on that subject involved a floppy drive, which I no longer have.  So I figured it would be time for one of those "Linux rescues" I keep hearing about.  ;)

---

### Post by Herman on 2006-03-01
> The system was running fine up until the NTLDR message I got tonight. All the HOWTO's I could find on that subject involved a floppy drive, which I no longer have. So I figured it would be time for one of those "Linux rescues" I keep hearing about. I would love to be able to help you with a file rescue using the Ubuntu Breezy Live CD or GParted, but I think this particular problem is one that makes both of these types of operations impossible, sadly, as far as I know.

If you are paying good money to an antivirus sofware company for protecting you, now would be a good time to call them (on the phone maybe) and see if they can help you. They should be very interested in helping you, as well as learning about what it might be. They might have an antidote already prepared that you can run somehow. They should have the first try, and then after that post back here and let us know how you got along (what they said) and if you still need help we'll see what we can do. 
Good luck with it, (Herman)

---

### Post by WebScud on 2006-03-01
I know this is moving a bit away from Ubuntu talk...

I'm waiting on an e-mail back from Symantec.  Phone support costs $29.95.  LAME.  Anyway.

I've tried GAG and BootIT! NG today, to no avail.  After using GAG I got the error message "No active parition".

So, I found this [Microsoft article]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/dm_active_partition.mspx").  Running "diskpart" via the XP CD's repair console shows me that I only have one 131GB partition, which is drive X.  However, it says "131072 MB ( 131071 MB free)".  So I don't know what the problem is.  I'm really lost now.

I think I'm going to install a second hard drive and install XP to see if I can access the files that way.  I'll keep you posted.

---

