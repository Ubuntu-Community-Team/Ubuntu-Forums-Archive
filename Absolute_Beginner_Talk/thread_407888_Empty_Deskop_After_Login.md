---
title: "Empty Deskop After Login"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by HiTM4N on 2007-04-12
Hey Everyone-

System specs- Compaq Presario R3065US laptop- 15.4 inch widescreen, Pentium4 3.2ghz, 1GB ram, ATI Mobility 9200 64mb.

I just set up a dual boot with Winblows XP and Ubuntu 6.10.  I checked the CDs for errors and everything- the CD is good.  I went through the whole install with no problems.

The login screen comes up and lets me login.  I see Nautalis load and all that and hear the startup sound.  It loads the wallpaper but nothing else on the laptop.  It lets me ctrl+alt+backspace and logout and stuff like that.  I can get to the command prompt also with ctrl-alt-F1.

Anyone have any idea whats going on??

Thanks in advance for you help :)

---

### Post by caffienefree on 2007-04-12
Try this in the terminal:

sudo gnome-panel

---

### Post by HiTM4N on 2007-04-12
Sorry man, didnt work.  When i go into the terminal, it goes into a black and white command line screen so i dont think that will work.

Is there a way to open up the terminal while staying in the desktop?

---

### Post by caffienefree on 2007-04-12
*smacks forehead*

Try **/etc/init.d/gdm restart** on the command line, and then switch to the interface. (ctrl+alt+f7)

Yes, but by default, that keyboard shortcut is disabled.

---

### Post by HiTM4N on 2007-04-14
Ok, I did that.  It says that it stopped the GNOME Display Manager then when it goes to start it again it fails.  I have no idea where to go from here :(

---

