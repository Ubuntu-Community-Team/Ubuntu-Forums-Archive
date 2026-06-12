---
title: "Grub"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by ibizatunes on 2008-01-15
I have somehow changed my grub setting to go from generic to server, i need to change them back
How can i do this? As i dont want it 2 boot to server by default

---

### Post by philinux on 2008-01-15
The system should have created a backup of the file menu.lst

Navigate to /boot/grub directory and see. All you need to do is replace the current file with its backup.

---

### Post by louieb on 2008-01-15
In /boot/grub/menu.lst look for this line: ```
default   0
```There is information on how to change this line in the file.

To open the file for editing. Press Alt+F2 and enter
```
gksudo gedit /boot/grub/menu.lst
```If you have trouble getting it to do what you want post menu.lst  and I'm sure you will get help getting it fixed.

---

