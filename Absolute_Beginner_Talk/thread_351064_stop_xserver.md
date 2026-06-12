---
title: "stop xserver"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by cacharreo on 2007-02-01
Hi
How can I stop the xserver and run ubuntu in text mode? sometimes I would like.

---

### Post by someusernoob on 2007-02-01
log out (from the ubuntu desktop)

ctrl + alt + f1 (f1 /  f6 = tty, f7 = x)

sudo /etc/init.d/gdm stop

---

To return to your desktop

startx (to start X without gdm)

or

sudo /etc/init.d/gdm start

---

### Post by riven0 on 2007-02-01
If you just hit CTRL + ALT + F1 or CTRL + ALT + F2, etc, you should get to text mode. To get back to the xserver hit CTRL + ALT + F7

---

### Post by mikewhatever on 2007-02-01
Ctrl+Alt+F1 removes GUI
Ctrl+Alt+F7 restores

---

### Post by cacharreo on 2007-02-01
OK
but with **Ctrl + F1 .... F6** I go to text mode but the xserver still is running
with gdm stop the system shows me the message ***GDM still is running... Aborting***

---

### Post by bodhi.zazen on 2007-02-01
Did you sudo?

> sudo /etc/init.d/gdm stop

---

### Post by DaveArb on 2007-02-01
I can't guarantee this will work on Ubuntu (my Ubuntu computer is headless, and this command can be disabled in configuration), but the X kill command is Ctrl-Alt-Backspace. You want to close everything first, this is the GUI equivalent of pulling the rug out from under someone. Use with care.

---

### Post by bodhi.zazen on 2007-02-01
Yes, but after Ctrl-Alt-Backspace X (GDM) will re-start.

---

### Post by cacharreo on 2007-02-01
Yes I did sudo
with ctrl+Alt+Backspace the xserver restart after a few seconds

---

### Post by Brunellus on 2007-02-01
sudo /etc/init.d/gdm stop

sudo /etc/init.d/gdm start

the two are obvious. to combine the two:

sudo /etc/init.d/gdm restart

---

### Post by igknighted on 2007-02-01
If your goal is to install graphics drivers, did you try using the ones available in the Ubuntu repositories before downloading the ones from the manufacturers website?

---

### Post by someusernoob on 2007-02-01
As i said, you have to log out first from the Ubuntu desktop (you can find "log out" in the menu) before you can kill gdm. Otherwise gdm is busy because you are still logged in, so you can not stop it. thats what that error means: "GDM still is running... Aborting"

---

### Post by Brunellus on 2007-02-01
> **someusernoob said:**
> As i said, you have to log out first from the Ubuntu desktop (you can find "log out" in the menu) before you can kill gdm. Otherwise gdm is busy because you are still logged in, so you can not stop it. thats what that error means: "GDM still is running... Aborting"
no need to log out if you do it from another console---hence CTRL + ALT + F1, which brings you to a textmode console.

---

