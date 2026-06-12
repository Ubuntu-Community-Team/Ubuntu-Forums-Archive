---
title: "[SOLVED] Desktop or Server? I would like to utilize both features."
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by icceric on 2008-01-26
I suppose I should start this by telling you what I want to do...

1. Ability to use server functions for my home with the possibility of running it without a GUI (CVS/SVN, LAMP, file server etc).  I have Ubuntu 7.10 desktop installed on it now, but would like the ability to not have the monitor running at all times.

2.  Sometimes I will want to use the computer with the GUI using apps like GIMP, Xara and Eclipse while still accessing that same CVS/SVN repository and still running the LAMP services.

I have all of these functions now using the desktop version, is it better to somehow disable the gui when I don't want to run the monitor, and enable it when I do?  Or is it better to install the server version?  I imagine that at this point there is no difference between the desktop and server versions if I were to install the server version with a GUI, is that a fair assessment?

And finally...
Is it possible to create two user logins... using one to boot into gnome and the other to not even use a monitor?  Or perhaps a way that I can reboot the server from my Mac (ssh) and utilize the GUI / monitor.  Or is the monitor going to have to be on or off at all times?

BTW, I use an Apple Cinema Display, so not as easy as turning on / off the monitor, I have no power switch.  :) ... it's either on or not plugged in.

---

### Post by mortsahl on 2008-01-26
To disable the gui, open a terminal and type "sudo /etc/init.d/gdm stop" (that's assuming gnome, if you use KDE, type "kdm stop" instead"

To start the GUI, log in, then type "startx"

---

### Post by icceric on 2008-01-26
Thanks!

What will that do with my monitor?

---

### Post by mortsahl on 2008-01-26
It won't do anything to your monitor, just what is displayed on your monitor.

With X windows on, you get the gui, with it off, you get a back screen with a comand line.  As for as your monitor, turn in on or off as needed (unless I missed the point of your question).

---

### Post by mortsahl on 2008-01-26
Just reread your initial post...

I have a web server running on Ubuntu 6.06 ... I have no monitor on the machine.  Before I removed the monitor I set up VNC on the machine so I could do a remote connect to the machine.  If the gui is not up, it won't connect.

If the gui is not up, I can use ssh to connect to it.

However, altho I've never had a need to, just tried it, and don't know how to start x again from ssh ... short of rebooting the machine.

Maybe someone else can help.

---

### Post by icceric on 2008-01-26
> However, altho I've never had a need to, just tried it, and don't know how to start x again from ssh ... short of rebooting the machine.

Unless I can plug and unplug the power to the monitor after the computer is started up at will, I would have to restart the computer anyway, there isn't an active on/off switch on an Apple Cinema Display, It just reacts as "on" as long as the computer is feeding it and it is plugged into power.  Its an awfully expensive monitor and I don't want to burn it out just leaving it run all day if I'm not using it, you know?  But sometimes, even fairly often,  I will want to use it.

---

### Post by Whiffle on 2008-01-26
this might be helpful:

[http://acdcontrol.sourceforge.net](http://acdcontrol.sourceforge.net)

---

### Post by dcstar on 2008-01-26
> **icceric said:**
> ........
I have all of these functions now using the desktop version, is it better to somehow disable the gui when I don't want to run the monitor, and enable it when I do?  Or is it better to install the server version?  I imagine that at this point there is no difference between the desktop and server versions if I were to install the server version with a GUI, is that a fair assessment?
........

The server install defaults to installing the "-server" kernel, versus the "-generic" kernel which is more optimised for desktop response.

Unless you constantly use the machine for interactive desktop use it would probably perform better with the server kernel.

If you want to stop the GDM starting automatically on boot, just delete the /etc/rc2.d/S30gdm link - you can then manually start it on the server with the following command:
```
sudo /etc/init.d/gdm restart
```

---

### Post by icceric on 2008-01-27
wow... killer link and great info, thank you both very much!

Regards,
Eric

---

