---
title: "Problem with X"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by cybson on 2007-12-22
Hey there folks, was hoping you could help me out with a little problem I just ran into ...

Okey, so I for some reason, in some way, installed the package xserver-xgl last night, and everything was kinda running fine except I had major fps-lagg in games. So I removed the package. And when I logged in again I was greeted with this little annoying pop-up, telling me my screen and graphics card can not be determined or something like that. My first reaction was to bring in my backup-copy of xorg.conf and reboot, but no luck. I then tried toying around with the GNOME-settings, but no luck.

I am completely clueless. What should I do next? I can barely browse this site in 800x600!

Oh, and I am running Ubuntu Gutsy 32bit, and I have a GeForce 7600GS.

thanks in advance 

/ dani

---

### Post by taurus on 2007-12-22
At the GUI login screen, press <Ctrl><Alt>F2 to get to another console.  Log in and reconfigure your X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by cybson on 2007-12-22
> **taurus said:**
> At the GUI login screen, press <Ctrl><Alt>F2 to get to another console.  Log in and reconfigure your X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Did that, and it worked now.

Thanks for a fast reply.

---

