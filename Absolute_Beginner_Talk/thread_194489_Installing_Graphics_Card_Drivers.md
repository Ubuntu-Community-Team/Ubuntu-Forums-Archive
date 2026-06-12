---
title: "Installing Graphics Card Drivers"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by C!pheR on 2006-06-11
Hi there!

First of all, I've only just installed Ubuntu 5.10 today, I've never used Linux before in my life so please bear with me if I'm being stupid.  ;) 

I've attempted to install nVidia graphics drivers from the Synaptic Package Manager.  I've downloaded the nvidia-glx drivers and done the terminal bit "sudo nvidia-glx-config enable".  This seemed to work, so when it finished I rebooted.

I've got a screen of gibberish!  I'm now sitting with a command prompt window and absolutely no idea how to get the GUI back.  Stupidly I didn't write down the command to restore from before the installation and now i can't remember it!  Please help me!

---

### Post by Aurelias on 2006-06-11
First, I'd seriously recommend installing Ubuntu 6.06 -- the latest -- instead of 5.10.  Once you've done that, try searching the forums for an nvidia tutorial; I'm sure someone's written one up by now.  That and I use ATI, so I'm not sure what the process is for nvidia :p
-Aurelias

---

### Post by steve.horsley on 2006-06-11
A quick way to turn off the nvidia drivers is to edit the /etc/X11/xorg.conf file and change the line:
```
    Driver "nvidia"
```
to
```
    Driver "nv"
```
then restart the desktop manager. The commands you need are:
[B]sudo nano /etc/X11/xorg.conf
sudo /etc/init.d/gdm start[/B]

---

