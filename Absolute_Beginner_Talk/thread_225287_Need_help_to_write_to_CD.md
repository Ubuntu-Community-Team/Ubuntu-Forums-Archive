---
title: "Need help to write to CD"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-07-29
Hi
I want to copy some date files to external media (floppy or CD). However, I'm having difficulty mounting either one.

To mount the CD RW drive, I entered the following in Terminal:
sudo mount /media/cdrom1/ -o unhide

and got the following somewhat bleak message:
mount: block device /dev/hdd is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Note that I can play music CDs without problem from this drive in Ubuntu.

Anybody know what's wrong?

Thanks
Paul

---

### Post by Koookie monster on 2006-07-29
Try "mount -t auto" (so use the command you used, but add the -t auto) or -t iso9660 and see if it helps. "-t" states mount which file system to use. More help: man mount.

[edit: see reply below] :)

---

### Post by Fass on 2006-07-29
You don't need to mount CDs to burn them, and I don't think you can mount just empty CDs at all, really. Just put the CD in and use your burning app (such as gnomebaker).

---

### Post by PaulFXH on 2006-07-29
Thanks guys for the replies.
OK, so I tried to burn without mounting.
Installed Gnomebaker and used it to copy a small html file to the CD RW drive.
Everything seemed to be going fine in that the correct lights came on and the appropriate progress bars were activated.
However, I cannot now verify if there is anything actually on the CD. 
When the CD was blank, it appeared in the LHS panel of the Text Editor Open box as Blank-CD.
However, now that there is, supposedly something on it, nothing of relevance appears in the same panel.
So, I rebooted and went into WinXP. However, Windows couldn't see anything on this disk.

What's up?

Thanks
Paul

---

### Post by PaulFXH on 2006-07-29
Hi
OK, I've resolved yet another mystery of Ubuntu. The reason nothoing burned onto my CD was that I had forgotten to press the Create Data CD button.

Paul

---

