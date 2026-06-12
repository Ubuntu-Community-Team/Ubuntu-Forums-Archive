---
title: "NDIS wrappers"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by the lemming on 2007-06-14
I've downloaded a NDISWrapper and the driver for my Wireless Network card.  I then took them off my laptop and put them onto the desktop of my PC.

I have done all this because I have done a fresh install of ubuntu onto my PC.

I have now dropped the NDISWrapper and windows driver onto the desktop.

Could somebody please tell me how I install them?

Cheers

---

### Post by w4ett on 2007-06-14
This Wiki should help:  [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by vikram on 2007-06-14
use this to install the driver after installing the ndiswrapper

ndiswrapper -i /data/tew-424ub/Drivers/Windows\ XP/SiS163u.INF
ndiswrapper -l
ndiswrapper -m
ifconfig wlan0 up
dhcpcd wlan0 &

--------------
config files

note the "usb-4-1\:1.0" value u can get by looking at /var/log/messages after pluggin in the USB drive.

---

### Post by the lemming on 2007-06-14
This is all driving me mad.

I have very limited experience of Linux and I have tried every link and tutorial that I can read.

I have even tried the link a couple of posts up and when I try to follow the instructions for access to the internet on another computer I just get links which send me to page after page after page with nowhere to download what I can recognise.

All I know is that I have been to the NDISWrapper website and downloaded a package.  This is now on my desktop.

Could somebody please explaine what to do in simple and easily understandable language?
Please be patient with me.  I am neither a programmer or anything else technical in the world of computing.

---

### Post by rebelfox-uk on 2007-06-19
I am in exactly the same position.  I have been trawling link after link and no set of instructions or compilation of them have a complete answer for a new ubuntu user. Judging by the tens of thousands who have read the forum on the linksys WPC54g I guess there are a hell of a lot of other people
with similar issues. Don't assume they're finding the answer, more likely they're binning ubuntu and running back to their commercial OS. 

I was very excited when I first booted ubuntu yesterday but having spent over 8 hours trying to find
an answer to get my wireless network going I think I'd rather just get another windows licence.
Sure we can all blame the manufacturer for not providing a linux driver but it doesn't really help to solve the problem.

Anyway I'm not one to give up ubuntu seems too beautiful...although I wont be recommending it to friends or family at this stage. 

The ndiswrapper is not in my repositories and I have no idea how to put it there. All answers seem to say from the root directory make install. How do you run a command from the root directory? (Presuming this means the directory in which ndiswrapper has been copied to which for me is the desktop)

---

