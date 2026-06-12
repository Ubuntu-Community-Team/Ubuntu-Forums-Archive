---
title: "Please Help!"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by xshady87 on 2006-03-18
For some reason I cannot login. I am given a prompt to type in my username and password, which I do. Then a prompt saying jason@jason:- $ comes up. I have no idea where to go from here.

---

### Post by stuporglue on 2006-03-18
> For some reason I cannot login. I am given a prompt to type in my username and password, which I do. Then a prompt saying jason@jason:- $ comes up. I have no idea where to go from here.

Well, that actually IS logging in, just not to the graphical interface. You didn't by chance do a server install did you? 

You can try to get a GUI up by logging in to the termial (what you're already doing), then typing:

sudo /etc/init.d/gdm start

sudo = Super User DO, (run as administrator)
/etc/init.d/gdm is the graphical logon manager
start is what you want gdm to do.

---

### Post by FizDev on 2006-03-18
You can also type
```
startx
```
to start the graphical interface. If you don't have it, I believe you can simply install everything correctly by doing
```
sudo apt-get install ubuntu-desktop
```
This will install Gnome, but if you want KDE, just do:
```
sudo apt-get install kubuntu-desktop
```

---

### Post by taurus on 2006-03-18
[QUOTE=stuporglue]Well, that actually IS logging in, just not to the graphical interface. You didn't by chance do a server install did you? 

You can try to get a GUI up by logging in to the termial (what you're already doing), then typing:

sudo /etc/init.d/gdm start

sudo = Super User DO, (run as administrator)
/etc/init.d/gdm is the graphical logon manager
start is what you want gdm to do.[/QUOTE]
If he did a server install, there won't be any /etc/init.d/gdm to run since there won't be any graphical program on his machine.  Therefore, he first must run
```

sudo apt-get install ubuntu-desktop

```

---

### Post by FizDev on 2006-03-18
Hmm... I just saw that you started another thread, and that you're not seeing any graphical interface because X makes an error. 
[http://ubuntuforums.org/showthread.php?t=146528](http://ubuntuforums.org/showthread.php?t=146528)

Would it be possible to post that error?

---

### Post by xshady87 on 2006-03-18
When I try: sudo apt-get install ubuntu-desktop
It says:  Building packaging list...Done
            Building dependency tree...Done
            ubuntu-desktop already istalled
            0 upgraded, 0 newly installed, 0 removed, 71 not upgraded


When I try:   sudo /etc/init.d/gdm start
It says:        Starting GNOME display manager....failed

---

### Post by stuporglue on 2006-03-18
Ok. Sounds like your graphics aren't configured properly then. 

First grab those updates incase the xserver or something is upgraded.

Do:
sudo apt-get update
sudo apt-get upgrade


Then once those install, do 

sudo dpkg-reconfigure xserver-xorg
(reconfigures the xserver, which is it sounds like isn't setup right).

This will bring up a series of screens with questions about your video card, your keyboard and monitor. Once you answer those questions, try running 

sudo /etc/init.d/gdm start 

again. If that doesn't work, run:

startx | grep EE
(Tries to start the GUI for just your user (no special login manager, and only prints the lines with "EE" in them. The lines with errors from startx have "EE" at the front of them. )

and post the lines it prints out. 

Good luck!

---

### Post by xshady87 on 2006-03-19
I tried everything above, but all I got was:

xauth: creating new authority file /home/jason.serverauth/.983
xauth: creating new authority file /home/jason.serverauth/Xauthority
xauth: creating new authority file /home/jason.serverauth/Xauthority

Fatal server error:
Server is already active for display 0
           If this server is no longer running, remove /tmp/.X0-lock
           and start again.



Please consult the The X.Org Foundation support
            at [http://wiki.X.Org](http://wiki.X.Org)
for help.

---

### Post by dueY on 2006-03-19
Try
```
sudo dpkg-reconfigure xserver-xorg
```

Set your video driver to "VESA"

---

### Post by IYY on 2006-03-19
The server is already active? That's strange. Maybe you just switched out of it? Try Ctrl+Alt+F7. Also, you could try to kill it and then start it again.

---

### Post by xshady87 on 2006-03-19
Horray! I set it to VESA, and everything is working fine now. It's funny how the little things make all the difference. Thanks a lot to everybody who helped me out. Though, I'll probably have more questions in the future. Thanks again.

---

### Post by dueY on 2006-03-19
[QUOTE=xshady87]Horray! I set it to VESA, and everything is working fine now. It's funny how the little things make all the difference. Thanks a lot to everybody who helped me out. Though, I'll probably have more questions in the future. Thanks again.[/QUOTE]

Well now that you've got it working with VESA you can research how to get your proprietary drivers working \\:D/

---

