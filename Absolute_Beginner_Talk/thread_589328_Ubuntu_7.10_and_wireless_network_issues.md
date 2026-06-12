---
title: "Ubuntu 7.10 and wireless network issues"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by rmhodv on 2007-10-24
Hi

Yesterday I recieved my new notebook without an operating system installed, along with a Netgear DG834G 54Mbps Wireless ADSL2+ Modem Firewall Router with 4-port 10/100 switch.

Upon getting my notebook I switfly installed Ubuntu 7.10. This is where I get stuck. How to you install the wireless network?:confused:

Please help.:)

---

### Post by Sef on 2007-10-24
When you try to use the wireless, do you get any messages, or does anything happen?  If so, what happens.

---

### Post by rmhodv on 2007-10-24
Ok, so I've plugged the router in to the mains, and connected to the phone line, what should I do next?

---

### Post by Pulka on 2007-10-24
errr....have you tried to read the router instructions? Usually they explain things very well.

I guess the next step would be logging in into the configuration page. Look in the instructions something like:

 192.168.1.1

Another possibility would be to connect the computer directly to the router through a network cable. After configurating everything, try the wireless.

good luck

---

### Post by realvz on 2007-10-24
can you try using this first and then let us know if this is no help
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by Pulka on 2007-10-24
i think he hasn´t got to that part yet. He´s still trying to set the router

---

### Post by realvz on 2007-10-24
connect the computer directly to the router through a network cable
then right click on the network applet icon in gnome panel (near the clock, on top right hand corner) and select connection information...
and post all you can read in that window here

---

### Post by rmhodv on 2007-10-24
Wow, thanks for all the responses. As I'm in the UK and it's 10:50 am, I'm currently at work. But I'll follow your advice when I get in this evening and post what I see. 
I'm very excited by this. For the first time ever I'm going to have a home PC without any Microsoft products installed. Not That I have anything against them, but just to prove it can be done, and done in a very competent manner.

---

### Post by realvz on 2007-10-24
be sure to share yuur success stories with friends and family :)

---

### Post by rmhodv on 2007-10-24
> **realvz said:**
> connect the computer directly to the router through a network cable
then right click on the network applet icon in gnome panel (near the clock, on top right hand corner) and select connection information...
and post all you can read in that window here

OK, I've done the above and connected the router directly to the laptop via a network cable and this is what I get when I right click.

Active Connection Information

Interface:                    Wireless Ethernet (wlan)
Speed:                         54 Mb/s
Driver:                          iwl4965

IP Address:                 192.168.0.2
Broadcast Address:    192.168.0.255
Subnet Mask:              255.255.255.0
Default Route:           192.168.0.1  
Primary DNS:              192.168.0.1
Secondary DNS:         0.0.0.0
Hardware Address:    00:13:E8:AA:74:FF


Thank you in advance for all your help. :)

---

### Post by rmhodv on 2007-10-25
Hi Guys

What do I need to do now?

---

### Post by Pulka on 2007-10-25
aren't you connected? then u don't need to nothing else :) Enjoy your ubuntu

---

### Post by MinstrelBoy on 2007-10-25
Open Firefox, enter  192.168.0.1   in the address box at the top and press enter.
You should get a login window, try   Username  admin   and  Password  password
(all this info is on the bottom of the router) 
That will get you into the router allowing you to setup it up with your ISP details.

---

### Post by rmhodv on 2007-10-25
Cool. I'm connected now. The only problem I have is that by default, on start up the pc connects to my neighbours wirless network as he has no protection. How do I make sure that I always connect to my network by default?

---

