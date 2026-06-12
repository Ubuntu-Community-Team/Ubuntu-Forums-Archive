---
title: "Need help with GRUB"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by IsKall on 2006-02-05
I recently installed Ubuntu and GRUB on my laptop, but I don't wan't the boot should start ubuntu first (not yet), how do I change so Windows XP starts first?

/IsKall

---

### Post by bartbes on 2006-02-05
In your /boot dir is a grub config file, in that file change the boot order, for more information just search this forum, I remember reading a thread about this

---

### Post by taurus on 2006-02-05
Assuming your Windows is the second entry in /boot/grub/menu.lst, change the default to 1 in from it

sudo gedit /boot/grub/menu.lst
(The line above is to edit /boot/grub/menu.lst)

Then, change
default 0
-to-
default 1

Save it and reboot...

---

### Post by bartbes on 2006-02-05
Didn't had the filenames he said because i'm now in windows (because of a problem described in another thread)

---

### Post by Klaidas on 2006-02-05
Use this guide: [https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

Remember to run ```
sudo update-grub
``` after you have changed your menu.lst :)

---

