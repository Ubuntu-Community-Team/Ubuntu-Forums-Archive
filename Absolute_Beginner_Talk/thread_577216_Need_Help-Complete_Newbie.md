---
title: "Need Help-Complete Newbie"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by scurvy on 2007-10-16
Two problems:
1. Would like to get online with laptop running 704, via cable modem.  problem seems that an IP is not being assigned

2. Seems to be a common problem, my ATI rage mobility m3 resolution won't go any higher than 800x600.  attempted fix from a posted solution, but unsuccessful. using Thinkpad A21p.

Anyone live in Toledo?  Anyone Make house calls?  I can pay with home brew beer.

J

---

### Post by overdrank on 2007-10-16
> **scurvy said:**
> Two problems:
1. Would like to get online with laptop running 704, via cable modem.  problem seems that an IP is not being assigned

2. Seems to be a common problem, my ATI rage mobility m3 resolution won't go any higher than 800x600.  attempted fix from a posted solution, but unsuccessful. using Thinkpad A21p.

Anyone live in Toledo?  Anyone Make house calls?  I can pay with home brew beer.

J

Hi and welcome, I am not much on networking but are you sure the nic card is working? Also have you reset the modem?
As for the resolution this link will help
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
And set your default depth under screen to 16 has help out users with that graphics.
Thanks for the offer of free beer though! :KS

---

### Post by xpod on 2007-10-16
> Anyone live in Toledo? Anyone Make house calls? I can pay with home brew beer.

:)
Welcome.
Is your cable modem usb or ethernet.Are you also using a router???
If it`s an ethernet cable modem connected direct,using a dhcp assigned ip address then you really should`nt need to do too much.I `m able to use both USB or ethernet so i know Ubuntu has some possibilities with usb "out the box" but USB can be more problematic for some.

You can check that your network card is available....and set to DHCP(?) in the network manager within your system menus or by clicking the nm-applet on your top panel(?)
You can also check your network card is at least showing up/getting ip address by going to the terminal in your apps menus and typing
```
ifconfig
```

That will show all network cards & the relevant info.Similar to ipconfig in windows
Mabey a reboot allround might help though and make sure all connections are good..??

---

### Post by scurvy on 2007-10-18
Hey thanks, eventually got on by hitting the reset button on the modem. Powering it off and on didn't reset it enough apparently.

stilling trying to figure out the deal with my video.  Will have to wait unitl 710 upgrade is complete.

cheers!!

---

