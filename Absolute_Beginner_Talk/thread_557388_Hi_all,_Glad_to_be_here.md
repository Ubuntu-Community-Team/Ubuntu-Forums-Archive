---
title: "Hi all, Glad to be here"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by jadonchristensen on 2007-09-22
I am new to Ubuntu, not new to Linux. I am very impressed with the performance and quality of Ubuntu. I had the best experience installing Ubuntu ISO then Kubuntu-Desktop through Synaptic. The other way of installing Kubuntu ISO, then Ubuntu-Desktop didn't go as smooth. I want to use both Gnome and KDE tools, so this works best for me. Great job and kudos to all the developers and programmers out there who make this all possible.

Have a good one,
Jadon

Below is my little MySpace blurb:
=========
This is what I did. Use this information at your own risk.

Setup Partitions
15GB for /
1GB for swap

Install Ubuntu

Update
System > Administration > Update Manager
...update and reboot when prompted

System > Administration > Restricted Drivers Manager
...enable driver and reboot when prompted

Applications > Accessories > Terminal
...type sudo nvidia-settings

Change resolution and refresh rate, under Server Display Configuration
...click Apply
...click Save to X Configuration File
...Quit

System > Administration > Synaptic Package Manager
...search for kubuntu-desktop (this will give you KDE)
...install it

When kubuntu-desktop is done installing, you should be able to choose KDE or Gnome at the login screen. At this point, I go back into Gnome.

System > Administration > Login Window
...select Local
...click the "circle" next to Happy Gnome with Browser. This allows you to select different users at the login screen instead of having to keep typing your username.

You don't need to run as root because they set it up so you can do most anything using sudo.
Examples at a terminal:
sudo konqueror
sudo nano /etc/crontab
sudo nvidia-settings

I read that you dont need to do any further firewall configuration because iptables or something is setup by default. However, you can install "firestarter" using Synaptic Package Manager. Firestarter does not need to run all the time, because it's only used to setup the iptables. I have yet to setup samba, so I shall see how that goes.

---

### Post by TheFourElements on 2007-09-22
welcome

---

