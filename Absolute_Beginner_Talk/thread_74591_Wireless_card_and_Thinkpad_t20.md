---
title: "Wireless card and Thinkpad t20"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by whiterabbit on 2005-10-12
Hi,

I've been trying to get my Netgear WG511(version 2) 54 Mbps Wireless PC card to work with my Thinkpad T20 notebook and Ubuntu. :(

Hasn't been working out thus far.  

Can anybody give me a hand if you know how to get it up and running?  I'd really appreciate it.

---

### Post by Pathogenix on 2005-10-12
Mmmm... PCMIA wireless cards and linux.

A quick google says that your card should work fine with ndiswrapper, a wrapper for windows wireless card drivers. If you haven't got it installed, it's under the package manager and I've had no problems with my 3Com and the bundled version. 

Get your driver (the .inf file) off your manufacturer's disk or website and put it somewhere sensible on your linux drive.
open a root console and type

```

ndiswrapper -i mydriver.inf
ndiswrapper -l

```

ndiswrapper should install the driver and print something like 

```

	Installed ndis drivers:
	netwg511        hardware present

```

If so execute 
```

ndiswrapper -m
modprobe ndiswrapper

```

That should create an alias for wlan0 to your card and then load your new driver to control it.

If you're still going strong with no error messages execute
```

ifup wlan0

```

and you should be able to configure your network from the admin tool under the system menu.

If in doubt, google "ndiswrapper wg511" because NDISWrapper has a few peculiar quirks that have been the cause of much lost sleep both times I've installed a card under Linux.

---

### Post by whiterabbit on 2005-10-12
Thank you so much for that.  Worked like a dream.  :D

---

### Post by ProfBib on 2005-10-20
I am faced with the same problem (same card number) under Ubuntu 5.10, but the instructions did not work for me.  I installed the drivers (first step) without any problem, but when I typed in

ndiswrapper -l

I was told that I had installed an invalid driver.

Any suggestions?

Cheers,
Evan

PS - I have the "Made in Taiwan" version of this card (as opposed to "Made in China") that is, according to numerous posts on different forums, the one to have for use with Ubuntu and other flavors of Linux.

---

### Post by cblanquer on 2005-12-28
Some adds - I use a 3Com wireless PCMCIIA XJack 802.g card over a Thinkpad T21.
I had some trouble to configure wireless access. I used ndiswrapper with its windows drivers (easy to obtain from 3Com website) to get the card working but wireless link still was wrong.
I finally tried network-manager.
This worked partially: I must manually call for "sudo dhclient" to get the card obtain the internal IP addreess from the ADSL router. 
For several hours invested, I am not able yet to figure out what is wrong there. :???: 

Any hint to solve this ? :confused: 
THXalot

====================
I do not need to run "sudo dhclient" anymore, after a Breezy update that started working fine with the NDISWRAPPER driver - from my drivers CD - but I do not localise what exactly fixed the stuff !

---

### Post by valnar on 2005-12-28
Not to hijack the thread further.... but what is the procedure to _remove_ hardware supported under Linux?  I usually just end up reformatting and reloading Linux if I change a video card, NIC, sound card, etc.  In the NDISwrapper example, what would I do if I wanted to retire that said PCMCIA card?

Robert

---

### Post by FrankBlourtango on 2007-08-26
if you type just ndiswrapper it shows you all of the options.

do ndiswrapper -l to see the name of what is installed.  then ndiswrapper -r  xxxxxx to remove the driver.

---

