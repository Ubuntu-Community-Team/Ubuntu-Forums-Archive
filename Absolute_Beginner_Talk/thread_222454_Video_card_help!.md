---
title: "Video card help!"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by rck_hitokiri on 2006-07-25
i cant resize my screen resolution to 1023x768 cauz i need a driver for my voodoo banshee vc can someone help please?

---

### Post by madmetal on 2006-07-25
have you look at /etc/X11/xorg.conf ?

---

### Post by rck_hitokiri on 2006-07-25
i tried it but i only had another "permission denied" message from terminal please help out. thanks.

---

### Post by mcvos on 2006-07-25
To look at system configuration files like /etc/X11/xorg.conf, you need to use 'sudo'. sudo gives you root permission for that one command, which is what you need to edit those files.

It's better not to edit /etc/X11/xorg.conf by hand, though.

---

### Post by rck_hitokiri on 2006-07-25
yes i tried sudo /etc/X11/xorg.conf just says "command not found" sorry for being a looser here but i really appreciate it. noob in da house. thx again bro.

---

### Post by testube_babies on 2006-07-25
```
sudo gedit /etc/X11/xorg.conf
```

You can manually edit the resolutions under Section "Screen"

---

### Post by Dr. Nick on 2006-07-25
yes, you can either edit xorg.conf by hand, or run the configuration script. look here for a little help

[http://www.geocities.com/aebcoat/index.html](http://www.geocities.com/aebcoat/index.html)

---

