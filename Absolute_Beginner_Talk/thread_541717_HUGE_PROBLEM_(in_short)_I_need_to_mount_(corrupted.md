---
title: "HUGE PROBLEM (in short) I need to mount (corrupted) ntfs partition..."
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by bkkenny on 2007-09-03
(This may be in the wrong section if so could someone please move it to somewhere more appropriate? This may also be a long story but I want to give as much detail as I can.)

I am running Ubuntu 7.04 on a separate partition to my XP install. One day I ran out of space on my Ubuntu partition. I booted into XP and ran a partition editor to resize the partitions; I was making the Windows one smaller and the Ubuntu one bigger. There was some sort of error during the resize of the Windows one, now I get a BSOD whenever I try to boot into it.
I used to be able to access this partition from Ubuntu so that I could access my old documents, music etc. now I cannot.
I think this was caused when I unmounted that partition using gparted.
Now I cannot mount it. I have tried following other forum posts which said to do stuff like this:

```
sudo mount /dev/sda2
```

When I do that I get this:
```
ben@ben-laptop:~$ sudo mount /dev/sda2
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/disk/by-uuid/76A4C768A4C72A07': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
```

I cannot boot windows and "shutdown properly" and I have tried to mount it read only but that doesn't work either:
```
ben@ben-laptop:~$ sudo mount -o ro /dev/sda2
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/76A4C768A4C72A07 ()
```

When I try ntfsdix, I get:
```
ben@ben-laptop:~$ ntfsfix /dev/sda2
Mounting volume... Error opening partition device : Permission denied
Failed to startup volume : Permission denied
FAILED
Attempting to correct errors... Error opening partition device : Permission denied
FAILED
Failed to startup volume : Permission denied
Volume is corrupt. You should run chkdsk.
```

Once again, I am unable to run chkdsk because I cannot start Windows. I have tried to do it in safe mode, but I get the same blue screen,



I would like to mount the partition so that I can copy all the files that I need onto an external device and then format that horrible messed up partition.

---

### Post by southernman on 2007-09-03
First off, run this command "ntfsfix /dev/sda2" with sudo in front and see if it may help.

If not, download and burn a great tool called systemrescuecd. It has a program called testdisk on it that will allow you to retrieve the data from that drive.

I not long ago posted a really brief tutorial for someone that had a bad drive. If you'll search my post you should be able to find it really easily. It wasn't that long ago doing so... 3-4 days tops. I will see too, if I can find it again.

Good luck

---

### Post by southernman on 2007-09-03
[http://ubuntuforums.org/showpost.php?p=3281765&postcount=6]("http://ubuntuforums.org/showpost.php?p=3281765&postcount=6")

It's way more brief than I thought, but the program is easy enough to finger out.

---

### Post by bkkenny on 2007-09-03
Hey, that Live CD looks great!
I really hope this solves my problem, I've been very frustrated for a very long time, this will be such a relief!
I'm downloading the iso now, Ill edit here my results...

---

### Post by southernman on 2007-09-03
It is a nice tool to have on hand for a lot of uses. Just do a little reading on testdisk ( learnt it myself by just tinkering with it ), and don't get in a hurry. If your files are recoverable, you'll be able to get them without much effort.

If you haven't tried to write to the disk since the problem arose, and continue to not try writing to it... most of them should come out unharmed. DO NOT TRY WRITING TO THAT DISK! very important

When your ready to recover them, you'll need your make a directory for the external drive in SRCD from a terminal

> mkdir /mnt/youchoose
Then mount it (first find it by doing "fdisk -ls")
> mount /dev/sda1
Replace sda1 with what fdisk shows you as your external drive

Repeat the above steps for your NTFS drive.

Now you'll be ready to copy the files from your old ntfs drive.

If you run into trouble let me know. 

Remember, just take your time.

---

### Post by Sef on 2007-09-03
To pull files off your hard drive, try [Knoppix]("http://knoppix.net").

To repair the partition, get [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

---

