---
title: "linksys wmp54g - dapper"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Vacharin on 2007-03-13
hi i justed installed dapper. everything looks fine but the only thing is that my wireless card (linksys wmp54g) is not working. i have no clue about the commands and such that i have seen in the other forums. i kno you have to type it in the terminal..but thats about how far my knowlegde goes..

ive seen other post and people asked for this 

iwconfig

lo - no wireless

eth0 - no wireless

eth1- ieee 802.11b/g essid:off/any nickename: "broadcom 4318"
        mode: Managed Access Point: Invalid Bit Rate = 1 mb/s
        RTS thr:off Fragment thr:off Link quality:0 Signal level:0 noise level:0 rxinvalid nwid:0 Rx invalid crypt: 0 Rx invalid frag:0 Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 - no wireless

please help thanks :)

---

### Post by orkim on 2007-03-14
Hrmm.  I guess the logical question to ask is if you are using WEP/WPA/WPA2.  If so, you are going to have a more complicated (but secure) setup.

It looks as though your device is recognized (at least a device) as a broadcom device.  I'm not sure that those linksys cards register as that.  Are there two wireless cards (maybe an internal and on in the pcmcia slot)?

A bit more information will be needed, but I think that by answering these questions we'll be started down the right path.

-orkim

---

### Post by Vacharin on 2007-03-14
i think i am using a WEP but in all honestly i dont know. the router should be all factory settings and the card is too.. i didnt change much about it. um there is an ethernet onboard the motherboard. could that be mixing up with it? and the linksys card is in the pci slot so i dont know where the mix up is.. i hope this helps.

---

### Post by orkim on 2007-03-14
I would imagine that this broadcom is the on board wifi.  I don't know of any LinkSys product that registers as broadcom.  I think that's probably the issue there.

If you are using WEP then you will need to know the WEP key that is on your router.  I'm assuming that you used the software that came with the router to initially set it up under a Windows environment.  If so, you probably don't know the WEP key because it typically sets it to something random or "encrypts" a pass code that you give it to make your WEP key.

