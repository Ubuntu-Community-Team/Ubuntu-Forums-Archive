---
title: "Getting wireless to work...."
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Insp Gadget on 2007-04-17
I am so new to Ubuntu and Linux that it's not funny. I am trying the cd only version and have a question. How in heaven's name do I get my wireless network connected? Is there not a place I can see the available wireless networks and click on the one I want to connect to?

---

### Post by jakev383 on 2007-04-17
Go to System -> Administration -> Networking
Does your wireless card show up there? If not, you may need some extra steps to get it working. Tell us what card you're using - I'm sure someone has the same card and has gotten it working. I use a Broadcom in my laptop and had to use ndiswrapper to get it to work, as an example.

---

### Post by Insp Gadget on 2007-04-17
Hmm. I see three things there. Wireless , Network and Dial Up. I can go into Wireless, but I don;t see where I can search for available networks. How do i see the wireless network I want to connect to?

As for the card, I have no idea. It's the one that came with my Dell Inspiron 9300.

I find this odd. Yesterday I was playing with the Fedora live CD. After it booted, I pressed the network button and it showed me a list of available networks. I selected mine, entered my password and was connected. Should Ubuntu not be similar??

---

### Post by jakev383 on 2007-04-17
> **Insp Gadget said:**
> Hmm. I see three things there. Wireless , Network and Dial Up. I can go into Wireless, but I don;t see where I can search for available networks. How do i see the wireless network I want to connect to?

As for the card, I have no idea. It's the one that came with my Dell Inspiron 9300.

I find this odd. Yesterday I was playing with the Fedora live CD. After it booted, I pressed the network button and it showed me a list of available networks. I selected mine, entered my password and was connected. Should Ubuntu not be similar??

