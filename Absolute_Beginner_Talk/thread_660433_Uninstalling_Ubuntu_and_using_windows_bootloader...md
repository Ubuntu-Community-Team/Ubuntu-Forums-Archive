---
title: "Uninstalling Ubuntu and using windows bootloader.."
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by VigCS on 2008-01-06
Hi all.  I've just sold my laptop and I told the buyer I'd put a fresh install of Windows on it for her, so it's bye bye to Ubuntu on the laptop.  It's a dell inspiron 9300 and has the hidden "Dell Restore" partition (which is still there) which contains an image of XP pro.  Anyway, I have the hard drive partitioned to 50gigs for windows, 20 gigs for Ubuntu, and a 5 gig FAT32 shared drive.  My question is:

How do I get windows bootloader back so I can run the DellRestore partition and make this thing factory fresh again?  It wouldn't be such a big deal but I can't find my dell restore CDs.

Can I just use fixmbr to get the windows boot loader back and boot into the DellRestore partition that way?  How do I get into the command line to enter fixmbr?  Thanks for any help!

---

### Post by Blutack on 2008-01-06
Might want to write this down, looks more complicated than it is.  If you need more help let me know.

Using a terminal in ubuntu type fdisk -l to find the partition of the dell thingy.  So for example, /dev/sda1.
Take one away from the number on the end to get your grub partition number (1 - 1 = 0)

Boot laptop to grub
Press escape to get grub menu
Press C to obtain grub command line
Type root (hd0,0) [where the second 0 is the number of the partition you want to boot, /dev/sda3 would be (hd0,2)]
Type chainloader +1
Type boot

I used that trick a few times, the dell restore thing is just mocked up on top of Win98.

---

### Post by VigCS on 2008-01-06
Thanks for the reply.  Unfortunately I just did fixmbr and it got rid of grub, so it boots directly into windows now.  However, the screen that needs to flash to boot into the Restore partition no longer flashes like it did before I installed grub/ubuntu.

So...with your trick...looks like I'll need to figure out how to get into Ubuntu again.  Will I need to reinstall Grub?  Could I do this using a USB flash drive?  Thanks!  I have a feeling my impatience made this harder than it should be.

---

### Post by Blutack on 2008-01-06
Your best bet is probably just to reinstall ubuntu then follow my instructions.  I know it seems a pain but pop it in the same partition you used to use for it, it's the safest way to go.

---

### Post by VigCS on 2008-01-06
Okay, thanks for the help.

---

### Post by eternicode on 2008-01-06
[Inside the Dell Restore Partition]("http://www.goodells.net/dellrestore/")

From the same author: [DSR fixes]("http://www.goodells.net/dellrestore/fixes.htm")

> **Blutack said:**
> Might want to write this down...

Unfortunately, this doesn't fix it so that the new user can use Dell's Ctrl+F11 pre-boot sequence to restore it themselves later.

> **VigCS said:**
> Unfortunately I just did fixmbr and it got rid of grub, so it boots directly into windows now.  However, the screen that needs to flash to boot into the Restore partition no longer flashes like it did before I installed grub/ubuntu.

That screen that flashes before booting is part of "Dell's custom boot code" ;)

---

### Post by VigCS on 2008-01-06
> **eternicode said:**
> [Inside the Dell Restore Partition]("http://www.goodells.net/dellrestore/")

From the same author: [DSR fixes]("http://www.goodells.net/dellrestore/fixes.htm")



Unfortunately, this doesn't fix it so that the new user can use Dell's Ctrl+F11 pre-boot sequence to restore it themselves later.



That screen that flashes before booting is part of "Dell's custom boot code" ;)

Do you know how I'd be able to get it such that the buyer would be able to restore using ctrl + F11 in the future?  Thanks.

EDIT:  Hold on a response...reading through the troubleshooting link you provided :).

EDIT2:  Okay, I think I'm going to do what Blu said and then run DSR fix after that's up and running.  Thanks again guys.

---

### Post by VigCS on 2008-01-06
I've got two problems now...running fdisk -l in terminal just enters as a command and doesn't display anything.  But, I'm almost 100% sure my dellrestore is /dev/sda3.

So in the grub command line I did root (hd0,2), chainloader +1, and typed boot, it said "starting..." very briefly and went right back to the grub command prompt.  I know this works because I successfully loaded into windows this way.  Any ideas?  Thanks guys.

---

### Post by eternicode on 2008-01-06
Depending on the system (Ubuntu LiveCD?  SysRescCD?) "fdisk -l" as a normal user may not give you info about the hard drive.  Did you try "sudo fdisk -l"?

---

### Post by VigCS on 2008-01-06
That worked, thanks.  This is what it reported

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        6085    48829567+   7  HPFS/NTFS
/dev/sda3            9218        9729     4112640   db  CP/M / CTOS / ...
/dev/sda4            6086        9217    25157790    5  Extended
/dev/sda5            6086        6207      979902   82  Linux swap / Solaris
/dev/sda6            6208        9217    24177793+  83  Linux

When I right click the DellRestore drive on my (linux) desktop it says the mountpoint is /media/sda3.  And from the list above I'm guessing, by processes of elimination, that /dev/sda3 is the DellRestore partition.  If so, what I did above in the grub command lines didn't work, unfortunately.  I did

root (hd0,2)  //(3-1 = 2)
chainloader +1
boot

And it briefly flashed "Starting up..." and went right back to a fresh page of grub command lines.  What would you guys suggest I do?  Will DellRestore recognize and wipe out an ext3 extension anyway?  Thanks!

---

