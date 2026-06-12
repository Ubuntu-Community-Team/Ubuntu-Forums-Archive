---
title: "installing new grub theme"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2006-07-23
im trying to install this theme [http://www.gnome-look.org/content/show.php?content=25568](http://www.gnome-look.org/content/show.php?content=25568) and its a rather simple task. but when i try to copy the 36907-blu.xpm.gz file to /boot/grub i get a pop up stateing "You do not have permissions to write to this folder." is there a way to solve/ work around this problem?

---

### Post by Jagot on 2006-07-23
By default you can only mess around with you /home directory.

Hit alt+f2 and type:

```
gksudo nautilus
```

This will open the file manager in root mode so you can copy and paste freely between directories.

---

### Post by ciscosurfer on 2006-07-23
You can either temporarily or permanently change ownership or permissions of the folder.  One option would be```
sudo chown YOUR_USER_NAME /boot/grub
```then change it back to its original owner (root) when you are done copying over the file.

EDIT: Of course Jagots suggetion will also work just fine!

---

### Post by bruenig on 2006-07-23
or you could use
```
sudo mv /path/to/36907-blu.xpm.gz /boot/grub
```
replacing path to with the path to the theme
enter your password and done.

---

