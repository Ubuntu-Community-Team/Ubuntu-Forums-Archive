---
title: "Live CD Demo Dies"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by Kerry Lange on 2006-06-03
Hi there:

I've not been able to get the Dapper Live CD to run.  The install gets as far as expanding the Linux Kernel then I get the blinking cursor at the bottom of the screen and the help menu at the top.  I can type stuff in using the cursor but nothing happens and pressing various "F" keys (per the help menu) simply inserts the appropriate value in at the prompt.  Pressing enter does nothing.

I've got an AMD 3800X2 with 2GB of RAM, plenty of disk space running on a Gigabyte G8 SLI motherboard.  Two of the HDDs are used in a SIL RAID.  The system has two Nvidia 6800 graphics cards and I've got onboard sound disabled because I have an M-Audio firewire unit for sound instead.

Does anyone have suggestions on what to do to get the Live CD to run?

---

### Post by bobpur on 2006-06-03
I had a similar problem with my install cd. I had to go back and reburn it. I had an error message that started out: "loading isolinux..." I took the "iso" part to mean I had burned the iso image to a disc and trying to boot with that.
To be honest, I'm not sure of the steps I used to fix the problem. Between Nero 6 ultra and the ISOrecorder I came up with a working disk. I do have a set of matching coasters to show for my efforts:)

                                Good Luck

---

### Post by Kerry Lange on 2006-06-03
I *don't think* the disk burn is the problem, as the install prior to that goes okay.  I'm presented with some of the graphical components and am told the disk is being mounted (I assume that's a virtual disk of some kind).  It's shortly after I'm told the disk is being mounted that I get the cursor and the help menu from the beginning of the install.

---

### Post by darckhart on 2006-06-03
just curious, but have you tried installing it to just a regular single hard drive (e.g. not part of any raid arrays)?

---

### Post by Kerry Lange on 2006-06-03
No, I haven't tried installing it to any of the drives.  My understanding of the Live CD is that it doesn't really install to the drives, except perhaps to a virtual drive created on one of the partitions.

Does the Live CD require that I have a FAT or FAT32 partition somewhere in order to run?  Currently I have only NTFS partitions.

---

### Post by painterboy on 2006-06-03
I ran my burnt live cd from windows which used NTFS and i had no problems so as far as I know from personal experience that shouldnt be a problem.

---

### Post by darckhart on 2006-06-03
oh whoops i misread your 'couldnt get it to run' as 'couldn't get it to install'

the livecd was able to run fine for me, and yes, i have winxp on a ntfs formatted single drive. to troubleshoot your problem, here's what i would do:

firstly, have you verified (via md5) that 1) the iso you downloaded is not corrupted, and 2) the iso you burned to cd is not corrupted?

secondly, is your boot order cdrom, floppy, hdd, raid?

thirdly, disconnect your current drives and raid array (to eliminate drivers and timing issues), and try to boot from livecd? (unless your mobo auto loads its raid drivers at the very beginning, in which case this probly wont help.)

---

