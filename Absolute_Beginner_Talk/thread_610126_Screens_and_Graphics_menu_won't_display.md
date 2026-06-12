---
title: "Screens and Graphics menu won't display"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by AdamMPkins on 2007-11-11
After playing with dual screens, i disabled my second monitor and restarted my computer, upon restart, my resolution was the minimum and the screens and the screens and graphics menu wont open. In the taskbar, it says "starting screens and graphics" then it disappears and never opens.

---

### Post by AdamMPkins on 2007-11-11
am i doing something wrong on these forums or something because nobody seems to be able to help my issues.

---

### Post by TimMc on 2007-11-11
At the login screen press:
```
CTRL+ALT+F1
```

Then enter your username and password.

To reset your graphics to their default type:
```
sudo dpkg-reconfigure -p high xserver-xorg
```

reboot or halt your computer and start it up again and the graphics should at least work again...

---

Im a newbie to Ubuntu too so that's as far as I've got :-P

I'm currently looking for Linux Drivers for my SiS Mirage 3 Integrated Graphics :-/

Tim.

---

### Post by jrharvey on 2007-11-11
are you using compiz fusion? Did you just enable a restricted driver? Either one of these has given me trouble when changing stuff like that.

---

