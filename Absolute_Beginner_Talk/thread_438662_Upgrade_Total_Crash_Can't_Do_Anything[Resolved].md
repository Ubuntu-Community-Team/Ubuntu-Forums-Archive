---
title: "Upgrade Total Crash Can't Do Anything[Resolved]"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by yakyakyak on 2007-05-09
Ubuntu 6.0 was running just fine on my x86 box, so I chose the "Upgrade" option and now I get a black screen of death on bootup.  So I burned the Ubuntu 7.0 iso disk and tried to install... and ge the same black screen of death.  Here is the error message and I have utterly no idea what to do:

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built in commanmds.  

(I tried this but I don't understand any of the commands or what to do with them)  THEN it goes on to say:

/bin/sh: can't access tty; job control turned off
(initramfs) [ 147.561554] ata2.01: failed to set xfermode (err_mask=0x4)
[ 183.353422]  ata2.01: failed to set xfermode (err_mask=0x4)
[ 219.141313]  ata2.01: failed to set xfermode (err_mask=0x4)
[ 224.140264]  ata2.01: failed to set xfermode (err_mask=0x40)

WHAT DOES THIS MEAN?????  What do I do now?

Thanks!

---

### Post by yakyakyak on 2007-05-10
So I am posting back to myself.  Turns out I was able to reinstall Feisty Fawn via my 2nd cd unit... for some reason my usual main cd wasn't functioning.  The reinstall went find once I tried the other cd player... I just checked for and installed software and system updates and Feisty Fawn is running!!!!!  I'm so excited.

---

### Post by Sef on 2007-05-10
Great.  Glad to hear you got Feisty Fawn installed.   Please post any more questions that you have.

---

### Post by catdriver on 2007-05-13
I just got the same error, on reboot things start normally, then the screen blanks for 5-10 minutes, then drops to the shell as described.   In recovery mode, there is a message that states /dev/disk/uidxxxxxx long string of numbers.... is not found.   It then drops to the shell, and when issued an ls -al the dirctory structuer is not what one expects, there is no home, and in the /dev location is a huge list of tty0x's and such as well as an entry that says snapshot.

I have no problem goning back to a 5.10 or downloading and burning a 7.xx disk as long as I can reinstall *without* a reformat, which my 5.1- install media insists in performing.... I *do not* want to lose my MP3 collection simply due to a blown upgrade.... I know backups...... not terrible feasable with out a functioning player (another story) or a ****load of CD's  I have resorted to a 5.10 live disk for the time being.....

---

### Post by catdriver on 2007-05-13
bump..???
Oh never mind this is addressed in any of a handful of thereads that don't mention it by name...

---

