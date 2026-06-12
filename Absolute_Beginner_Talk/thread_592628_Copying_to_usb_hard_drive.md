---
title: "Copying to usb hard drive"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-10-26
I am trying to copy music & photos from my hard drive to my spare hard drive which is attached via usb. I get this message "You do not have permissions to write to this folder.". The folder on the spare drive is root, how do I enable this operation?

---

### Post by Dr Small on 2007-10-26
Is the said USB Hard drive formated to NTFS ?

---

### Post by Benbow on 2007-10-26
Yes it is.

---

### Post by Nachtengel on 2007-10-26
Try this command:

sudo chown <destination directory name on USB drive here>  *username*

This will change the user that owns the folder on the USB drive to your user, and allow you write access to the folder

---

