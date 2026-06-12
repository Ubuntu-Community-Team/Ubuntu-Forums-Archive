---
title: "Crash when logging out"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by caravel on 2006-11-04
Running 6.06 Dapper Drake.

When I log out of gnome, KDE or Xfce, Linux crashes.  I can't do ctrl alt backspace nor switch to any virtual terminals.  There is a black screen with a mouse pointer, which becomes immobile.  This only seems to occur if I log out, not on reboots or system halts.

Any ideas would be greatly appreciacted.

Regards

Caravel

---

### Post by caravel on 2006-11-05
Bump

---

### Post by hearnden on 2006-11-05
Although I have no idea what could cause this, this tips might help you figure out what's going on.

To stop the X server, you can type in a Terminal window:

```

$ sudo /etc/init.d/gdm stop

```

If it successfully stops X and GNOME, then that rules those out as the culprits.  From the non-graphical console, you can type:

```

$ sudo poweroff

```

to shut down.  Maybe some error messages or other output can help to further diagnose your problem.

---

### Post by caravel on 2006-11-05
That would be great but I can't access any terminals.  The mouse pointer is frozen and ctrl + alt + backspace doesn't restart the X server either.

---

### Post by caravel on 2006-11-05
I have found this entry in the syslog:

```
Nov  5 17:07:14 localhost kdm_greet[4767]: Can't open default user face
Nov  5 17:07:24 localhost kdm_greet[4767]: Internal error: memory corruption detected
```

Also this:

```
Nov  5 17:07:12 localhost kernel: [17179800.624000] [fglrx] Internal AGP support requested, but kernel AGP support active.
Nov  5 17:07:12 localhost kernel: [17179800.624000] [fglrx] Have to use kernel AGP support to avoid conflicts.
```

How do I disable the kernel AGP support, and use that supplied by the driver?  Or am I barking up the wrong tree here?

My fglrxinfo output

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9000 PRO DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)
```

Any ideas... anyone? ](*,)

---

### Post by hearnden on 2006-11-06
Does the problem occur when you restart the X server after logging in successfully?  i.e. boot, login, do NOT log out but hit Ctrl-Alt-Backspace.

If the problem occurs there, then you could try to stop and start the X server by booting, logging in, then open a terminal and run "sudo /etc/init.d/gdm stop", and it should stop the X server and dump you to a console.  You can then try to restart the X server with "/etc/init.d/gdm start" and look for more problems.

Another idea is that it is a problem with the login process.  In GNOME  you could try to play with gdmsetup and try a different login theme.  I don't know that the equivalent is for KDE or XFCE.

---

### Post by junglepeanut on 2006-11-06
Old bug.

If I understand what you are experiencing correctly, (it is listed multiple times.)

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/30447](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/30447)

Mine is not fixed yet...

Many people list success through options listed in bug report.

---

### Post by caravel on 2006-11-06
> **hearnden said:**
> Does the problem occur when you restart the X server after logging in successfully?  i.e. boot, login, do NOT log out but hit Ctrl-Alt-Backspace.

If the problem occurs there, then you could try to stop and start the X server by booting, logging in, then open a terminal and run "sudo /etc/init.d/gdm stop", and it should stop the X server and dump you to a console.  You can then try to restart the X server with "/etc/init.d/gdm start" and look for more problems.

Another idea is that it is a problem with the login process.  In GNOME  you could try to play with gdmsetup and try a different login theme.  I don't know that the equivalent is for KDE or XFCE.

Ctrl alt backspace works fine, logging out does not.  It seems to be fine with Gnome and Xfce.  The problem only occurs with KDE.

I haven't tried "sudo /etc/init.d/kdm stop" or "sudo /etc/init.d/kdm start", I didn't think of that, thanks.

> **junglepeanut said:**
> Old bug.

If I understand what you are experiencing correctly, (it is listed multiple times.)

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/30447](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/30447)

Mine is not fixed yet...

Many people list success through options listed in bug report.

That's really useful info thanks!  I'll see if any of that works for me and let you know later.

Thanks for all the help.

Regards

Caravel

---

