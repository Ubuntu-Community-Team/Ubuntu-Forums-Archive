---
title: "[SOLVED] Palm m500 &amp;amp; Jpilot problems."
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by SirJ77 on 2007-09-14
First off, I have done searches (search is about useless, but I tried), and most posts have incomplete info, or are for Ubuntu/Gnome.  I an running XUbuntu, and have no intention of running Gnome or KDE.  A decent generic step-by-step how-to would be handy, instead of trying to pull info from scattered posts that all assume that Gnome is being used.

So far I have gotten JPilot to sync once.
After that, my m500 complains the port is being already in use by another application.
I have unplugged the palm, and exited Jpilot, and tried again without any luck.
Sometimes the palm will try to communicate, but eventually times out.

What I have done...
I ran 'sudo modprobe visor', per one post.  I verified that visor and usbserial modules are loaded.  I don't know if these are the correct modules for the job.
In Jpilot, I have tried using '/dev/pilot' and 'usb:'  per other posts.
The time it did work, it was set to /dev/pilot
I have tried different button combinations (jpilot first, palm first, cradle button first).

Obviously something is still missing, or I don't understand how something works.  Any tips would be appreciated.  
I've only been running Xubuntu for about 2 weeks.  I have played with other distro's over the years, but this is my first time trying to sync my palm.

---

### Post by linuxwizard on 2007-09-16
[https://help.ubuntu.com/community/PortableDevices/PalmOS](https://help.ubuntu.com/community/PortableDevices/PalmOS)

[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

Note: To make it absolutely clear, when I say 'Ubuntu', I mean Ubuntu AND Kubuntu AND Xubuntu (for people who find this confusing - just accept it and don't feel bad - I and probably a whole lot others got confused when we started out).

---

### Post by SirJ77 on 2007-09-17
Ok, cool, now it syncs reliably.  The 2nd url did it for me.  I remember seeing that page, but for some reason it didn't click what it was telling me.  Must have been tired. lol

I'll attempt to recap, so hopefully this does someone else some good later.

Running on Xubuntu (my preferred flavor), and Jpilot sync'ing with a Palm m500 via usb...

Used the package manager to search for Jpilot and installed (it picked a couple other dependencies to go with it I believe).

In Jpilot, File menu, preferences, settings tab,  Under 'serial port' entered /dev/pilot

From a terminal window, entered 
sudo mousepad /etc/udev/rules.d/10-custom.rules

Per [https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)
I entered...
BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"
... into the file, and saved.

Per the same webpage, still in the terminal, I entered...
sudo mousepad /etc/modules
And after the last entry entered...
visor

Saved the file, Reboot, start jpilot, pushed sync button on cradle first, then sync on jpilot, and all was well.  Did it again for good measure, still worked no problem. :)
Hope this does someone else some good.
Just for FYI, [https://help.ubuntu.com](https://help.ubuntu.com)  is a good url to keep handy. Just don't try to read the stuff when your tired. lol  Thanks linuxwizard.

---

### Post by linuxwizard on 2007-09-17
I'm glad that you got your Palm setup and working. Nice review or recap on the steps you took to get it working. Please mark thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

