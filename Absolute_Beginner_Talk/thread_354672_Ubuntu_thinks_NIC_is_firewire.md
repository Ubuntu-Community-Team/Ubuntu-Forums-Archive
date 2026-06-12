---
title: "Ubuntu thinks NIC is firewire"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Bright Carver on 2007-02-06
Hi there

I just did a dual-boot on my laptop, and while installing Ubuntu, a message came up saying there was no network available, but it had found a firewire, and would I be using that for internet.  I installed it saying no (because I don't know what I'm doing :)), but I can't get connected to the internet.

I'm using a Motorola SB4200 cable modem which can do a normal network cable or an USB.  I've tried both of them to no avail.  Should I have said yes to use the firewire (although I'm pretty sure it's actually a NIC because the plug fits) and installed it that way?

Failing that, if I can't get internet on it, how easy is it to install software from CD's?  I would like to try my Windows software in WINE and see if it works, and maybe some other software I've seen, like Rosegarden and Ardour.

I just use XP for playing music on stage, and I don't want to let it on the internet, or use it for anything else, so I thought having Ubuntu would be a good solution.

Any help you can give me would be appreciated

Thanks

Karl

---

### Post by Bright Carver on 2007-02-06
:confused: 

I'm going to try a reinstall of Ubuntu with firewire internet enabled, and then I'm going to try with Knoppix or something.  If that works, there should be something I can do :)

---

### Post by aseneca on 2007-02-06
Stick with Ubuntu!

Although upon install there are can be several issues, posting, googling, and experimentation can usually lead to a solution.

Try posting some of your system specs here (eg. terminal> dmesg).

What have you tried?  System> Administration> Networking

AS

---

### Post by Bright Carver on 2007-02-07
Thanks for the reply.

All I want to do is to install software.  :(  The only ways seem to be DVD's and the internet, and my laptop can't handle either...

I've tried going through the setup you get when you start Firefox, that didn't work.  I tried system->admin->network and network tools (although I'm just sort of poking it blindly) and none of them would get me connected.

I tried Googling around for a bit, but couldn't find much.  Not that there isn't a solution out there sometime, it's just that I'm not sure what I'm looking for.  A couple of people seem to have had my problem in '04 and '05 on different distros and I'd like to get a little human advice before I went experimenting.  Also I have to keep rebooting computers just to swap the internet connection round, so I can't Google while I'm working on the laptop.
It's difficult because there's only one internet connection, so I have to unplug the modem from the desktop and plug it into the lappy.  Should I be booting my laptop with the internet plugged in?

I'll post up the results of dmesg if I can get my digital camera to work on Ubuntu. My lappy has a floppy drive but the family desktop (which I'm using right now) doesn't.  My lappy has just a CD drive, the desktop has a DVD burner.  Both computers have USB but I can't fit my pendrive into my lappy because the pendrive is too fat and the socket is sunk into the laptop, so you just bang plastic off plastic...

Thanks

Karl

---

### Post by mcduck on 2007-02-07
> **Bright Carver said:**
> Should I be booting my laptop with the internet plugged in?
That's the easiest way, and you also should have it connected when doing the install.. This way installer tries it's best to make the net work for you.

---

### Post by docshawnc on 2007-02-07
Hi Karl -
    This happened to me last night while doing a dapper install on a new laptop.  I answered 'no' to the firewire question as well and when the install finished, went to the system/network option on the menu, saw there was a wireless card there which was not active or configured, and configured in manually.  Works fine now

---

### Post by Bright Carver on 2007-02-07
Thanks for the help. :) 

I'm going to try connecting with a LiveCD (just to see if the card's working) and then I'll try a reinstall with the internet plugged in.

---

### Post by Bright Carver on 2007-02-07
Strange:

just had activity light on the modem and eth01 was in the system->admin->networking bit when I had it plugged into the USB, but I couldn't get it working.  Then after a reboot, it vanished and I haven't seen an activity light on the modem until I plugged it into my desktop again.

Looks like it's going to be too much hassle to connect to the internet :(

---

