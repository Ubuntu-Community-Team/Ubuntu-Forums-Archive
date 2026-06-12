---
title: "SBC YAHOO DSL and Ubuntu"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by aquavita on 2007-03-21
Hello members. I am new to Ubuntu, Linux and this forum. I am versed in PC's running Windows and basic functioning here. I have an old Compaq P3 Deskpro EN running Ubuntu 6.06.1 LTS. I also have SBC Yahoo DSL with a wireless capeable modem. I have read through many message threads on this forum regarding DSL and internet connectivity. 

I am attempting to get the Ubuntu on the Compaq to access the internet using a wired connection off of my 2Wire modem. I have attempted to access the internet after initially hooking the modem up via the USB cable, rebooting the maching numerous times and even re-installing Ubuntu with the modem connected. 

I have as of yet not been able to access the internet. It may be my incorrect assumption, from sorting through the posts in the forum, that you can access the internet using this type of setup. Now, in using network utilities on the Compaq I have been able to PING the IP's involved with my DSL connection. 

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.
C:\Documents and Settings\Gateway User>ipconfig
Windows IP Configuration

Ethernet adapter Local Area Connection:
        Connection-specific DNS Suffix  . : gateway.2wire.net
        IP Address. . . . . . . . . . . . : 172.**.*.**
        Subnet Mask . . . . . . . . . . . : 255.***.*.*
        Default Gateway . . . . . . . . . : 172.**.*.*
C:\Documents and Settings\Gateway User>

I have also gone into the UBUNTU device manager and seen where a 2Wire modem, shows up on the list of devices. What needs to happen in order to get this machine on the internet? 

The Fourm's help would be a step in increasing my knowledge to share with others. Thanks!

Chris Berg

---

### Post by Rotaj on 2007-03-21
Can you connect to the internet by a wired connection? If you can, then it becomes the issue of dealing with the wireless access. 

I am no expert in that area, but there are plenty of post regarding wireless connectivity in the forums.

---

### Post by lyceum on 2007-03-21
I may not have followed you correctly, you have a 2WIRE modem. Their routers work well with Linux, I have one it is great. Their wireless, from what I have read on their site, do not. 

try this thread...

[http://ubuntuforums.org/showthread.php?t=388461&highlight=2wire](http://ubuntuforums.org/showthread.php?t=388461&highlight=2wire)

---

### Post by Kobalt on 2007-03-21
If you have an ethernet capable modem then it's better using this interface instead of USB (which can be tricky to configure in Linux).

---

### Post by aquavita on 2007-03-26
**_Rotaj_** - The only way my machine can connect to the internet is via the USB wired connection off of the 2Wire Modem. The 2Wire modem which I have only allows the host computer, a wireless capable computer and a connection via the USB. The Compaq Deskpro I have UBUNTU installed on is not the host computer (a Gateway P3 is), does not have wireless capability so I have to use the USB connection. I currently get no recognition from UBUNTU that it is connected to the internet, it does seem to recognize the 2Wire modem but that is it. 

**_lyceum_** - I am not using the wireless function on the UBUNTU loaded Compaq I am attempting to use the USB connection off of the 2Wire modem. 

**_Kobalt_** - You bring up a great point. I have not tried this option yet. What I am wondering though is how I make it work using the 2Wire DSL modem. In my response to ROTAJ "2Wire modem which I have only allows the host computer, a wireless capable computer and a connection via the USB. " My only thought along your line is somehow to create an additional ethernet connection off of my Gateway P3 computer which is the internet host for the DSL connection. I have a Synoptics ethernet HUB but how to connect it in to the 2Wire DSL modem and still have internet connection on my HOST computer (Gateway P3) is my area of question in your proposition.  

Keep the information and ideas coming, I love learning LINUX!

Regards,
Chris (aquavita)

---

### Post by aquavita on 2007-03-26
OK.... Gosh I am so happy! I should have waited until now to post versus posting just a few moments ago. 

- I used the ehternet wire coming out of my 2Wire modem and plugged it into the first port on my ethernet hub. 
- I then plugged a cabel from port 2 into the back of my Gatway P3.
- Next I ran an ethernet cable over to my Compaq running UBUNTU...and rebooted. Guess what? I am now on the internet with UBUNTU..... How cool is this.... so new to LINUX and I now have a PC dependible running on the internet in a GUI / LINUX environment....


:guitar: :guitar: :guitar: :guitar: :-\" =D> :biggrin: :biggrin: 


I am so HAPPY!!!!

---

### Post by lyceum on 2007-03-26
> **aquavita said:**
> OK.... Gosh I am so happy! I should have waited until now to post versus posting just a few moments ago. 

- I used the ehternet wire coming out of my 2Wire modem and plugged it into the first port on my ethernet hub. 
- I then plugged a cabel from port 2 into the back of my Gatway P3.
- Next I ran an ethernet cable over to my Compaq running UBUNTU...and rebooted. Guess what? I am now on the internet with UBUNTU..... How cool is this.... so new to LINUX and I now have a PC dependible running on the internet in a GUI / LINUX environment....


:guitar: :guitar: :guitar: :guitar: :-\" =D> :biggrin: :biggrin: 


I am so HAPPY!!!!

That is very cool. Now that I understand your issue, I have read the getting the internet to work through USB is a pain for some.

Enjoy!

---

