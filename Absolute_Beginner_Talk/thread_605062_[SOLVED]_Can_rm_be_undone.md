---
title: "[SOLVED] Can rm be undone??"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Sozin on 2007-11-06
Hi all,

it seems i gave a program access to my desktop, which then proceeded to delete the desktop using an rm command. This was a link from helix media player to a real player download. When i ran it i saw my desktop get wiped. Looking through the history shows it "properly" deleted everything there. Worst of all, irreplaceable photos, files and data were lost.

Is there any way of getting any of it back?

Thanks for any help

---

### Post by skymera on 2007-11-06
check your .trash and roots .trash

---

### Post by aysiu on 2007-11-06
First of all, stop using your computer as soon as possible.

Reboot and use a live CD instead. You may be able to recover your deleted files:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by bodhi.zazen on 2007-11-06
As aysiu indicated , STOP using your ubuntu installation or you may easily overwrite your files.

See if this link helps [https://answers.launchpad.net/ubuntu/+question/2178](https://answers.launchpad.net/ubuntu/+question/2178)

---

### Post by Sozin on 2007-11-06
> **skymera said:**
> check your .trash and roots .trash

there is nothing in  /root/.trash

---

### Post by aysiu on 2007-11-06
> **Sozin said:**
> there is nothing in  /root/.trash
Nor should there be. *rm* removes the file completely. It doesn't move it to the trash.

Are you still using Ubuntu? Stop now and reboot with the live CD and try to recover your files. See the link I posted earlier.

---

### Post by Sozin on 2007-11-06
im not still using ubuntu, however it was used to backup all the rest of my files before we tried anything

most of these tools seem to be for corrupted disks, not for recovering deleted files

are there any tools specifically for rm deleted files on an ext3 file system?

---

