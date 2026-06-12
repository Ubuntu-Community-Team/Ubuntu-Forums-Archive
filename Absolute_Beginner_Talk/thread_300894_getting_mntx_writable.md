---
title: "getting /mnt/x writable"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by leetrefz on 2006-11-16
It says I can't write to /mnt/x. I think if, in kde when I right click the icon & go to properties & permissions and could switch to root, I could probably solve this. Maybe someway under system settings, disk & file systems too. 

I think this has something to do with why I can't listen to music off there, though can't saving a note either. 

Thank you!

---

### Post by dillbertdabomb on 2006-11-16
I don't quite recommended it, for you (kubuntu)
it would be 
kdesu konquerer (or however you spell that) 

find your folder and right click, look for permissions, and give the others and user group write permissions, you could open a file itself writable

kdesu kate File_name_here

but be careful! make backups if you change anyhting big!

---

### Post by taurus on 2006-11-16
It depends on how you mount /mnt/x!  If it's ext3, then you can change permissions with chmod.  But if it's vfat or NTFS, then you need to mount it with the right permissions either from a terminal or through /etc/fstab.

---

### Post by leetrefz on 2006-11-16
So as it's unfortunately ntfs, I shoud unmount and remount it with care to the permissions? 

thanks to alcohol i forget how I got it mounted in the first place, but that fstab thing rings a hazy bell. it was only 2 days ago.

Is it because it's ntfs that I can't edit those permissions settings from the desktop?

---

### Post by tuxcantfly on 2006-11-16
you need ntfs-3g to write to ntfs: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

