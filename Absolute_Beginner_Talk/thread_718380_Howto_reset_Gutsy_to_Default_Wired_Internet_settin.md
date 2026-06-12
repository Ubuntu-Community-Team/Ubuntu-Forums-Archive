---
title: "Howto reset Gutsy to Default Wired Internet settings"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by urbushey on 2008-03-08
I've seen another post or two on this but the question is largely un-answered.

When I first installed Gutsy, the wired connections were detected and automatically worked with nm-applet in my tray etc. 

Recently I was trying to get a wireless network configured in ad-hoc mode, and of course I screwed with all sorts of settings. Now by the time I try and plug in the wired connection that was Just working a minute ago, I'm no longer able to connect with that, either.

Is there a way to have the system re-scan and re-configure this connection automatically, or reset my connection to the defaults, or do I have to try and figure out what I broke?  I didn't edit any config files but I did play with System > Administration > Network; and System > Administration > Network Tools.

---

### Post by MockY on 2008-03-08
You could always do this in a terminal window:

```
 sudo /etc/init.d/networking restart
```

---

### Post by urbushey on 2008-03-08
Hm, that didn't seem to work, and neither did restarting the DHCP server.

The nm-applet connects to the network (although it takes a very long time for a wired ethernet connection) but i can't connect to any web pages, and when I try network tools, I can't ping google.com or anything. Network info gives me '0' in every category and I am not assigned an IP address.

I've restarted several times, no avail. Everything worked perfectly out of the box, so if there's a way to just reconfigure my internet setup in the same way that Gutsy does when it detects/installs, that would fix things nicely. Otherwise I can begin the arduous process of finding out precisely what I messed up.

Basically the only things I screwed with were things suggested in the  [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc) community doc to try and get ad hoc wireless working (very little of which dealt with eth0, my ethernet device) and I'm pretty sure I only tried the things suggested under the Wireless Extensions CLI tools heading. 

thanks,
uri

---

### Post by urbushey on 2008-03-08
Also, I seem to have two ethernet devices configured perhaps?

In System > Administration > Network Tools, under Devices, I have eth0: avahi and eth0 (also eth1 and lo). Two eth0 devices seems to be just asking for trouble.

Any hints with that?

---

### Post by JermainWijnhard on 2008-03-28
*BUMP*

Hi, i recently got a new laptop and installed kubuntu. My internet (wired) worked out of the box and there were no problems. At work however i couldn't connect so a tech savvy guy offered to help by tinkering with the network settings. Long story short: now i dont have internet on it AT ALL.

Is there some way to reset it because i dont know the original settings anymore. All help is welcome.

---

### Post by superprash2003 on 2008-03-28
go to the terminal and type ifconfig and post results here

---

