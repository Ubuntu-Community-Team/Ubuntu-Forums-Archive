---
title: "Removing Ubuntu?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Gimpster on 2007-04-19
I have xp installed on my main drive, and my super old second drive i have ubuntu installed on it.

now since the drive is so old and slow, i never use ubuntu and i would like to know the best way to remove it.  i unplugged the second drive altogether once and i got some kind of error.  the GRUB loader screen didn't come up and i couldn't choose to load win xp

i figured that would bypass anything that has to do with ubuntu, does it have something to do with the bios or maybe does it install system files on my main drive?

can i just format the spare drive or do i hafto go through some kind of uninstall process

thank you.

---

### Post by xpod on 2007-04-19
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

That should show you all you need to know.
It seem odd seeing a remove Ubu request amidst all these folks sitting installing at this moment in time:) 

Good luck

---

### Post by cypherzero on 2007-04-19
Do not format the drive - not yet anyway!

I installed Ubuntu to an external disk and after this my computer would no longer start without the disk - this is because GRUB looks for it's startup files on the external disk!

**What I did**
I reinstalled GRUB to a 7Mb EXT3 partition on my primary disk and (this time) told it to look for files on my primary disk so it could start Windows without the external disk.

[FONT="Courier New"]sudo grub-install --root-directory=/media/drive1-partition2-mount-point /dev/hda[/FONT]

**Alternatives**
If you have already formatted the drive you can use the Live CD to reinstall GRUB or use Windows to restore NTLDR (people say use fdisk, but I can't find a tool called fdisk on my computer). As a last resort use GRUB4DOS, I've heard many success stories but this trashed my MBR.

---

