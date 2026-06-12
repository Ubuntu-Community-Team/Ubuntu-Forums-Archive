---
title: "My Wireless card."
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Baelfael on 2007-02-18
Alright. I've probably asked for help countless of times for this. But I feel I need to do it again and get as much help as possible; because I'm desperate.

I own a WPC54G v3.1 wireless card. I cannot get the damn thing to work for the life of me. Usually when I put it in, lights come on; so it's detecting it. But I have no idea how to connect or install all these drivers. Is there some sort of tutorial aimed at newbies like me to get this particular model working with my laptop? It's driving me insane, really.

Mega thanks to anyone who can help me.

---

### Post by solar george on 2007-02-18
What chipset?

```
lspci
```

---

### Post by terdon on 2007-02-18
If it is detecting it you can try wlanassisant (in the repositories) and see if you can connect. If you are still having problems check out 
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/)


and the ndiswrapper wiki: 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

---

### Post by Baelfael on 2007-02-19
> **solar george said:**
> What chipset?

```
lspci
```
I think this is it:
```
04:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

Oh, and terdon, how do I use the wlanassistant?

---

### Post by solar george on 2007-02-19
Disregard this - use the link in my next post

It's the proper howto.



That's the same card as mine then.

I installed the ndiswrapper package and then used the attached package to install it.

Download the package, extract it into a folder open a terminal, cd to that folder and run the file with sudo.

In the example the files are extracted in /home/george/wireless
```
cd /home/george/wireless
sudo ./ndiswrapper_setup
```

I found the package on the forums - if I can find the thread I will post a link.

---

### Post by solar george on 2007-02-19
Here's the howto link
[http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")

---

### Post by Baelfael on 2007-02-19
I followed it, it seemed to install correctly, but it won't connect!! Is it supposed to connect automatically, or do I have to do something to make it connect?

---

### Post by solar george on 2007-02-19
Open the network settings program in the system menu - it should allow you to connect.

---

### Post by Baelfael on 2007-02-19
> **solar george said:**
> Open the network settings program in the system menu - it should allow you to connect.
I don't see anything that could connect me... it just has the devices and their properties.

---

### Post by solar george on 2007-02-19
Double click on the wireless adaptor (wlan0) this will bring up a config tool.

---

### Post by Baelfael on 2007-02-19
This is so confusing. How do I find my ESSID? Is my network password my WEP key? >_<

---

### Post by Baelfael on 2007-02-20
Anyone help here? =\

---

### Post by solar george on 2007-02-20
Your ESSID is your network name - you can find this in your access point config.

Your passwork is your WEP key

---

### Post by steveandarchie on 2007-02-20
Make sure it's WEP. Ubuntu (6.10) seems to see my wireless dongle (Netgear WG111v2) out of the box but I can't connect to it because I'm using WPA on the router and nothing I've tried works (although to be honest I've tried more with Puppy linux).

---

### Post by kelbizzle on 2007-02-20
I have the broadcom bcm4318. I use this thread [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
 everytime to get it working. After you run the script which sets up the card for you. Type into terminal:
```
sudo aptitude install network-manager
``` This will install the network-manger daemon and the gnome front end (the panel applet).

---

