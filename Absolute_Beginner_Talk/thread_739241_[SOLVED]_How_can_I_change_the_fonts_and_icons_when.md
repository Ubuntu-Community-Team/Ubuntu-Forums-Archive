---
title: "[SOLVED] How can I change the fonts and icons when I run an app with sudo?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2008-03-29
Hello,

Whenever I run a command or an app with sudo or gksudo, the desktop window goes back to 'Sans 10' and an ugly Gnome base. I would like to know if there is a way to set this to use the fonts and icons I have on my desktop theme.

Thanks in advance!

*PS: I don't have a root user account, so if I need one, please tell me how I can activate it first.*

---

### Post by Ub1476 on 2008-03-29
```
sudo ln -s /home/<insert your username here>/.themes /usr/share/themes
sudo ln -s /home/<insert your username here>/.icons /usr/share/icons
sudo ln -s /home/<insert your username here>/.icons /usr/share/fonts
```
I'm quite sure this is correct:)

---

### Post by kerry_s on 2008-03-29
you can create a /root/gtkrc-2.0 or link it to yours. mines linked to mine.
**sudo ln -s ~/.gtkrc-2.0 /root/.gtkrc-2.0**
if you want it different from yours, do it in root
**sudo gedit /root/.gtkrc-2.0**

check that you have a ~/.gtkrc-2.0 first, if not make it, put

**gtk-theme-name = "whatever"**  <-name of theme
**gtk-icon-theme-name = "whatever"**  <-icon theme
**gtk-font-name = "Sans 14"**  <-font to use

---

### Post by kerry_s on 2008-03-29
> **Ub1476 said:**
> ```
sudo ln -s /home/<insert your username here>/.themes /usr/share/themes
sudo ln -s /home/<insert your username here>/.icons /usr/share/icons
sudo ln -s /home/<insert your username here>/.icons /usr/share/fonts
```
I'm quite sure this is correct:)

no, it's not.

---

### Post by the8thstar on 2008-04-13
Thanks guys.

Being a GUI lover (yep, I like Windows too), I tried another way... 

First I followed your suggestions and copied my ~/.icons, ~/.themes and ~/.fonts to the root.Then I ran the 'Appearance' command in the menu with sudo. As simple as that. From there I was able to reconfigure everything that accesses the root account using my beloved theme and personal preferences. Now my interface is in complete harmony. :guitar:

---

