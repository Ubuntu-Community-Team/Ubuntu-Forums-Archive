---
title: "Firestarter when logging in"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by NegativeSpace on 2007-03-11
Hi,

Ubuntu automatically connects to a wireless network when logging in, so I thought I would try and launch Firestarter at the same time. I added *firestarter* to the *Startup Programs* in *Sessions*.

However, Firestarter requires root access and asks for a password, so when I log in I am told that I *"don't have privileges to start Firestarter"* (or something along those lines).

Is it possible to have Firestarter run without requiring the password when I log in?

Regards.

---

### Post by Delvien on 2007-03-11
This is a useful quote


> **yabbadabbadont said:**
> If you are just worried about having an active firewall when you login, then you don't need to start the firestarter GUI.  Once firestarter is installed and configured, a startup script is run automatically at boot that configures iptables (the real linux firewall) appropriately.  The GUI is just for viewing events/logs and making changes to the configuration.

---

### Post by garybrlow on 2007-03-11
firestarter already registers itself as on boot. It runs as daemon service in the background even before gdm/the login screen appears on your screen. Unless of course you compiled it yourself and did not install from the repos.

---

### Post by NegativeSpace on 2007-03-11
Ah, then I needn't worry!

Thanks Delvien, garrybrlow

---

### Post by astrolabio on 2007-03-11
Firestarter is always running. Even when you don't have the window. The window is used just to modify its configuration.

Anyway if you wish to start the configuration window as you start your windows manager and you're using kde put this in a text file inside your
~/.kde/Autostart 
folder.

#!/bin/sh
kdesu "firestarter --start-hidden"

then make that file executable. 
chmod +x nomefile

(the +x means add eXecutable attribute to the file)

If you instead use Gnome look around because I hate it with all my body so i dunno.

---

### Post by palletjackracer on 2007-03-23
So, if firestarter continues to run what is the process name?  I don't see anything obvious in my 'processes running' list.

---

