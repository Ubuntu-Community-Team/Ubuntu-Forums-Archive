---
title: "Unmounting windows from Ubuntu"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by phil66 on 2006-05-14
I mounted window with the intention of using wine to open a windows app.In the mean time I found an app that would be suitable for Ubuntu and would replace the windows app.

When I right click and click unmount windows on the windows icon and error message appears as follows:
Unmount: only root can unmount /dev/hda1 from /media/windows

Went to terminal and typed "sudo umount /media/windows"
This removed windows until the next time I boot up then it reappears.

Is the right script"sudo /dev/hda1/media/windows"
The reason I ask is that I do not want to erase my windows ME operating system

Thanks
Ray

---

### Post by oscar on 2006-05-14
to make it not automatically mount each time you reboot you need to remove the line that refers to your windows partition from your /etc/fstab file:
```
gksudo gedit /etc/fstab
```
look for a line like (it will not be exactly the same):
```
/dev/hda1                /media/windows     ntfs-fuse   auto,gid=1001,umask=0002   0       0
```
and add a # before it so that it looks like this:
```
#/dev/hda1                /media/windows     ntfs-fuse   auto,gid=1001,umask=0002   0       0
```
this will make ubuntu ignore the line, if you change your mind later just remove the #. When you reboot your windows partition will not be mounted

---

### Post by aysiu on 2006-05-14
Paste these commands into a terminal: ```
sudo umount /dev/hda1
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Delete the line that refers to /dev/hda1. Save (control-x), confirm (y), and exit (Enter).

---

### Post by phil66 on 2006-05-14
Thanks for the help

Followed the code as per your instructions and all windows in ubuntu were removed
I only have an empty windows directory in media left
I can handle that

This forum and its member are the best help around

Thanks again and I'm sure I will be back asking for help again
Ray

---

### Post by cgjones on 2006-05-14
If you will no longer need to mount the Windows partiton in Ubuntu, you can safely remove the windows directory in /media. Thats just the location where Ubuntu mounted the Windows partition. As long as the Windows partition isn't mounted, /media/windows is just an empty directory.

---

