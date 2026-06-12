---
title: "Having Wireless problems...like everyone else :("
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by mrdeeno on 2006-12-24
I installed Ubuntu and connected to my wired internet connection for all the updates.  Everything works fine except for my wireless connection.

I have a Broadcom card.  

lspci brings up the following: (copied at the end because all the stuff before doesn't matter)
0000:02:05.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
**0000:07:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**

I tried following some of the instructions posted using ndiswrapper and when i go to System > Admin > Networking it shows the Wireless connection (eth1) as active and when i click on properties, it shows the network name and the WAP code (which was entered).

But when i disable my wired connection to test my wireless, it doesn't work (the network monitor in the tray has an "!" in it.  

What could be wrong and what should I do?

This seems to be the only problem I'm having with the install so far.

---

### Post by Frak on 2006-12-24
Sorry for being bludgerant... but have you tried this?:
 [http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom)
Tell me if that worked.

---

### Post by MkfIbK7a on 2006-12-24
you probably have to blacklist bcm43xx if you havent allready

---

### Post by mrdeeno on 2006-12-24
> **Frak said:**
> Sorry for being bludgerant... but have you tried this?:
 [http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom)
Tell me if that worked.

I started to follow those procedures, but it said:

> It seems that if you get the following string back: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) that this guide is VERY unlikly to work for you

That's what I get when I run the lspci command.

---

### Post by Frak on 2006-12-24
Blacklist it.
(P.S. if you have to get a new card, go for an Orinoco, all of their drivers are open source and are included with Ubuntu, and it runs better on Linux than it does with Windows, should work on reboot, sorry for being bludgerant again.)

---

### Post by cilynx on 2006-12-24
```

rcw@angus:~$ lspci|grep Broad
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
rcw@angus:~$ 

```
I have mine working great using fwcutter.  Just to check it out, I slated my networking install and ran the tutorial linked to above and it still works great on the other end.  In all honesty, it'l less flaky than it was.

In response to the "blacklist" comment.  You absolutely do NOT want to blacklist bcm43xx.  That's the honest-to-God built in driver you're using.  You're not using ndiswrapper which (for some reason I don't understand) everyone seems to think you should use.

This was done on an hp8135nr.  Please run the procedure in the tutorial and let me know where it craps out for you...

---

### Post by MkfIbK7a on 2006-12-24
> You're not using ndiswrapper which (for some reason I don't understand) everyone seems to think you should use.  ndiswrapper is what works for broadcom chipsets

---

### Post by cilynx on 2006-12-24
```

rcw@angus:~$ lspci|grep Broad
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
rcw@angus:~$ lsmod|grep -i ndis
rcw@angus:~$ lsmod|grep bcm43
bcm43xx               141844  0 
ieee80211softmac       39040  1 bcm43xx
ieee80211              38088  2 bcm43xx,ieee80211softmac
rcw@angus:~$ 

```

There are two methods right now.  ndiswrapper is the hack that ndiswrapper has always been (wrapping up the windows drivers in POSIXy glue).  bcm43xx-fwcutter splices just the firmware out of the binary driver loads that up to the card, then implements a fully OSS driver.  fwcutter works better.  Trust me.  I've been using it with no problems for 3 months or so.

I'm not trying to be an ***, I just don't understand why people are so adamant on using ndiswrapper when there is a native solution available that works.

---

### Post by spockrock on 2006-12-24
I know you said WAP code, but do you mean WPA password, if thats the case you need to use either wifiradar, or network-manager-gnome/network-manager-kde to log into WPA wireless networks.

---

### Post by MkfIbK7a on 2006-12-24
i was never able to get that to work but im using ndiswrapper and its working like a charm much faster than windows:D

---

### Post by spockrock on 2006-12-24
ndiswrapper allows you to use windows drivers in linux for your wireless (and some other drivers).  This wont allow you to connect to a wpa encrypted wireless network.

To connect to a wireless network thats wpa encrypted, you need to use wpa supplicant, or as I mentioned wifi radar and gnome-network-manger (that is just a gui for wpa supplicant to my understanding).

I had to use ndiswrapper to get my fathers wireless card detected and install in edgy, and then use network-manager-gnome to connect to my wpa encrypted wireless network.

---

### Post by mrdeeno on 2006-12-24
Ok, got it working finally! 

The problem was that I followed the stesp in the link from Frak and it didn't work at first.  I checked my blacklist file and bcm43xx was blacklisted, which from what I understand is NOT what I want unless i'm using ndiswrapper. 

So i remarked it and rebooted, and now the wireless connection works!

But alas a new problem arises now.  I have disabled my eth0 (wired) connection, but now my Network Manager Applet displays what looks like 2 screens but with a "!" in front of it.  I was under the assumption that it should change to bars for my wireless connection strength.  

Anyone know how to change that?

---

### Post by MkfIbK7a on 2006-12-24
can you clarify what you just said a screenshot or something?:confused:

---

### Post by mrdeeno on 2006-12-24
> **wert613 said:**
> can you clarify what you just said a screenshot or something?:confused:

uh, how do you do a screen capture in Ubuntu (similar to ctrl+prtscr in XP)?

---

### Post by spockrock on 2006-12-24
just printscreen

---

### Post by mrdeeno on 2006-12-24
The one next to the battery is the icon i'm talking about...its like this when the wired connection is disabled.  

How can i get it to display the wireless connection?

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=21639&stc=1&d=1167000701[/IMG]

---

### Post by MkfIbK7a on 2006-12-24
hmmm....
does it connect to your network?
if so you probably should restart then it might show up

---

### Post by mrdeeno on 2006-12-24
yeah, its connected because i'm using it right now (i moved the router back downstairs). 

the light on the pmcia card blinks and stuff, so everything is cool except for that icon.  I'll try restarting and see what happens.

---

### Post by spockrock on 2006-12-24
ok that means you arent connected to a network, when your click on it, it should show you the available wireless networks.   Also, if you right click it should show enable networking, or enable wired and enable wireless, in case you don't see any available networks.

---

### Post by mrdeeno on 2006-12-24
When i click on it, it has "Wired Network" grayed out because i have disabled the wired network.  But there is no option for wireless network.  

When i right click on it, "Enable Networking" is checked.  Those are the only options I have.

I am connected to the internet through wireless though.

---

### Post by MkfIbK7a on 2006-12-24
did restarting work?

---

### Post by MrKlean on 2006-12-24
Go to tuxmagazine.com..on the right there's a how to on Ndiswrapper.  Near the end of the article it tells you how to associate manually.  That's what I had tom do to get my WG311v3 to work after doing everything else.  Don't know why..but it worked !!

---

### Post by mrdeeno on 2006-12-25
Yeah, i restarted but the icon and the warning sign is still there.

I think i'm going to go ahead and uninstall the network manager applet since it's not doing anything anyway.

does anyone know if there's another applet out there that monitors the network connection and blinks when it's transferring data?

---

### Post by Frak on 2006-12-25
GTK Wiki on the front page of the forums.

---

