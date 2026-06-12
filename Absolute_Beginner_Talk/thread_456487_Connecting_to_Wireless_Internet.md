---
title: "Connecting to Wireless Internet"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Keitarosan on 2007-05-27
I am having trouble connecting my laptop to my Linksys router with my Compaq Presario R3000 notebook, and I was just wondering if there was a guide to help with this problem that is not really difficult to understand. I've tried a few guides, but they either didn't work, or I didn't understand them.

---

### Post by ugm6hr on 2007-05-27
In Terminal - type:
lspci

And look for your Ethernet / Network controller - it will tell you what chipset your wireless uses.  Search for that here in these forums to see if someone else has succeeded.

If you've found a guide - just copy and paste what you don't understand here - and someone will try and help.

---

### Post by Keitarosan on 2007-05-27
I tried using this guide **[http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm4306)**
When I got to step 16, I went to the Network Settings and there wasn't an option for Wireless like there used to be before I started. I restarted the computer, and still nothing. Any suggestions?

---

### Post by oilchangeguy on 2007-05-27
> **Keitarosan said:**
> I tried using this guide **[http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm4306)**
When I got to step 16, I went to the Network Settings and there wasn't an option for Wireless like there used to be before I started. I restarted the computer, and still nothing. Any suggestions?

have you tried what was suggested in post #2?

---

### Post by Keitarosan on 2007-05-27
> **oilchangeguy said:**
> have you tried what was suggested in post #2?

I'm going to restart again and see

---

### Post by Keitarosan on 2007-05-27
Still not there, and near the end the guide creator said he changed his guide to fix this problem, but it still happened to me anyways. I'm not really sure what to do now.

---

### Post by ugm6hr on 2007-05-27
Afraid I don't have a Broadcom - and there are other HowTo's for this chipset (search for broadcom 43xx).
Have you seen this at the bottom of that page?


Totoro found a fix for the eth1 problem. Thank You Totoro!
add ndiswrapper to /etc/modules
change eth1 -> wlan0 in the files below:
Code:

sudo gedit /etc/modeprobe.d/ndiswrapper
sudo gedit /etc/network/interfaces
sudo gedit /etc/iftab

---

### Post by Keitarosan on 2007-05-27
I'm trying some of the other things people have said, but I'm not sure if they are working or not because Wireless doesn't appear in my Network Settings. Is there an easy way to reset things so I can get that back?

---

### Post by Keitarosan on 2007-05-27
Any suggestions?

---

### Post by Keitarosan on 2007-05-29
Hey, I'm still having the same problem with my Network Settings where Wireless is no longer there. Does anyone have any ideas or suggestions on how to get it back? Thanks.

---

### Post by Keitarosan on 2007-05-29
Any ideas at all? This is the last time I'm going to bring this up, thanks.

---

