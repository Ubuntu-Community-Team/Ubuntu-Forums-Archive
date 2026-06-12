---
title: "Stop X server"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by venik212 on 2007-01-12
In trying to install the latest Nvidia driver (1.0-9831) I am asked to shut down the X server. How do I do it?
 I hit Cntrl-Alt-F1, init 3, but when I try:
sudo sh NVIDIA-x86-1.0-9831-pkg1.run I am told AGAIN that the X server is running, and that I should shut it down....
This can get to be very frustrating!

---

### Post by NeoLithium on 2007-01-12
Well, to restart the x-server, you can just do CTRL+ALT+Backspace and that'll restart the server and take you out to the login screen, without needing to reboot your computer.

---

### Post by taurus on 2007-01-12
Why not use this guide and install it!

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by venik212 on 2007-01-12
I used it previously, and it worked flawlessly.  Once I switched to the larger monitor, however, the script screws up my xorg.conf.  I spent many hours dancing around it, and now have the large monitor working, but no access to the GUI NVIDIA settings.

---

### Post by venik212 on 2007-01-12
I needed to know how to STOP it, not restart it.  When I used Cntrl-Alt-Backspace it screwed up the file system, which required learning all about fsck...

---

### Post by taurus on 2007-01-12
If you replace your monitor, you just need to run this command again to general a new xorg.conf file!

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If you need to stop GUI, just remove gdm and install it again if you want use it.

```
sudo aptitude gdm
```

---

### Post by venik212 on 2007-01-12
For that (or ANY)  command to work, my new monitor had to work, but it did not.
I finally got around it by using the LiveCD, but now I am trying to get the NVIDIA settings to work in a GUI mode, as they did after I ran the A. Milione ENVY script, which seems dysfunctional now, at least on my system.

---

### Post by gready on 2008-06-22
I have the same problem can't someone just tell us how to stop the xserver.
and to the ubuntu team sham on you for removing the option in the login screen for a console only login.

---

