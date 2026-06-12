---
title: "Run command on start"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by BlackLight94 on 2008-04-20
I looked for a previous post with this info on it, but none of those solutions worked for me. My problem is that I have a netgear Wg311 wifi card and it is supported on Ubuntu, and at the end of the guide it says to run ```
sudo ndiswrapper -m
``` to make it run on startup but that doesn't fix it. So now every time I restart or shut down I have to run ```
sudo modprobe ndiswrapper
``` to get it to work. I need a solution that doesn't require me to enter my password every time i start.

---

### Post by PeterJS on 2008-04-20
To run a command automatically on system startup as root you'll want to add the command to /etc/rc.local. But there's an easier/better way to automatically load modules, if you put the module name in /etc/modules, the system will automatically load the module as part of the normal boot process.

---

