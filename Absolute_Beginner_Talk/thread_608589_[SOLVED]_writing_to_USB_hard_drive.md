---
title: "[SOLVED] writing to USB hard drive"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by lee292 on 2007-11-10
I have a 250 GB USB hard drive I'm trying to back up my Ubuntu 6.10 system to.  I was able to create the TAR file OK, but when I try to copy it to the USB drive I get a "You do not have permission to write to thsi folder" message.  The drive was formatted as NTFS and I loaded ntfs3g but I still couldn't write to it.  I've also repartitioned the drive into one NTFS partition for my Windows stuff and an etc partition for my Ubuntu backups with no success.   I used the Gnome partition editor to create the etc partition, and when I look at the permissions, it says the owner is "root"  What do I need to do to write to this drive?

---

### Post by Nikitas350 on 2007-11-10
Type "gksu nautilus" in your terminal. This will open the nautilus with root permissions. Go to the usb hard drive and paste what you want.... :)

---

### Post by Harpoon on 2007-11-10
The drive is mounted, so take note of the mount point  

then you can enter the following in a terminal

sudo chown -R username:username /media/diskname <return>

That should give you ownership of the disk and all files on it.

---

### Post by lee292 on 2007-11-10
IT WORKS! IT WORKS!  IT WORKS!!!!  :D Thanks, Nikitas and Harpoon for your help!

---

