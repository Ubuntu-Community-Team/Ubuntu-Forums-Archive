---
title: "booter [not grub...]"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by Heretic on 2006-06-20
Here is my situation: GRUB kinda screwed me over, and I used a backup floppy to restore the MBR on my primary drive.

-Primary Hard Drive [80gb] :: WINDOWS
-USB laCie hard drive [250gb] :: Ubuntu

I have several backups that can restore the mbr, so im willing to try booters. Anything but grub.

I want a booter so that when my computer boots up, past the memory check, and after checking A:\ & D:\ to list my operating systems on both hard drives [one internal, one external]

Is this possible?

---

### Post by underdog on 2006-06-20
LILO is another bootloader. I don't know if it does what you want, but its something to look up.

---

### Post by rowanparker on 2006-06-21
Are you sure it was Grub that messed your MBR up and not you? (No offence, it does happen though.)
How did it "screw you over" exactly?

Rowan.

---

### Post by bscbrit on 2006-06-21
The drives A:\ and D:\ are Windows names - they only exist once windows has started running.  At this stage it is too late to switch to Ubuntu.  A:\ is a floppy - not a hard drive.  If you have 2 hard drives under windows they would be C:\ and something else, possibly D:\ or E:\.

 If you tried to do the same in Linux, you would see drives hda and hdb except it would only see the external drive once linux had booted - by which time it would be too late to select Windows without rebooting again.

Either grub or lilo will boot into either operating system but neither will see an external drive as far as I know.  Perhaps someone out there will correct me, but it is not something that I have ever seen before.  If you want to dual-boot, both OS will have to reside on a hard drive partition to be selectable at boot time.

---

