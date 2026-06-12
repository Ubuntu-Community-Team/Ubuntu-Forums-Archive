---
title: "firestarer auto start"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-08-19
Hello, I would like to get Firestarter to start up each time I log in (I'm talking about the GUI, I think. Is this possible?? I think I read on this forum that the firewall program is always active.... TRUE?
Thanks ----- Love that Ubuntu

---

### Post by oilchangeguy on 2007-08-19
> **skyjacker said:**
> Hello, I would like to get Firestarter to start up each time I log in (I'm talking about the GUI, I think. Is this possible?? I think I read on this forum that the firewall program is always active.... TRUE?
Thanks ----- Love that Ubuntu

yes it's true. the built in firewall is always on.

---

### Post by sumguy231 on 2007-08-19
> I think I read on this forum that the firewall program is always active.... TRUE?
True. I don't know how to start things on login with GNOME, though.

Edit: Beaten!

---

### Post by expatCM on 2007-08-19
The firewall is always on through iptables.  This may be edited manually when changes are needed or a more friendly approach is by using FireStarter which provides a nice GUI.

The real question I have is why would anyone want to auto start FireStarter since the only function of the program (as I understand it) is to change the firewall settings, it does not start the firewall.  By reading this forum I can see that there are a lot of people who want to though but I cannot work out why ....  Am I missing the point?

---

### Post by skyjacker on 2007-08-19
I just like to see the events log to see whats going on while I'm on the internet.

---

### Post by Dr Small on 2007-08-19
Perhaps System > Preferences > Sessions > Startup Programs. You could try adding firestarter in there, and it may auto start...

Dr Small

---

### Post by Falcorian on 2007-08-19
> **expatCM said:**
> The firewall is always on through iptables.  This may be edited manually when changes are needed or a more friendly approach is by using FireStarter which provides a nice GUI.

The real question I have is why would anyone want to auto start FireStarter since the only function of the program (as I understand it) is to change the firewall settings, it does not start the firewall.  By reading this forum I can see that there are a lot of people who want to though but I cannot work out why ....  Am I missing the point?

Probably just used to windows, where if the firewall icon isn't in the system tray, it's not running.

Oh, and Dr. Small's method should work, that's how I'd do it.

---

### Post by oilchangeguy on 2007-08-19
> **expatCM said:**
> The firewall is always on through iptables.  This may be edited manually when changes are needed or a more friendly approach is by using FireStarter which provides a nice GUI.

The real question I have is why would anyone want to auto start FireStarter since the only function of the program (as I understand it) is to change the firewall settings, it does not start the firewall.  By reading this forum I can see that there are a lot of people who want to though but I cannot work out why ....  Am I missing the point?

no, you are correct. and the user needs to understand, that the more things that load at startup the more system resources are being used. and that can slow performance.

---

### Post by oilchangeguy on 2007-08-19
> **Falcorian said:**
> Probably just used to windows, where if the firewall icon isn't in the system tray, it's not running.

Oh, and Dr. Small's method should work, that's how I'd do it.

xp's firewall icon is not in the system tray (don't know about vista's) if you're running xp's firewall. a third party app like zone alarm does show in the system tray.

---

### Post by ramjet_1953 on 2007-08-20
One thing that you need to understand, is that it is not a good idea to run the Firestarter GUI on your desktop continually.

Why?

Because it needs to be run in root-mode.

Any application on your desktop running in root mode, while you are connected to the Internet is a serious security risk.

iptables is not broken, don't try to fix it!

Regards,
Roger :cool:

---

