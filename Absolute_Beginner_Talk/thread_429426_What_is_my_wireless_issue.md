---
title: "What is my wireless issue"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by lex524 on 2007-05-01
Hi all

Well I finally got Ubuntu onto my laptop, after some fun and games with partition software... I have now hit the common beginner brick wall of WLAN connectivity...

I have an Airlink 802.11g PCMCIA card. I know there are a lot of posts about this card when it "doesn't work", but I am still not sure whether I have a driver issue or not. The wireless card is definitely detected, as it appears in the network settings page (and goes away when I unplug the card). However, neither of the lights on the card are active (which they should be). Does this mean the driver doesn't work? I was assuming that if the OS can detect it as a Wireless card, it must have an appropriate driver, but now I am thinking it might be just PnP and the driver is still wrong/faulty

Ideas?

Thanks

Alex

---

### Post by starcraft.man on 2007-05-01
Take a look at [ndiswrapper]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29") in the ubuntu guide, I assume your on feisty. If your an older version pick your version at the index of the page. Check the supported hardware section of ndiswrapper and see if your card there. It should work though.

---

### Post by zetsumei on 2007-05-01
I gave up on my WiFi for my laptop.  I got so freaking annoyed I was about to throw the laptop out the window -_-

---

### Post by sirkism on 2007-05-01
> **zetsumei said:**
> I gave up on my WiFi for my laptop.  I got so freaking annoyed I was about to throw the laptop out the window -_-

I felt the same way, but after following the instructions that I found on this board and using wicd as my network manager it started working.

---

