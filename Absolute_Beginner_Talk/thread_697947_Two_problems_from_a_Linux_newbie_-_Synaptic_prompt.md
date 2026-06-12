---
title: "Two problems from a Linux newbie - Synaptic prompting for cd &amp; wireless problems"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by atmosfeer on 2008-02-15
Hey there,

I have no idea if this is the right place to post this, but as I'm new to Ubuntu and ubuntuforums.org, thought this was the right category. So here it goes.

My computer is a Zepto 3215W with Gutsy on it.

So I had installed my wireless card from Broadcom and it worked well, but one day, while using my computer plugged in to both power and ethernet, I took both these cables off, went to the network configuration to find another wireless network than usually (i was away from my place), and the wireless category suddenly disappeared in network configuration.

I had no idea why so I tried to re-install using ndiswrapper like I had the first time, but it didn't help, so I tried to remove ndiswrapper to install it again. I haven't been able to make it work since. When I type ndsiwrapper -l, it says that the driver is installed and the device is present, but iwconfig says that both lo and eth0 have no wireless connections what to do?

After trying to re-install ndiswrapper, synaptic asks me to insert my Ubuntu Gutsy installation CD, which it didn't do before... Did I accidentally toggle some option, is it supposed to be like that or is it just me that has no clue what the hell I'm doing? Now, every time I try to install a new package, it wants me to pop the CD in...

Any kind of help is greatly appreciated.

---

### Post by MasterJS on 2008-02-15
Have you tried the restricted drivers for your card?? For me, Gutsy made it way easier to install the wireless card drivers for my Broadcom 4318 (which used to be THE most annoying card to get to work in the whole LINUX COMMUNITY!)

---

### Post by Miljet on 2008-02-15
I don't know about the wireless card, but maybe can help with the CD request. Try going to System ->Administration ->Software sources and remove the check at the bottom of the page beside CD-ROM.

---

### Post by MasterJS on 2008-02-15
Miljet's reply is the answer for your CD troubles and you can try mine, its your best bet.

---

