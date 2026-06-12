---
title: "Grub Help"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by HolyPhoenix on 2007-03-22
I installed ubuntu succesfully on an external hdd.  I had a few problems and almost bricked up my computer, but I got lucky and finally got it working.  I love it though and I believe it was worth the effort to put on my external hdd.  My problem that I am running into now, is that I am trying to hide grub that was installed.  I installed it on the one with windows, so now when I try to edit it with terminal in ubuntu it says I do not have permission.  I was wondering if I could get the location of it where it would be in windows so I can go edit it there, or give permission to edit it to ubuntu.  Thks!

---

### Post by sad_iq on 2007-03-22
Try this: **sudo gedit /boot/grub/menu.lst** ...however make a backup before you edit it: **sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup**

---

### Post by igknighted on 2007-03-22
Grub is partially installed on the MBR of the windows drive, not really in the windows partition.  The config files for grub, however, are on your linux drive in the /boot/grub folder.  Use the commands listed above to edit them.

---

### Post by HolyPhoenix on 2007-03-22
When I try that it asks for a password.  I tried the password of my account, and then the password I put in to do administrative things.  Neither worked.

---

### Post by louieb on 2007-03-22
> **HolyPhoenix said:**
> When I try that it asks for a password.  I tried the password of my account, and then the password I put in to do administrative things.  Neither worked.
Did you do an oem install? In order to use sudo the user must be a member of the admin group. If you did a normal (non oem) install the user you used during the install is a member of that group. 
sudo gedit is not always safe. 
Try opening the run dialog (Alt+F2) and enter.
```
**gksudo gedit /boot/grub/menu.lst**
```

---

### Post by HolyPhoenix on 2007-03-23
I Would, but when I got home I could no longer get into ubuntu, and it comes up with some job thing not implamented.  I am looking for answeres on that right not.  But I will try when I get back in thks.

---

### Post by HolyPhoenix on 2007-03-23
eeek, it looks like my other error is because grub is pointed to the wrong place.  

The error is the job turned off one.  So any ideas on how I can edit it without being able to access ubuntu?

```
Cannot access tty; job turned off
```

---

