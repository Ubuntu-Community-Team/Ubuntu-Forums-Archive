---
title: "Continued Network and USB Issues"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by geekchicohio on 2008-01-09
Hi all,
After an absolutely tragic attempt at upgrading to Gutsy with a fresh install and about a week and a half's worth of trying to get my internet connection functioning by transposing CLI info to my smartphone...
I gave up.

I am now using a fresh install of Feisty and it has been working like a dream until today, here's what's up:

1. A USB flashdrive that I've used with the computer a number of times suddenly is NOT popping up on the desktop when inserted.

2. My wired internet connection, which was working, has STOPPED working since the ethernet modem was taken out of my room (without my knowledge, permission, or supervision) and installed in another room.  To be fairer to my roommates I moved my desktop to the common space with the cable modem and upon plugging my computer into it...I suddenly didn't have a connection where last week I did.

Any thoughts on either of these problems (or, hell, both of them) would be fantastic.

Thanks a ton, you guys have never let me down.

---

### Post by geekchicohio on 2008-01-09
Apologies for the double-post/bump. I wanted to specify that both the internet connection and the flash drive were working on the PC in question on this most recent feisty install. I would be (begrudgingly) understanding if I had changed my setup in ANY WAY when they stopped working, but to my knowledge i have not. No updates, no changes of any kind.

---

### Post by chewearn on 2008-01-09
> **geekchicohio said:**
> 1. A USB flashdrive that I've used with the computer a number of times suddenly is NOT popping up on the desktop when inserted.

Quick questions:
Did the flash drive completely not detected at all, or just no icon appearing on the desktop?
Is the drive still mounted in /media?
Is the drive still detected and appeared as /dev/sdxx?
Did you see success in "dmesg"?

---

### Post by geekchicohio on 2008-01-09
The drive appeared in fdisk and in dmesg (I *think*) but there's nothing on my desktop nor in /media.

---

### Post by chewearn on 2008-01-09
> **geekchicohio said:**
> The drive appeared in fdisk and in dmesg (I *think*) but there's nothing on my desktop nor in /media.

What did you get from dmesg?

---

### Post by geekchicohio on 2008-01-09
Nothing catches my eye as incorrect until the very last line:
```
[ 5057.216923] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed
```

I'm transposing from one PC to another here, so let me know if you need more than that.

---

### Post by geekchicohio on 2008-01-09
I read on another thread that a possible cause of this problem is that I might have removed it from a Windows PC without properly stopping it first. How can I fix things, if this is the case? I've already completely reformatted the drive using the Sandisk drivers included to no avail.

---

### Post by chewearn on 2008-01-09
> **geekchicohio said:**
> Nothing catches my eye as incorrect until the very last line:
```
[ 5057.216923] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed
```I'm transposing from one PC to another here, so let me know if you need more than that.

That line refers to Broadcom wifi, not related to usb flash drive.

Look at dmesg, immediately after the usb drive is plugged in.  Did you get an error message from the usb?

Another thing, if you manually mount the drive in command line, does it work?

---

### Post by geekchicohio on 2008-01-09
```
 new high speed usb device using ehc1_hcd and address 9
configuration #1 chosen from 1 choice
scsi emulation for USB mass storage devices
device found at 9
waiting for device to settle before scanning
device sscan complete
direct-access  Sandisk U3 Cruzer Micro 4.04 PQ:  0 ANSI:  2
device sdb: 3997696 512 byte hdwr sectors (2047)MB
write protect is off
Mode sense 03 00 00 00
assuming drive cahse: write through
device sdb 3997696 512-byte hdwr sectors (2047 MB)
write protect is off 
Mode Sense: 03 00 00 00 00
assuming drive cache: write through
sdb: sdb1
sd 7:0:0:0: Attached scs1 removable disk sdb
sd 7:0:0:0: Attached scs1 generic sgg1 type 0
```

Again, that's all transposed, so I apologize. Let me know if you need anything else.

---

### Post by chewearn on 2008-01-10
> **geekchicohio said:**
> ```
 new high speed usb device using ehc1_hcd and address 9
configuration #1 chosen from 1 choice
scsi emulation for USB mass storage devices
device found at 9
waiting for device to settle before scanning
device sscan complete
direct-access  Sandisk U3 Cruzer Micro 4.04 PQ:  0 ANSI:  2
device sdb: 3997696 512 byte hdwr sectors (2047)MB
write protect is off
Mode sense 03 00 00 00
assuming drive cahse: write through
device sdb 3997696 512-byte hdwr sectors (2047 MB)
write protect is off 
Mode Sense: 03 00 00 00 00
assuming drive cache: write through
sdb: sdb1
sd 7:0:0:0: Attached scs1 removable disk sdb
sd 7:0:0:0: Attached scs1 generic sgg1 type 0
```Again, that's all transposed, so I apologize. Let me know if you need anything else.

The dmesg looks ok.  Can you manually mount:

```
sudo mkdir /mnt/usbdisk
sudo mount -t vfat /dev/sdb1 /mnt/usbdisk

```

If yes, see if some of the things here will help:
[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025)

---

### Post by chewearn on 2008-01-10
> **geekchicohio said:**
> I read on another thread that a possible cause of this problem is that I might have removed it from a Windows PC without properly stopping it first. How can I fix things, if this is the case? I've already completely reformatted the drive using the Sandisk drivers included to no avail.

Oh and I forgot to answer this one; I think it's related to usb drive formatted in NTFS (usually for harddisk usb).

For flash drive, it should be FAT16 or FAT32 format, so it should not be see this problem.

---

### Post by geekchicohio on 2008-01-10
Okay. Great news, I got the flashdrive to mount manually (damn, wish I'd have known to think of that).
Now I'm looking into the bugfix for this whole mess.
And hey, maybe then I can start to contemplate fixing my internet connection.

---

### Post by geekchicohio on 2008-01-10
Alright, I'm going to need some help with this bugfix:

> HERE'S THE FIX:
--------------------

Go into gconf-editor and navigate to /system/storage/default_options/vfat/mount_options, and then remove the "usefree" option from the list. Exit gconf-editor, and try hotplugging your drive again. It works :-)
I really have no idea how to do this.

---

### Post by geekchicohio on 2008-01-10
Sorry to be double/triple posting. I'm solving my own problems.
I got into gconf and found the entry described but there isn't a "usefree" option that I can see. Does this mean this fix isn't for me? Or am I just not seeing it?

EDIT:
Looks like the linked fix is for Gutsy, I'm running Feisty and am thinking this doesn't apply to me.
Any ideas for a fix for my problem? or should I just mount manually whenever I need to?

---

### Post by chewearn on 2008-01-10
> **geekchicohio said:**
> Sorry to be double/triple posting. I'm solving my own problems.
I got into gconf and found the entry described but there isn't a "usefree" option that I can see. Does this mean this fix isn't for me? Or am I just not seeing it?

EDIT:
Looks like the linked fix is for Gutsy, I'm running Feisty and am thinking this doesn't apply to me.
Any ideas for a fix for my problem? or should I just mount manually whenever I need to?

Is it only this particular sandisk usb flash drive failed to work, or all usb flash drive?

---

