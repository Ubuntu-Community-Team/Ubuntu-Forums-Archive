---
title: "solving wifi issues - where is network manager"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by mor10 on 2007-01-14
I'm trying to get Xubuntu Edgy to work on a Sony Vaio that is being crushed under the weight of all the Windows updates. The installation itself works like a charm but I just can't get the PCMCIA WiFi card to work.

Let me correct that... as far as I can tell the wifi card works but I can't get it to connect to anything. 

The card btw is a D-Link AirPlus DWL-G650.

MadWiFi is running and when I put the card in it is recognized in Network Settings. But I can't get it to log on to any network.

I've searched around and tried to find an app that will let me see all the available networks and choose one (there are 6 available networks here). My research tells me I should be using NetworkManager. So I install the app through Add/Remove Applications, reboot and then.... NOTHING.

Where is Network Manager? I can't find it. I'm sure it's because I'm a total idiot but still it's very annoying. It's not in the Applications menu and when I try to run it manually (Alt+F2) it says there is no such application.

any help would be greatly appreciated :o)

mor10

---

### Post by cilynx on 2007-01-14
The available ESSID browser doesn't work under Edgy to the best of my knowledge.  

Not sure what xUbuntu uses for a network manager...

If you want to take a shot on the command line, take a look at 'iwconfig'

---

### Post by edmund on 2007-01-14
nm-applet should be running, causing a terminal-like icon to appear in the deskbar at the top right of the screen. Left-clicking on that should show all the available networks.  
If it doesn't, there is some useful info in the first post of this thread:
    [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)
though not all of it may be relevant.

---

### Post by mor10 on 2007-01-15
thanks guys

dunno exactly how it happened but after a few more tries everything just started working.... 

on to the next problem I guess

mor10

---

### Post by grogger13 on 2007-02-22
im have the same problem under edgy, dont know what to do

---

