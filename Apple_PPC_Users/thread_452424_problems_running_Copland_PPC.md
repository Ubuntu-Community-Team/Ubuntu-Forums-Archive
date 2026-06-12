---
title: "problems running Copland_PPC"
date: 2007-05-23
forum: Apple PPC Users
---

### Post by tr333 on 2007-05-23
Hi,

I seem to be having problems running the Community Preview of CoplandPPC.

after booting the CD, it failed to load X.  trying "sudo startx" just resulted in error (i have attached the error log).  it also prints the following error in addition to the error log:
```
fatal server error:
no screens found

X10: fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

```

i tried "sudo dpkg-reconfigure xserver-xorg" and i could run "sudo startx" afterwards, but that seemed to leave me logged in as "root" instead of "ubuntu" and stuck in 800x600 or lower resolution despite what i set in the reconfigure phase.  i was not able to change the resolution from the display properties in the system menu.

I thought this would be a good place to let the developer know of these problems, because i don't know any other place to leave a bug report for this :(


EDIT: i was running this on a 12'' Powerbook G4 (512MB RAM, NVidia GeForce FX Go5200)

EDIT: i have attached the default xorg.conf file present, and also the reconfigured xorg.conf that enabled me to start X11.  i have also attached the contents of /proc/cpuinfo, dmesg, /Copland/xorg-profiles/log.log and the previously mentioned xorg error log.

---

### Post by tr333 on 2007-05-23
default xorg.conf contents attached from above post.

---

### Post by stmiller on 2007-05-23
Okay looks like the problem is that the live cd put in the ATI driver when your hardware is Nvidia.

---

### Post by tr333 on 2007-05-23
after doing the reconfigure of xorg and starting X11, i have no idea why it was stuck in a low resolution :s

i should also mention that the mouse/trackpad was extremely slow to move across the screen :(

---

### Post by 3rdalbum on 2007-05-24
Thanks for the bug report. This looks like an upstream issue, as none of my code is touching your Xorg.conf.

Your collection of logs and correct Xorg.conf makes it possible for me to update xorg-profiles to deal with this situation. I'm assuming that, because this is a Powerbook, that the graphics is standard for your machine? (i.e. it didn't come with a different card originally).

Also, rather than "sudo startx", you can perform "sudo /etc/init.d/xdm restart" to give you a proper login prompt after reconfiguring.

---

### Post by tr333 on 2007-05-24
good to hear that people actually read bug reports :p

---

