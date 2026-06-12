---
title: "[SOLVED] How do I add Icons to?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-12-05
How do I add Icons to this folder /usr/share/pixmaps  when I edit one and try to save it says I don't have permission

---

### Post by vikramsharma on 2007-12-05
> **J11Gyro said:**
> How do I add Icons to this folder /usr/share/pixmaps  when I edit one and try to save it says I don't have permission

Try using the sudo command for example you have icon named firefox.png on your desktop use 'sudo cp ~/Desktop/firefox.png /usr/share/pixmaps' without the quotation marks.  Hope this helps you out, you should do man sudo to know more about sudo. All this would have to be done through gnome-terminal.

---

### Post by shafin on 2007-12-05
Io copy bulk amount of icons,Run sudo nautilus,and work in the file browser,but be careful though,in nautilus as root,you are even able to wipe out your system files.

---

### Post by J11Gyro on 2007-12-05
Thanks worked like a champ

---

### Post by natehall on 2007-12-05
Nice tip! Thanks.

---

