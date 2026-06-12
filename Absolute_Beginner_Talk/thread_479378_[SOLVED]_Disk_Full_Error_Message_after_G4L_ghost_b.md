---
title: "[SOLVED] Disk Full Error Message after G4L ghost backup"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by razeshkale on 2007-06-20
I was trying to get backup of Ubuntu for safety reason and I think I messed my Ubuntu.?
I did BIG mistake i stored backup copy on same disk on Ubuntu.

Now Ubuntu has run out of Space and I could not get into Ubuntu machine.
I booted with Ubuntu CD and Mounted the partition (My old Ubuntu ) but Now I have permission problems. so i can delete that backup file and Ubuntu can start normal again.

Any idea how to change Ownership in Ubuntu with Ubuntu Live CD.
I m attaching screen shot and i want to delete this Backup file highlighted in Screen shot?

Help out!!!!

---

### Post by Skrynesaver on 2007-06-20
When you have it mounted on the live CD hit [ALT]+[F2] together then type
```
gksudo nautalis
```
This will give you the same approach but with root permisions

---

### Post by razeshkale on 2007-06-20
i got read and write excess on properties,but still i cant delete any file as it gives following error!!

How can i gain access of Root on this mounted partition?
so i can delete some files from my original Ubuntu system
Screen shot

---

### Post by razeshkale on 2007-06-20
I did sudo chown username:users folder gain Read Write access on same folder/mounted disk

Still i cant delete that Linux folder?
please have look at Screen shot

---

### Post by razeshkale on 2007-06-21
Issue has been resolved!!!

Mounted image 
and 
on terminal with live cd i put
sudo rm /media/ubunturoot/file name 

so that delete my unwanted backup files and now i m back with my Sweet Ubuntu 
Gr8
Cheers

---

