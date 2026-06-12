---
title: "Installing Remaining packages failed"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by Aurdal on 2006-06-29
So, I tried to install Ubuntu today after having formatted my drive. Only to get an error message in the middle of the process.

When the installer had finished installing the base syste, and had just started to install the remaining packages, I got a message along the lines of:

"Installing remaining packages failed, this migth be because the targer /var filesystem is full." It also listed a faulty CD as a possible reason. 

So, does anyone have any idea on how to fix this, I don't think it's the faulty CD thingy, because I've encountered this before, with other disks. I do not remember what I did to get around it though.

Thank you.
-Aurdal

---

### Post by ifican on 2006-06-29
It sounds like the partition that was created is not big enough and is now full. I dont know how to check that off the top of my head but i would search along those lines.

---

### Post by Aurdal on 2006-06-29
Thanks for your reply, but 30GB shouldn't be too little... Anyway, here's the full error message:

"Copying packages to the hard disk failed. You may have run out of disk space "
"in the target /var filesystem, or your CD drive may be having problems "
"reading packages from the CD. Cleaning the CD drive or burning the CD at a "
"lower speed may help."


EDIT: I set up my partition table diffrently, and voaila... :)

---

### Post by az on 2006-06-29
[QUOTE=Aurdal]

EDIT: I set up my partition table diffrently, and voaila... :)[/QUOTE]
So it's working?  Check for bad blocks on all your partitions.

example:
sudo badblocks /dev/hda1

---

