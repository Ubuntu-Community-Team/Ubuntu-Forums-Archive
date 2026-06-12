---
title: "[SOLVED] Shutdown Problem"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by FotiX on 2007-03-29
I have Kubuntu 6.10 edgy, on Athlon XP 2800+.

When i try to shutdown or reboot my computer, sometimes it freezes in the first black screen. I mean, when it closes the desktop and it is about to show the shutdown progress bar, it freezes. Tried waiting but it doesnt seem to work. I then have to shut it down manually (pressing the button for 4 secs). I havent lost any data yet, but it still is unconvenient to do the procedure. Anyone know a way to solve the problem?

---

### Post by voltsy on 2007-03-29
I had a similar problem last night when I was fiddling about with running nvidia-xconfig and manually editing the /etc/X11/xorg.conf file

with one of the bad configurations, I had opened a non-GUI window with "<ctrl><alt>-<F2>" and issued the command sudo /etc/init.d/gdm stop (to close the GUI without actually shutting down) - or maybe I did <ctrl><alt><backspace> to back-out of the GUI

at that point my computer froze. so my suggestion is to check your graphics driver for errors in its configuration. once I got NVIDIA configured correctly the machine was stable again when exiting gdm/Gnome

HTH

;-)

---

### Post by FotiX on 2007-03-30
Thanks. I just reinstalled the driver and everything 's ok now (because i didnt know what to edit in the xorg file :D ) .
I also found out that by commanding "sudo shutdown -h now", it didn't have any problems.

---

### Post by charles.g.moore on 2007-03-30
> **FotiX said:**
> Thanks. I just reinstalled the driver and everything 's ok now (because i didnt know what to edit in the xorg file :D ) .
I also found out that by commanding "sudo shutdown -h now", it didn't have any problems.

Just something to think about, the 'sudo shutdown -h now' command should only be used as a last resort (which in your case probably qualifies) because I believe it does not allow processes to 'clean up' before they shut down.  In essence it is somewhat akin to a hard reboot.

---

### Post by FotiX on 2007-04-02
Thanks for the info. I 'll keep that in mind the next time I try to use the command. :D

---

### Post by spydon on 2008-03-30
Try to add the ```
apm power_off=1
``` to the /etc/modules file like this:
```
sudo gedit /etc/modules
```
and then just add the line :).

EDIT: Hehe you had allready solved it, you can mark the thread as solved now with "thread tools"

---

### Post by IanB2 on 2008-04-05
> **spydon said:**
> Try to add the ```
apm power_off=1
``` to the /etc/modules file like this:
```
sudo gedit /etc/modules
```
and then just add the line :).

EDIT: Hehe you had allready solved it, you can mark the thread as solved now with "thread tools"

This is a problem I've had on a couple of friend's boxes which I've been setting for them with xubuntu. Such a simple solution .... brilliant and thanks :)

---

### Post by spydon on 2008-05-05
> **IanB2 said:**
> This is a problem I've had on a couple of friend's boxes which I've been setting for them with xubuntu. Such a simple solution .... brilliant and thanks :)

Yeah, np, I wonder why it isn't in some files on clean installs...

---

### Post by noisygecko on 2008-05-13
> **spydon said:**
> Try to add the ```
apm power_off=1
``` to the /etc/modules file like this:
```
sudo gedit /etc/modules
```
and then just add the line :).

EDIT: Hehe you had allready solved it, you can mark the thread as solved now with "thread tools"

I just added this change for my Hardy 8.04 install on my Dell Inspiron 710m and it finally shuts down properly.

Thanks!

---

### Post by hkduddu on 2008-05-19
Thanks spydon man,

Cheers.

---

