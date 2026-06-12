---
title: "Can't connect to wireless"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Want A Pie on 2007-12-13
Hey, I have a D-Link wireless router with a wireless internet connection set up with windows XP. It is also connected to a Mac OS X Leopard MacBook. 
I recently installed Ubuntu 7.10 onto my laptop, and I have not been able to connect to my wireless network.

I have checked my settings from my router's intranet, and this is what I've found:
MAC Address 00-19-5B-BF-C4-23
ESSID Colbeck House
Security 64-bit WEP Enabled
Channel 6

I have looked at people's tutorials, but I have no idea what to do with them, as I have only just started using Ubuntu.

---

### Post by Dr Small on 2007-12-13
Did you try going to System > Administration > Network, and configuring your network from there?
Or did you try selecting your network, from the little network applet in the top panel ?

---

### Post by Want A Pie on 2007-12-13
I've tried both, but I don't know how to use the Network Settings

---

### Post by Want A Pie on 2007-12-13
can anyone help?

---

### Post by hfranco on 2007-12-13
What model number is your D-Link wireless router?

---

### Post by Giradman on 2007-12-13
Well, as Dr. Small has mentioned above, you'll need to use the network settings applet and try to setup your 'wireless' connection there - if you have a WEP key installed on your router, then you'll have to figure out how to get it into your 'wireless' laptop running Ubuntu;  if that is a potential problem, you could 'disabled' your WEP security, and try establishing a connection w/ the Ubuntu laptop - if successful, then the issue has been at least partly explained; also, if you have MAC filtering enabled in your router, then double-check that the MAC number of your laptop is being accepted by the router.  Just a few more suggestions - please report back if any help - I'm new to Ubuntu myself and have had some problems figuring out this network stuff w/ my old IBM laptop!  :)

---

### Post by Want A Pie on 2007-12-13
Dl-524
and I connected to it before with this laptop
I am connected to it now, but with an ethernet cable, rather than wireless

---

### Post by hfranco on 2007-12-13
I have a DI-624 and I'm assuming that the web interface looks the same

[IMG]http://image.bayimg.com/iaijaaabc.jpg[/IMG]

You can try it in this format.  But you might want to enable SSID broadcast so that you can make sure that its working.

Also, as a side note.  You and me both should be using WAP, WEP stinks.

---

### Post by Want A Pie on 2007-12-13
Mine doesn't have that page, but it has a very similar one

---

### Post by anewguy on 2007-12-13
If you think your wireless is actually running, then check for a network icon on the top bar (assuming you are running the default Ubuntu - i.e., the gnome desktop).  It may look like a terminal with an "x" through it.  Left mouse click on that icon and see if your wireless network is showing.  If so, click on it, then when asked put in the wep key your router requires and be sure to say it's 64 bit hex, not the apparent default of 128-bit encryption, then let it connect.

If your network doesn't show, click on "system" then "administration" and then on "network".  The screen that comes up should say if your wireless adaptor is recognized and running (it will have "wireless connection" showing).  You also need to be sure that this is set to "roaming".  If the wireless connection does not show here, or it says it is not working, then we need to look at the drivers for your wireless card.

Post back what you find out from just this, and if we need to move on to your wireless card we'll try to handle that in the next step.:)

---

### Post by Want A Pie on 2007-12-13
wireless is working!!
thanks heaps!!
Now I just need to get my sound and Java working....

---

### Post by anewguy on 2007-12-13
You may need to download Java - I can't remember if the engine comes with Ubuntu or not.  For your sound - do you know what type of sound card you have?  Post the output of the following back here and I'll see if I can help or point you to somewhere that might.

click "applications", then "accessories" and over and down to and click on "terminal".  When the window opens, type    lspci   and press enter.  Copy the results from that and paste them back here in a reply.:)

---

### Post by anewguy on 2007-12-13
Getting some supper - be back to check in about an hour.:)

---

