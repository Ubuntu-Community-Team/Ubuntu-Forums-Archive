---
title: "Cable internet issues"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by theknave on 2006-10-31
I am staying at a friend's house, but her computer is extremely slow. I brought mine with me, but I cannot connect to the internet.

I've browsed through the other threads on this issue, but I am unable to find anything that helped.

The connection is as follows:

PC ---> Motorola Surfboard SB 5101 Cable Modem (from Rogers Cable) -----> Cable (ISP, I suppose)

Can anyone help?

---

### Post by theknave on 2006-10-31
Anyone, please? The computer I'm on would lose a footrace to a snail.

---

### Post by Henry Rayker on 2006-10-31
Are you sure your ethernet is actually up when you're trying to connect to the internet? What kinds of things have you tried? (so we won't go over the same stuff multiple times).

Is it possible her ISP requires a logon/authentication of some kind?

---

### Post by theknave on 2006-10-31
I don't really know where to start. At home I've used wireless (it took forever to set up, but I finally got it running), and ethernet cable through a modem, so there was no issue, just plug and play, so to speak.

I ran the ifconfig command which spat a bunch of information at me that I don't recognize.

EDIT:

When I tried connecting from Windows on my machine, it still wouldn't connect. There's a Rogers CD here that I could use to set it up on windows, but I'd much rather use Ubuntu, as that's where my files are.

---

### Post by Henry Rayker on 2006-10-31
I'd suggest running the CD in Windows, to see if that even fixes the issue. If it does, then you may be screwed. If it doesn't, then the problem lies elsewhere.

Another thing you could try is calling their tech support.

---

### Post by CatKiller on 2006-10-31
When I was setting Ubuntu up with a cable modem, to steps were really straightforward:

Plug the modem into my network card
Turn the modem on
Turn the computer on
Go to System -> Administration -> Networking and set eth0 up for DHCP
Reboot the computer

Some of these steps might not even be necessary.

Good luck.

---

### Post by David Corrales on 2006-10-31
Is the modem connected to a router or are you connecting directly to the modem? If it happens to be the latter, unplug the cable modem power cord. Then, connect the cable directly from your laptop to the cable modem and boot it up again.
The reason I'm suggesting this, is because some cable providers allow a maximum of concurrent MAC addresses connected to a given modem. The table is cached inside the modem's memory and you need to turn it off so it picks up your MAC address instead of another.
If the configuration goes like this modem->router->pc's then it should be easier to configure since it's your private network, no the cable company's one.

---