Highlight the wireless connection, select properties. Then tick enable connection and in the ESSIS box it should show you the APs around you.
Shouldn't it be the same? Yes and no. They're all based off of the same kernel, but whoever runs the distro (or it's parts) decides on what software to install, what drivers should be included out of the box, how it's configured, etc. That's why there's so many distros. Ubuntu worked the best for me, but my wireless was a 3-day ordeal. If I could have gotten it to work on Fedora I would use that instead, since I work on Redhat servers all day it would be more familiar.
One of the first programs you'll want to install is network-manager. Look for that one on the forums - it will make your life a lot easier.

---

### Post by kirab on 2007-04-17
> **jakev383 said:**
> Go to System -> Administration -> Networking
Does your wireless card show up there? If not, you may need some extra steps to get it working. Tell us what card you're using - I'm sure someone has the same card and has gotten it working. I use a Broadcom in my laptop and had to use ndiswrapper to get it to work, as an example.

Hey jakev383, is there a way to get the Broadcom drivers working with an internet connection?

---

### Post by Insp Gadget on 2007-04-17
> **jakev383 said:**
> Highlight the wireless connection, select properties. Then tick enable connection and in the ESSIS box it should show you the APs around you.
Shouldn't it be the same? Yes and no. They're all based off of the same kernel, but whoever runs the distro (or it's parts) decides on what software to install, what drivers should be included out of the box, how it's configured, etc. That's why there's so many distros. Ubuntu worked the best for me, but my wireless was a 3-day ordeal. If I could have gotten it to work on Fedora I would use that instead, since I work on Redhat servers all day it would be more familiar.
One of the first programs you'll want to install is network-manager. Look for that one on the forums - it will make your life a lot easier.

Unfortunately it shows me nothing. the box is completely empty. 

Is this Network Manager on the cd I burned? If so, how do I go about installing it?

---

### Post by N Clement on 2007-04-17
Go to the terminal and enter these commands:
```
lspci | grep Network

iwconfig
```

and copy paste the output to the forums.

EDIT: seems like | grep wireless might not work.  Use lspci | grep Network

---

### Post by bukwirm on 2007-04-17
The Dell Inspiron 9300 appears to come with a Intel 2200 802.11 b/g wireless card, which should be supported under linux just fine (mine is, at least).

Can you provide any information about the type of wireless network you're trying to find/connect to?

---

### Post by Insp Gadget on 2007-04-17
> **N Clement said:**
> Go to the terminal and enter these commands:
```
lspci | grep Network

iwconfig
```

and copy paste the output to the forums.

EDIT: seems like | grep wireless might not work.  Use lspci | grep Network

This is kind of difficult as I have to keep booting into two different OS to do this. I booted into Ubuntu and did as you suggested. I then copied and pasted the info to a text file on a USB drive. I then booted into Fedora and the file is not on the USB drive. Just my luck.

Anyway, if it helps, it said there was no wireless networks.

---

### Post by AOndusko on 2007-04-17
I am having a problem of a nature not unsimilar. I am assisting a friend with a desktop and his wireless conneection. Problem is when we have his wireless network device plugged in we get two  setable devices wmaster0 and wlan0, unfortunately we cannot seem to isolate what needs to be done with them. I myself have a laptop, and a wireless card that only gives me one thing, so I don't have that problem, but our cards are the same brand, although mine's a different class, that is his is a wireless - G from Linksys. So can you tell me what we're missing? We know all the network information, we just can't get the bothersome thing to work.

---

### Post by Insp Gadget on 2007-04-18
So is there anything else I can try???

---

### Post by N Clement on 2007-04-18
I know you already did this, and are probably feeling pretty frustrated at this point, but if you could try to get the output of these commands again, that would be great :KS 

```
lspci | grep Network

iwconfig

sudo ndiswrapper -l
```

The ndiswrapper command will only work if you have the ndiswrapper package installed, but you might so give it a try.

---

### Post by jakev383 on 2007-04-19
> **kirab said:**
> Hey jakev383, is there a way to get the Broadcom drivers working with an internet connection?

Sure. I'm using a Broadcom on my laptop while typing this using ndiswrapper.
I followed a how-to somewhere on the forum, but if you get stuck lemme know.

---

### Post by jakev383 on 2007-04-19
> **Insp Gadget said:**
> This is kind of difficult as I have to keep booting into two different OS to do this. I booted into Ubuntu and did as you suggested. I then copied and pasted the info to a text file on a USB drive. I then booted into Fedora and the file is not on the USB drive. Just my luck.

Anyway, if it helps, it said there was no wireless networks.
When you finished writing to the disk, did you umount the USB drive to close the writes?

---

### Post by jakev383 on 2007-04-19
> **Insp Gadget said:**
> I am so new to Ubuntu and Linux that it's not funny. I am trying the cd only version and have a question. How in heaven's name do I get my wireless network connected? Is there not a place I can see the available wireless networks and click on the one I want to connect to?
Do you still have windows on the machine? I looked your laptop up, but it could come with one of about 5 different wireless cards. Knowing which card it is would help us get you started in the right direction.

---

### Post by bytejunkie on 2007-04-19
I'm having a similar issue.

ubuntu 6.10, fairly vanilla install, with both the sucom (or safecom) dongle based on the ZD1211 chipset or the Netgear WG111T USB stick. 

i've narrowed it down to the inability to configure which channel you want network-manager to scan on. I've moved the channel of my dg834t to channel 6. I can't however work out how to move the channel of my wireless connection to channel 6

I have tried

```


sudo iwconfig eth1 channel 6


```

so for the ubuntu geeks in here, why doesn't the command above work?

and for the original poster

take note of the channel being used by the router.
take note of the channel listed in the iwconfig info
work with this page to convert frequency into channels
[http://ubuntuforums.org/showthread.php?t=92142](http://ubuntuforums.org/showthread.php?t=92142)

force the router to talk on the same channel and see if that helps. i cant because of massive interference on channel 1 which seems to be my routers preferred channel of choice.


another question. how do you subscrive to a thread on this board?

Matt

---

### Post by bytejunkie on 2007-04-19
I wonder if this post has a bearing on things?

[http://ubuntuforums.org/showthread.php?t=413071](http://ubuntuforums.org/showthread.php?t=413071)

Matt

---

### Post by bytejunkie on 2007-04-19
this post too...

[http://ubuntuforums.org/showthread.php?t=412957](http://ubuntuforums.org/showthread.php?t=412957)

Matt

---

### Post by sailor2001 on 2007-04-19
if you are still on windows and want to check what wireless card you have, download BELARC and it will audit your hard drive and peripherals

---

### Post by nvteighen on 2007-04-19
Hey, Feisty will do it much easier, believe me.

I'm using the Feisty Fawn Live CD currently and it detected everything from the desktop. Of course, you should wait to download it (I had luck to pick a UK server that wasn't overloaded at that moment).

---

