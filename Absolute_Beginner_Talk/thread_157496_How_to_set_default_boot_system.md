---
title: "How to set default boot system"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by beef_thing on 2006-04-09
I am running dual boot on a system with Ubunto and Windows 2000, but I am confused at to how to configure the default bootup system(right now it's Ubunto). Any suggestions?

---

### Post by boodeey on 2006-04-09
If you want to change the default, you need to edit your /boot/grub/menu.lst. Open a terminal by clicking Applications -> Accessories -> Terminal. Now, type

Code:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak <-- making a backup copy
sudo gedit /boot/grub/menu.lstThen, count to see which number is the entry for your XP. Let's assume that your XP is the fourth entry (there are three title's before the one for XP), then at near the top, change the default value from 0 (currently) to 3... Save it and reboot!

---

### Post by beef_thing on 2006-04-09
Thx a lot! I'll try it now, then see if I'd have more problems

---

### Post by beef_thing on 2006-04-09
Yea! it works perfectly, THX again!

---

