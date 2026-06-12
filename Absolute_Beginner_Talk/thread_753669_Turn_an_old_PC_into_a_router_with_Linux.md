---
title: "Turn an old PC into a router with Linux?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-04-12
So, here's the deal:

I have some old equipment down in my garage that I'd like to be able to get online using a WIRED connection. I have a wireless router upstairs, but I don't want to run an ethernet cable all the way down into the garage. So, my question is, can I somehow set up an old PC (laptop or desktop, doesn't matter) to receive a wireless transmission from the router upstairs (in lieu of a CAT5, you see) and then transmit the connection over wired cable?

I've searched online, and all I find is people wanting the reverse of what I'm after. They want to run a short wire into their old box and transmit wirelessly.

I know precious little about networking, but I'm sure there's a way to do this. Anyone know how?

Thank you!

---

### Post by privaterolf on 2008-04-13
I'm pretty sure you'll need a Crossover Cable (Cat5e?) (ask at a computer/electronics store, they should be able to point you in the right direction).

You will also need the program Firestarter, available for free via Ubuntu's repositories (aka the Add/Remove programs option), or at their website (fssecurity, google it)

You may need to to a little mingling with your IP/network settings, but this took me all of 6 minutes to set up.

---

### Post by Csylleste on 2008-04-13
Since it is older equipment, the first question to sk yourself ..."Is it any good?"

I reently tried to restore and old box to get Linux up and running. Nothing was any good anymore an had to go buy a new motherboard, RAM, and processor.

And that should be your next question... "Can the older motherboard run wireless?"

If your equipment can handle this, and you have enough RAM, then yeah, it is possible.

---

### Post by Whiffle on 2008-04-13
If it were me, I'd buy a dd-wrt compatable wireless router, and set it up as a wireless bridge.  It'll use a whole lot less power and probably work better...

[http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge](http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge)

---

### Post by rs3 on 2008-04-13
> **doctorbighands said:**
> So, here's the deal:

I have some old equipment down in my garage that I'd like to be able to get online using a WIRED connection. I have a wireless router upstairs, but I don't want to run an ethernet cable all the way down into the garage. So, my question is, can I somehow set up an old PC (laptop or desktop, doesn't matter) to receive a wireless transmission from the router upstairs (in lieu of a CAT5, you see) and then transmit the connection over wired cable?

I've searched online, and all I find is people wanting the reverse of what I'm after. They want to run a short wire into their old box and transmit wirelessly.

I know precious little about networking, but I'm sure there's a way to do this. Anyone know how?

Thank you!

I apologize if this is not quite what you're looking for, but I had to do this too.  (At least, if I understand your predicament correctly.)

I took the computer with the wi-fi card.  I took the easy way out and installed Firestarter on it, then used Firestarter to enable internet connection sharing.  Without setting up a DHCP server on this computer, I instead assigned the wired connection a static IP of 192.168.0.1

Then, I assigned a static IP of 192.168.0.2, subnet mask 255.255.255.0, and gateway of 192.168.0.1 to the computer which required a wired connection.  I told Firestarter to use the wi-fi card as my internet connection and the wired card as the internal LAN connection, and it configured iptables for me.

A thread that features information on Firestarter for this use (he gives directions on getting DHCP working, which I skipped): **[http://ubuntuforums.org/showthread.php?t=74925](http://ubuntuforums.org/showthread.php?t=74925)**

You can do this by hand without a GUI or Firestarter, but I am not particularly savvy with iptables and can't tell you from memory how it is done.

This might help: **[http://www.debuntu.org/iptables-how-to-share-your-internet-connection](http://www.debuntu.org/iptables-how-to-share-your-internet-connection)**

Now, if it's not an internet connection that you're sharing, but rather an ad-hoc wireless connection (I was assuming that you're trying to communicate with an access point upstairs), I won't quite know what to tell you...

---

### Post by doctorbighands on 2008-04-13
> **Whiffle said:**
> If it were me, I'd buy a dd-wrt compatable wireless router, and set it up as a wireless bridge.  It'll use a whole lot less power and probably work better...

[http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge](http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge)

Do all WRT54G routers come with this feature? I happen to have one, but I'm not sure if it will do the job for me. Do I need to buy a new one? Can I update the firmware on the one I have to get this job done?

This is cool!

EDIT: Nevermind. I found the "compatible hardware" list on the dd-wrt website.

---

### Post by gartenzwerg2 on 2008-04-13
Hi,

I don't use my router on a wireless connection, but I've used an old 468-pc for many years now as a router with the german fli4l linux routing software, first via ISDN, now on a dsl line. It has many additional packages, also a WLAN package. I don't know if the fli4l-team has translated everything into english. Might be worth to check it out, though. [http://www.fli4l.de/](http://www.fli4l.de/)

---

