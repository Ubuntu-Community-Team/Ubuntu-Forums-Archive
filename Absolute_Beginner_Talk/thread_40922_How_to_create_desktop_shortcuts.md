---
title: "How to create desktop shortcuts?"
date: 2005-06-11
forum: Absolute Beginner Talk
---

### Post by aysiu on 2005-06-11
In Windows, you can right-click on something and say "send to desktop as shortcut." In Mac, you can create an alias and drag it to the desktop. In KDE, you drag the item to the desktop and click "link here."

How do you in Gnome/Ubuntu get a desktop shortcut for a file/folder?

---

### Post by diomedesxx on 2005-06-11
One way would be to right-click, choose "Make Link" and move the newly created file to your desktop.

---

### Post by aysiu on 2005-06-11
Sounds like a good idea. For some reason, my "make link" option is greyed out when I right-click on folders.

---

### Post by Kapre on 2005-06-11
Try dragging the application to the desktop (works for me).

---

### Post by aysiu on 2005-06-12
Really? When I drag the item to the desktop, Ubuntu tries to copy it to the desktop.

Turns out the problem with "make link" is that the folder/file has to be in my user's home folder. Even when I tried changing permissions to chmod 775, the user was unable to "make link" for folders outside of its home directory.

I also found out that I can't "make link" any files that reside within a FAT32 partition. The partition itself (mounted as a folder in Ubuntu in the user's home folder) can have a link made, but files within the FAT32 partition can't have links made for them.

---

### Post by zaxer on 2005-06-12
[QUOTE=aysiu]Really? When I drag the item to the desktop, Ubuntu tries to copy it to the desktop.

Turns out the problem with "make link" is that the folder/file has to be in my user's home folder. Even when I tried changing permissions to chmod 775, the user was unable to "make link" for folders outside of its home directory.

I also found out that I can't "make link" any files that reside within a FAT32 partition. The partition itself (mounted as a folder in Ubuntu in the user's home folder) can have a link made, but files within the FAT32 partition can't have links made for them.[/QUOTE]
 I have this problem too.

---

### Post by intangible on 2005-06-18
Have you tried dragging the file to your desktop with the middle mouse button?  It'll then give you options instead of just doing the default action.

Also, have you tried it from the command line?

**ln -s /mnt/windows/filetolink ~/Desktop/Shortcut**

You should be able to make links to the files on the Fat32 partition as well as make links outside of the user's home.

---

### Post by doclivingston on 2005-06-18
[QUOTE=aysiu]I also found out that I can't "make link" any files that reside within a FAT32 partition. The partition itself (mounted as a folder in Ubuntu in the user's home folder) can have a link made, but files within the FAT32 partition can't have links made for them.[/QUOTE]
Fat32 doesn't support symbolic links. This means that you can't create a link _on_ the  fat32 partition, but you should be able to make link to files that are on the partition. Right-click -> Make Link won't work, because it will try to create the link in the same directory as the original, on the fat32 partition.

If you middle-button-drag an icon, it will pop up a menu with copy, move and link. So if you middle-button-drag the icon to your desktop, you should be able to make links to files that are on fat32 partitions.

---

### Post by aysiu on 2005-06-18
What a neat trick! You've totally made my day. Thanks.

---

### Post by Ampi on 2008-03-31
Thanks, you made my day too!

---

### Post by aeiah on 2008-03-31
> **Ampi said:**
> Thanks, you made my day too!

the difference being that it made his day back in 2005 ;)

---

### Post by rajarshi on 2008-05-06
You could just create an application launcher and direct it to 'nautilus /home/usrname'!

---

