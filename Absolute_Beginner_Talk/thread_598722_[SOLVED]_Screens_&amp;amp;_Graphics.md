---
title: "[SOLVED] Screens &amp;amp; Graphics"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2007-10-31
Hey,

I have a slight problem, i recently changed my screens and graphics set up so i could have two screens. When i unpluged the second screen, i decided to go back into the settings and disable the second screen, this is where the problem occured. 

In the bar at the bottom it says starting screens and graphics, this hangs for a while and then dispears and screens and graphics never appears so I can not edit the settings.  So if anyone has experienced this problem or knows the fix could you please let me know. I ve had this problem before with other applications and just ended up reinstalling the OS but i dont wish to do that this time.

Saj

---

### Post by taurus on 2007-10-31
Press <Ctrl><Alt>F2 to get to a console.  Log in and either edit /etc/X11/xorg.conf

```
sudo nano -Bw /etc/X11.xorg.conf
```
and save the changes with <Ctrl>o and exit with <Ctrl>x.

Or reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by saj0577 on 2007-10-31
> 

Or reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

Thanks alot :)

Saj

---

