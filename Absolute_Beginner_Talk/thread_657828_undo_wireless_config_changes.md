---
title: "undo wireless config changes"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Clinojim on 2008-01-04
I have an old Dell Inspiron 7000 that I've installed Ubuntu on.  My absolute first time using, installing, doing anything with anything Linux.  Ubuntu installed fine so I plugged in the Linksys WPC11 v4 PCMCIA wireless adapter that I had.  I put in the SSID and WEP key for my wireless network but I couldn't connect to the internet.  In the properties for the wireless connection I clicked on the option below static IP and DHCP (I don't remember what it's called now) and the mouse curser and keyboard stopped responding.  If I reboot with the card in the computer Ubuntu doesn't start, if I reboot without the card in it the computer boots up fine, but as soon as I plug in the card I lose control of the mouse and keyboard again.  Is there a way to undo the changes I made to the wireless configuration without actually plugging in the card?  Right now all I see is "modem connection" in the network settings, no wireless conection is visible (I assume because the card isn't in it.)

---

### Post by Yellow Pasque on 2008-01-04
> If I reboot with the card in the computer Ubuntu doesn't start
Any indication of where it stops or what stops it?

---

### Post by Clinojim on 2008-01-04
Nope, nothing ever shows up, the computer powers up, I see the bios startup screen, then a black screen that just sits there.  There are two LED's that start flashing above the keyboard, one is a picture of a lock with a capital "A" in it (I assume it's the caps lock) and the other is a lock with a downward pointing arrow.  When I first clicked on the wrong wireless option that locked up the controls in the first place those two started flashing.  I assumed I had accidentally hit caps lock or some FN key combo or something, but no combination of the FN key and anything else would make them stop flashing and give me back control, the only solution was rebooting without the card in it.



/edit: also, if I boot up without the card in it, then stick the card in after ubuntu has started the two LEDs start flashing and I lose control of the keyboard and mouse.

---

### Post by Clinojim on 2008-01-04
I did a fresh install and reinput all the ssid and wep stuff, and set it to dhcp, no go.  So I tried assigning it a static IP and the same thing happened, capslock and that other LED started flashing and I lost control of the mouse and keyboard.  I also noticed that while the power LED on the card was always lit, the activity LED lit up with I told it to use a static IP, but again, no keyboard or mouse.

---

### Post by Clinojim on 2008-01-04
So I did a bunch of searching here last night and found options to try today, one being to revert to an older version of Ubuntu (supposedly 6.10 works) or to try using windows drivers with 7.10.  I also read that someone said their WPC11 worked fine with a live CD but not with it installed to the HD.  Unfortunately that didn't work for me.  I'll try the other options tonight.

But the main question I have still remains, if I do something that locks up Ubuntu when the card is in, is there anyway to undo those changes without having  the card in so that I can try a different configuration *without* having to reinstall?

---

### Post by poklebery on 2008-02-18
I am experiencing exactly the same symptoms though in my case it is a netgear ma521 wireless PCI card.
But I also get complete lockup and flashing caps lock/num lock combo. I followed roughly the same process, installed Ubuntu 7.10, set up wireles with wep, and the first time the connectuion light came on on the card Ubuntu froze.
Since then I have gone down the ndiswrapper route, but as I have to remove the card and use a wired connection to use the PC, I can't get anywhere. I have tried blacklisting the open source driver to no avail.
What I really want to do is work out which driver Ubuntu is trying to use with the card, but as I can't have the card in when Ubuntu is running that is kind of tricky.
PLEASE HELP!

---

