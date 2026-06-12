---
title: "Deleting Read-Only Files from Trash"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by SavageFreedom on 2007-01-14
RESOLVED.
I used nautilus to find that the files I couldn't delete from Trash were actually not in the usual Trash directory, but a different one on my secondary hard drive. I was able to delete them there.


On my old Windows hard drive (while running Ubuntu from the other HD) I had a directory full of obsolete files that I wanted to delete, so I threw them all in the trash bin. The problem is, one of those folders was full of read-only files that would not delete. They say they are owned by "root" and that I cannot modify their permissions or delete them. I'm not sure what to do. I've read about changing a file's permissions, but I don't know how to do it while they're in the trash bin, nor do I know if it's actually a problem because they are windows read-only files and I'm wanting to delete them via linux.

---

### Post by taurus on 2007-01-14
If your Windows is ntfs, then forget about them because you can't delete them even if you are root.  However, you can install ntfs-3g if you want to write to your ntfs filesystem.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by jonny on 2007-01-14
If the files are on a filesystem that ubuntu can write to, the asiest way is to type ```
sudo nautilus
```
in a terminal.  That will give you a graphical file editor with root permissions so you can change permissions on the files (right click on them) and delete them.  But be careful.  Ubuntu doesn't give you a file browser with root permissions for a very good reason - it's dangerrous.  One misplaced press on the delete button and you can hose your entire system.

---

### Post by SavageFreedom on 2007-01-14
I suppose though Windows isn't still installed on that HD (it was a secondary in my old Windows machine) it is still ntfs. I don't think it's FAT32. If I'm unable to delete these files, is there a way to get them back out of trash? I'm not sure what the actual location of Trash is in the filesystem in order to try and do it from the terminal.

I don't mind having the files taking up space on hdb1, but if by putting them into Trash they were moved to hda1, I'd rather move them back.

---

### Post by taurus on 2007-01-14
Run this command from a terminal to find out for sure whether it's ntfs or vfat.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
If it's ntfs, then you need to follow this link to install ntfs-3g so you can write (and delete) to ntfs.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by SavageFreedom on 2007-01-14
Thanks everyone! With your help I figured it out. I used nautilus to browse /home/(user)/.Trash, and there was nothing there. I went to the folder representing hdb1 on my machine (/fat_files) and found another hidden folder, (.Trash-username). Therein were the files in question, and I was able to delete them there without a problem.

Thanks again.

---

### Post by monolegis on 2007-01-16
> **jonny said:**
> If the files are on a filesystem that ubuntu can write to, the asiest way is to type ```
sudo nautilus
```
in a terminal.  That will give you a graphical file editor with root permissions so you can change permissions on the files (right click on them) and delete them.  But be careful.  Ubuntu doesn't give you a file browser with root permissions for a very good reason - it's dangerrous.  One misplaced press on the delete button and you can hose your entire system.

Thank you, this helped me solve a similar problem on the server, after i switched from mandriva to ubuntu.

---

