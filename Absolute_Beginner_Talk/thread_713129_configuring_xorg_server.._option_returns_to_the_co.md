---
title: "configuring xorg server.. option returns to the command line"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Kevin Jones on 2008-03-02
I successfully installed Ubuntu 7.10 onto a dell xps 210 I use KDE

I  have an ATI graphics card (Groan)

I was trying to set the device to use dual monitors.
I am not sure how this happened but:
The secondary screen 'took over' as the primary screen. My primary screen does not work because the system cannot set/detect the resolution. The secondary screen resolution is very low.
 I went to system settings and and tried to adjust the 'monitor and display' settings I could not adjust the settings. even in 'administrator mode'
I ran the following command to reconfigure
sudo dpkg-reconfigure xserver-xorg

I chose defaults whenever I could,

When I get to the page:
'desired default color depth in bits... I chose '24 bits' right tabbed, and then hit OK
It seems that no matter what option I take the console appears below the Xorg config screen, the cursor is flashing on the console and not the set up screen and I cannot get back into set up without running the whole set up again.
Can any one tell me what I am doing wrong? I have done this same 'loop' about five times

Kevin

---

### Post by Kevin Jones on 2008-03-02
I should add that the command line says
xserver-xorg postinst wanring: overwriting possibly customized configuration file; back up in /etc/x11/xorg.conf.20080302122633

Still in the loop, not sure what to do.
Can I access the back up? and use that instead of re-configuring?
Any help??

Please!

Kevin

---

### Post by glennric on 2008-03-02
Yes, you can access the backup.  Go to /etc/X11 (cd /etc/X11) and type
```
sudo cp xorg.conf.20080302122633 xorg.conf
```

---

