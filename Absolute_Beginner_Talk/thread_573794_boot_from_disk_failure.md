---
title: "boot from disk failure"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Just Some Person on 2007-10-12
I recently got an old pc to try out ubuntu. its specifications are:

400MHZ intel celeron
468M ram
toshiba 13.7GB hard disk

This managed to run ubuntu 6.10 with no problems, though when I tried to use 7.04, it was somewhat more problematic:

The install appeared to work fine, however when I try to boot it from the hard disk the loading bar freezes at about five percent; then after a while the loading screen disappears and i get this message:

 *Reading files needed to boot...
[469.073555] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[469.073696] ata1.00: cmd c8/00:00:0a:c6:e9/00:00:00:00/e0 tag 0 cdb 0x0 da
ta (either 13072 or 90112)in

it then repeats that message about a dozen times before the screen goes black and nothing happens (though the HDD light is on)

It boots fine from the disk.

Please help!!!

---

### Post by Bliepo32 on 2007-10-12
You could try recovery mode. You could also try using a live-cd to fix it. If these don't work, try to re-install. And by the way, it would be a good idea of you would make back-ups next time. Read [Howto: Backup and restore your system!]("http://ubuntuforums.org/showthread.php?t=35087") for more information on how to do this.

---

### Post by Just Some Person on 2007-10-12
recovery mode didn't work. it just kept running through scripts with that error code every so often.

what do you mean, 'use a live-cd to fix it'?

---

### Post by Just Some Person on 2007-10-12
about making backups; there was nothing on the computer i wanted, so thats fine

---

### Post by Just Some Person on 2007-10-12
I have reposted the guts of this question under the heading "Failure to boot from hard disk after installing 7.04", being a better heading for the problem - so please look to that heading to pick up the thread,

Cheers

---

