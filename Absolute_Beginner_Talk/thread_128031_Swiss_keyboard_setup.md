---
title: "Swiss keyboard setup"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by Pretorian on 2006-02-10
Hi,
I have a problem with the keyboard, i am living in Swityerland and i would like to change obtain the right keyboard  QWERTZ for Switzerland.
I modified the keyboard in the menu System but nothing happend.
thanks in advance for your help

---

### Post by rwabel on 2006-02-12
how did you configure your keyboard when you did install it?
There is a section in /etc/X11/xorg.conf
mine looks like that
```
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "ch"
    Option        "XkbVariant"    "de"
EndSection
```

try to adjust yours and it should work fine.

---

### Post by Pretorian on 2006-02-12
Thanks for your answer!!!
But there a second problem, this file "xorg.conf" is a read-only file. How can I change this attribution?

---

### Post by christhemonkey on 2006-02-12
you need to open it as root.
If you open it from a terminal
```
sudo nano xorg.conf
```
 or if you prefer GUIs an stuff
Go onto Applications menu then select system or whatever last option is called, and go to run as different user.
Type gedit
select root user, then open the file that way.

---

### Post by rwabel on 2006-02-12
it must be read-only for normal user! :-) so you need to edit it as root. open it with your preferred editor with the sudo command. for example if you want to edit it with gedit, type the following command:
```
sudo gedit /etc/X11/xorg.conf
```

then you need to enter your root password.

---

### Post by Pretorian on 2006-02-14
Thanks a lot
It's ok now, I can leave completly the Bill's Evil

---

