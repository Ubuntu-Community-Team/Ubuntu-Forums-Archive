---
title: "Problem with Execute Permissions?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Theo21 on 2006-07-10
I'm fairly new to Linux and Ubuntu, and I recently set up Ubuntu on the second partition of my Windows system. I've been trying to edit my xorg.conf file but I haven't been able to save a backup file or an edited file to the X11 directory. When I attempt to save the files to /etc/X11 I get an error: "could not save the file /etc/X11/xorg_backup.conf" and "You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again. I can save these files to the desktop, but not to this folder. I was also unable to drag and drop them in the folder from the desktop.

I checked my user privileges and I have all possible privileges selected.

When I looked at the xorg.conf properties under the permissions tab the read, write, and execute options were grayed out, and at the bottom of the window it said: "you are not the owner, so you can not change these permissions."

I was wondering if there was a way to change these settings, if anyone can help me out I'd really appreciate it.

Thanks

---

### Post by digby on 2006-07-11
Since xorg.conf is a system-wide configuration file, it is owned by root (the administrative user).  That means that you can only edit that file if you are root.  To run commands as root, you will preface the command with 'sudo.'  For example, to edit your xorg.conf,```
sudo gedit /etc/X11/xorg.conf
```You can substitute any editor you like for gedit, it's just simple to use.

---

