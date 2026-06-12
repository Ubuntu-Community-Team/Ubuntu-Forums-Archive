---
title: "renaming a mounted drive"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by GaijinOnline on 2006-07-10
hi, I would like to know if there is a way to rename a mounted drive. I have my windows drive that is mounted to my desktop and it is named "hda1", I would like it to be named "Windows". And will you guys are there can you tell me how I can remove an icon in my menu "applications>internet", I try to right click by I can't see any option to remove/erase it.

thank you!

---

### Post by aysiu on 2006-07-10
You probably mounted the drive to /media/hda1, and that's why it's showing up as *hda1*.

If you want it to be named Windows... ```
sudo umount /dev/hda1
sudo mkdir /media/windows
sudo rm -rf /media/hda1
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Change the line for /dev/hda1 so that it mounts to /media/windows instead of /media/hda1. Then save (Control-X, Y, Enter) and ```
sudo mount -a
```

---

### Post by GaijinOnline on 2006-07-10
is there by any chance a way to do that via a GUI?

---

### Post by aysiu on 2006-07-10
Yes.
Are you in Gnome or KDE?

---

### Post by GaijinOnline on 2006-07-10
I am using Gnome.

---

### Post by aysiu on 2006-07-10
> **GaijinOnline said:**
> I am using Gnome.
Press Alt-F2 and type ```
gksudo nautilus
``` This will temporarily allow you to browse as root.

In the new Windows, browse to the /media folder. Right-click and unmount the drive. Delete the *hda1* directory and create a new directory called *windows*.

Then go to the /etc directory and copy and paste the *fstab* file and call the backup copy *fstab_backup*. Edit the *fstab* file and change */media/hda1* to */media/windows*.

Then go to Places > Computer and right-click and mount your drive.

Close the "browse as root" Nautilus window.

---

### Post by Frank Golden on 2006-07-10
> **GaijinOnline said:**
> is there by any chance a way to do that via a GUI?
Awhile ago I would have sought a GUI method to do something
like this. Today I would just use the terminal. I guess I am
getting more comfortable with the command line.
I do "cheat" though. I made a panel shortcut to "gksudo nautilus". On my setup whatever my XP NTFS or Fat 32 partitions were named in Windows was what they were named when automounted
in Ubuntu.

---

### Post by GaijinOnline on 2006-07-10
> **Frank Golden said:**
> Awhile ago I would have sought a GUI method to do something
like this. Today I would just use the terminal. I guess I am
getting more comfortable with the command line.

Well the command line doesn't scare me it's just that it is good to know both way to do it. If I have to help someone in the future who have this problem and want a GUI alternative to a terminal one I have it now.

@aysiu: thanks a bunch for your help!

Now is there any way to remove an icon in my "application > Internet" drop down menu?

---

### Post by aysiu on 2006-07-10
Right-click on the Applications menu and select **Edit Menu**. Uncheck the box for the icon under the Internet submenu.

---

### Post by GaijinOnline on 2006-07-10
thanks a lot for the help, it all worked! :D

---

