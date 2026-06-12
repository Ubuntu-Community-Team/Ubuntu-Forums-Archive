---
title: "Edgy wont boot anymore PowerbookG4"
date: 2007-03-15
forum: Apple PPC Users
---

### Post by ranxoren on 2007-03-15
Hi, i have a question for you guys.
First of all i would like to thank everybody again for last time i had a problem i got answers on how to fix it within an hour.
Now i have another problem. I have been running Edgy on my PB G4 for about 3 weeks now and it suddenly stopped working.
It boots everything all the way like it used to do but stops at a black screen with this on it :

[B]( 39.893274) JBD: Failed to read block at offset 4941
( 39.893438 ) EXT3-fs: error loading journal

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control turned off
(initramfs)[/B]

I have NO CLUE what to do as it won't even boot from CD anymore. I dont mind AT ALL having to reformat and reinstall as i dont have anything important on it for now.

Thanks to everybody that reads this and hopefully somebody will be able to help.

THANKS guys.

O.T.

---

### Post by grazie on 2007-03-15
Looks like you've had a file system corruption which has possibly been caused by a disk failure. Run fsck after you get to

[B]BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands
[/B]
However, this shouldn't stop you from using the live cd in any way. Maybe the cd needs a bit of clean? I'm assuming you still get the l, x, c menu and selecting c no longer works. Correct? Try entering check at the boot: prompt. If the check fails after you've cleaned the cd, you'll have to burn yourself another live cd.

If fsck doesn't auto fix the problem, you'll need to boot with the live cd, mount the HD and look at some log files, firstly /var/log/dmesg.

---

### Post by ranxoren on 2007-04-01
Sorry for the loooooong time that it took me to answer i didnt have my computer anymore so not really access to internet as i get my emails on my blackberry.

Thanks a lot for answering.

O.T.

---

