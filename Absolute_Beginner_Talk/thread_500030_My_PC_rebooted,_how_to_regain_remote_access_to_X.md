---
title: "My PC rebooted, how to regain remote access to X?"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by OneLinux on 2007-07-13
I have been able to connect to my home PC (Ubuntu 7.04) from work using VNC, but after a power issue rebooted my PC today I can only access it via SSH. I tried to start x11vnc via the commandline in ssh but it errors out. I'm sure it is sitting at the gdm login screen at home. How can I gain graphical control of X in this situation?

(I've tried freenx but I can't get it to work.)

Any ideas?

---

### Post by Pom2122 on 2007-07-13
You need to set up auto-login.

```
sudo nano /etc/gdm/gdm.conf
```

In this section:

```
[daemon]
# Automatic login, if true the first local screen will automatically logged in
# as user as set with AutomaticLogin key.
AutomaticLoginEnable=true
AutomaticLogin=yourusername
```

save (ctrl o)
exit (ctrl x)

```
sudo reboot
```

ssh back in and restart x11vnc.

---

### Post by OneLinux on 2007-07-13
I hadn't thought about that option, thanks... however now when I try to start vnc I get:

13/07/2007 13:13:47 x11vnc version: 0.8.2 lastmod: 2006-07-12
13/07/2007 13:13:47
13/07/2007 13:13:47 *** XOpenDisplay failed. No -display or DISPLAY.
13/07/2007 13:13:47 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
13/07/2007 13:13:47 *** 1 2 3 4
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

13/07/2007 13:13:51

13/07/2007 13:13:51 ***************************************
13/07/2007 13:13:51 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.


The command I'm using is: sudo x11vnc -noxdamage -forever -solid -speeds dsl -passwd somepasswd

I even tried: sudo cp /home/MyUserName/.Xauthority /root/

---

### Post by Pom2122 on 2007-07-13
Hi,

Try the command ```
sudo x11vnc -noxdamage -forever -solid -speeds dsl -passwd somepasswd -auth /var/lib/gdm/:0.Xauth
```

(That's a zero, a period and an uppercase X) :)

---

### Post by OneLinux on 2007-07-13
I'm in! Awesome, thank you very much.

Now if I could only get FreeNX to work, but that's another day.

---

