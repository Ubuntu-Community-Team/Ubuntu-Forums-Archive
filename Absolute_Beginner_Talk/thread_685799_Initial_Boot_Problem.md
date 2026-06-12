---
title: "Initial Boot Problem"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by fella12 on 2008-02-02
Hello, I just want to thank you guys for the help beforehand.  Im a complete newbie and my problem is that I installed ubuntu 7.10 as a dual boot with vista on a dell 9200.  When I choose to boot gutsy it loads and I hear the intro drum beat then I get to a screen where I can use my mouse but what I see are a bunch of dotted lines.  It's almost as if the driver for the video card arent correct; as if I am looking the desktop on horrible resolution settings.  Please help, I have been at this for 2 days straight.  THanks again.

---

### Post by doddo on 2008-02-02
Hello! 

Which graphics card are u using?

I suggest that you hit CTRL + ALT + F1 to switch to console and then preform the following commands
```
sudo cp /var/log/Xorg.0.log /var/log/Xorg.0.log.bu
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bu
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart

```

And try to lower your screen resolution to max 1024x768 and select the "vesa" driver for graphics card. 

All this is just so you can get into the gnome environment, for it is much easier further troubleshooting from there,

---

### Post by fella12 on 2008-02-06
Hello...I had to reconfigure the x server..thanks for the help, i really appreciate it!!!

---

