---
title: "How do I uninstall kernal update 2.6.20-16?"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Jonothewright on 2007-09-29
I made the mistake of updating from 2.6.20-15 to 2.6.20-16. The update doesn't allow my laptop to boot up under the new kernal (it gets stuck loading) and I have to tell it to boot under the old one which is kinda annoying  to have to do everytime. Anyone know how I can get rid of the 2.6.20-16 or at least have it automatically start on -15?

Thanks

---

### Post by oilchangeguy on 2007-09-29
you can use synaptic, and delete the kernal.

---

### Post by srunni on 2007-09-29
GRUB should still have the old option in the boot menu. If the boot menu doesn't show up automatically, do ```
sudo gedit /boot/grub/menu.lst
``` from the Ubuntu LiveCD. Find the line that says "hiddenmenu" and put a number sign (#) in front of it. If you want to set it to select the old kernel automatically on boot, find the line that says "default". On the boot menu, count (starting with 0, not 1) the number that corresponds to the old kernel's regular boot (so if it's the 4th one, you'd put in "default 3"). Then when you boot up, it should automatically select that one, and boot it if you don't touch anything for 10 seconds. You can change this to any amount of time that you want as well, by changing the number after "timeout" in the GRUB config file.

---

