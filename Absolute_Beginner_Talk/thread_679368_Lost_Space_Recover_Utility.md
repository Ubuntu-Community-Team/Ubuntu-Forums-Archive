---
title: "Lost Space Recover Utility????"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2008-01-26
I added a second user and by mistake deleted home folder for the first user.

As a consequence the available disk space is down to 30GB and should be 100 GB more.  What happens is that Ubuntu does not show the deleted home folder but it's accounting for its size.

I cannot restore the folder, so is there utility which would scan, consolidate/defrag the drive so the lost folder would be gone or I have to reinstall the system???

Thanx!!!

---

### Post by Rocket2DMn on 2008-01-26
Did you delete it from nautilus as root?  If so, the folder could still be in /root/.Trash
Otherwise, you cannot restore folder and there is no defragmentation on ext3 filesystems.  It seems like that folder is in the trash to me since space doesn't just disappear.  If /home is on a separate partition, you may want to check for something like /home/.Trash or /home/.Trash-root[/code]

---

### Post by seventhc on 2008-01-26
also make it to show hidden files.
'ctrl + h' or you can click on view, show hidden folders.

---