You can typically connect to the router at [http://192.168.1.1/](http://192.168.1.1/) or [http://192.168.0.1/](http://192.168.0.1/) depending on the model.  There are many default passwords and if you haven't changed it, you will most likely be able to gain access.  After you are in you will most likely be able to locate whether you are using WEP/WPA/WPA2/etc and also obtain the keys that you are using.  This will (of course) need to be done from a computer that is hard wired into the router (after all, your wireless connection isn't working yet!).

There are many many many tutorials on the web regarding router setup and getting WEP working.  There are hundred of WEP/WPA/WPA2 Ubuntu tutorials here on these forums.  I would encourage you to do a bit of foot work and brush up on how these things learn.  If there are specific questions that I can help with I would be happy to assist.  Unfortunately, I will not be able to outline the entire process for you.

I hope this has given you some guidance on where to go from here.

-orkim

---

### Post by Vacharin on 2007-03-14
> **orkim said:**
> I would imagine that this broadcom is the on board wifi.  I don't know of any LinkSys product that registers as broadcom.  I think that's probably the issue there.

If you are using WEP then you will need to know the WEP key that is on your router.  I'm assuming that you used the software that came with the router to initially set it up under a Windows environment.  If so, you probably don't know the WEP key because it typically sets it to something random or "encrypts" a pass code that you give it to make your WEP key.

You can typically connect to the router at [http://192.168.1.1/](http://192.168.1.1/) or [http://192.168.0.1/](http://192.168.0.1/) depending on the model.  There are many default passwords and if you haven't changed it, you will most likely be able to gain access.  After you are in you will most likely be able to locate whether you are using WEP/WPA/WPA2/etc and also obtain the keys that you are using.  This will (of course) need to be done from a computer that is hard wired into the router (after all, your wireless connection isn't working yet!).

There are many many many tutorials on the web regarding router setup and getting WEP working.  There are hundred of WEP/WPA/WPA2 Ubuntu tutorials here on these forums.  I would encourage you to do a bit of foot work and brush up on how these things learn.  If there are specific questions that I can help with I would be happy to assist.  Unfortunately, I will not be able to outline the entire process for you.

I hope this has given you some guidance on where to go from here.

-orkim

thanks. appreatiate the help. :D

---

### Post by pete stahl on 2007-03-14
> **orkim said:**
> I would imagine that this broadcom is the on board wifi.  I don't know of any LinkSys product that registers as broadcom.  I think that's probably the issue there.

If you are using WEP then you will need to know the WEP key that is on your router.  I'm assuming that you used the software that came with the router to initially set it up under a Windows environment.  If so, you probably don't know the WEP key because it typically sets it to something random or "encrypts" a pass code that you give it to make your WEP key.

You can typically connect to the router at [http://192.168.1.1/](http://192.168.1.1/) or [http://192.168.0.1/](http://192.168.0.1/) depending on the model.  There are many default passwords and if you haven't changed it, you will most likely be able to gain access.  After you are in you will most likely be able to locate whether you are using WEP/WPA/WPA2/etc and also obtain the keys that you are using.  This will (of course) need to be done from a computer that is hard wired into the router (after all, your wireless connection isn't working yet!).

There are many many many tutorials on the web regarding router setup and getting WEP working.  There are hundred of WEP/WPA/WPA2 Ubuntu tutorials here on these forums.  I would encourage you to do a bit of foot work and brush up on how these things learn.  If there are specific questions that I can help with I would be happy to assist.  Unfortunately, I will not be able to outline the entire process for you.

I hope this has given you some guidance on where to go from here.

-orkim

I was able to connect to my router with my Windows PC being I can't get my wireless card to work with Dapper. How would I find out if it's WEP/WPA/WPA2/etc.? If I do know which one it is where do I go next. If I go to the Network page It says under my Wireless Connection: The interface ra0 is active. Another thing, is there anything I need to set in the Network Settings before I should try anything else first? Any help you can give will be much appreciated. I know this card works because I set up a dual boot and it works well on the PC side. I don't mind doing the setup my self, I just need more guidance though it. Still very green to ubuntu.

---

### Post by orkim on 2007-03-14
Honestly, I don't know where in Windows to find if its WEP/WPA/WPA2/etc.  I don't use windows much, sorry.

If you are able to log onto the router though, this information should be pretty easily found.  Like I said,  you will need to point a web browser to the routers IP address and login with a username/password to see the settings on the router.

You might want to consult your manual about how to log on and make changes.  If you've never done that before there should be a default password (and/or one printed on a sticker on the bottom of the router) to be able to access that page.

I hope that helps a bit!

-orkim

---

### Post by pete stahl on 2007-03-14
> **orkim said:**
> Honestly, I don't know where in Windows to find if its WEP/WPA/WPA2/etc.  I don't use windows much, sorry.

If you are able to log onto the router though, this information should be pretty easily found.  Like I said,  you will need to point a web browser to the routers IP address and login with a username/password to see the settings on the router.

You might want to consult your manual about how to log on and make changes.  If you've never done that before there should be a default password (and/or one printed on a sticker on the bottom of the router) to be able to access that page.

I hope that helps a bit!

-orkim
orkim,

Thanks you for the reply. I did log into my Modem and it says WAP Personal. What I wanted to know was why do I need to know this and what do I do with this information? I looked through a lot of instruction that want you to paste results from terminal commands but I can't get my modem to work! this is the really frustrating part.

---

### Post by orkim on 2007-03-14
WAP stand for Wireless Access Point.  That's not a form of encryption like WPA (noice the placement of the letters).

You might have a "security" or "encryption" tab that will tell you if WEP/WPA is being used.  You  might want to double check in there again for something like that.

The reason you need this information is that *IF* you use WEP/WPA there is a key that is used to encrypt/decrypt the wireless traffic.  You would most likely have to set this up in Windows as well, so you may not use it and run your WAP in open mode.  In open mode there is no encryption and any one (at least within range of the WAP) can access your internet connection.  You might want to look into WEP/WPA if that is the case.

Again, these are just general guides.  Hopefully there is something useful in there for you!

-orkim

---

### Post by pete stahl on 2007-03-14
> **orkim said:**
> WAP stand for Wireless Access Point.  That's not a form of encryption like WPA (noice the placement of the letters).

You might have a "security" or "encryption" tab that will tell you if WEP/WPA is being used.  You  might want to double check in there again for something like that.

The reason you need this information is that *IF* you use WEP/WPA there is a key that is used to encrypt/decrypt the wireless traffic.  You would most likely have to set this up in Windows as well, so you may not use it and run your WAP in open mode.  In open mode there is no encryption and any one (at least within range of the WAP) can access your internet connection.  You might want to look into WEP/WPA if that is the case.

Again, these are just general guides.  Hopefully there is something useful in there for you!

-orkim

Must be a little dyslexic, it said WPA Personal. I do have a password you have to enter to get into my network. Would like to know what needs to set to what in the Network Settings in Ubuntu, then what commands I need to enter in the Terminal to set up the driver/Wireless card, etc.

---

### Post by orkim on 2007-03-14
The only experience I've had was with a package called "wpasupplicant"

You should be able to follow this how-to and get yourself a working wireless connection:

[http://www.neowin.net/forum/lofiversion/index.php/t399787.html](http://www.neowin.net/forum/lofiversion/index.php/t399787.html)

Good luck!

-orkim

---

