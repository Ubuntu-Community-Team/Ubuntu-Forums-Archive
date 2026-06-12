---
title: "Wireless connection problem"
date: 2007-08-21
forum: Apple Intel Users
---

### Post by Davey8000 on 2007-08-21
I recently installed Ubuntu 7.04 on my Macbook (Core Duo, 1.86 ghz) and everything went smoothly until I went to connect to my wireless network. The name of my network appears in the list of wireless networks (when I click the network option in the top right corner) and I entered my WEP password correctly, but I am still not able to connect... I don't believe it is a hardware issue as the airport card is picking up the surrounding networks.

I apologize if the above isn't specific enough, if you need screenshots I will be happy to take them. This is my first venture into Ubuntu, so I'm not quite used to how some things work...

Thanks.


Note: In case it makes a difference, I have Ubuntu and Mac OS X on my computer and switch between them using Boot Camp.

---

### Post by moore.bryan on 2007-08-21
[I]let's find out more details about your wireless card; what are the outputs of:
```
lscpi
iwconfig
```
?[/I]

---

### Post by Davey8000 on 2007-08-21
iwconfig gave me:

Lo- Nothing
eth0- Nothing
wifi0-Nothing

ath0 gave me a bunch of info about my router and my network, but clicking 'properties' gave me a message saying that the device was not supported.

The lscpi command didn't work, what does it do exactly?

---

### Post by cyberdork33 on 2007-08-21
> **Davey8000 said:**
> iwconfig gave me:

Lo- Nothing
eth0- Nothing
wifi0-Nothing

ath0 gave me a bunch of info about my router and my network, but clicking 'properties' gave me a message saying that the device was not supported.

The lscpi command didn't work, what does it do exactly?

Should be lspci. No matter, you have an atheros based wifi card. I would suggest madwifi.

---

### Post by Davey8000 on 2007-08-21
I was going to try to extract the bcm43xx FW to see if that would work, but I can't boot up because of a kernel panic:

Not syncing: IO-APIC + timer doesn't work!

...and then tells me to boot up in 'noapic' mode.

I didn't change any settings the last time I booted up Ubuntu. If anyone needs to see exactly what happened I can boot up in recovery mode and write down where everything failed, it's just kind of a pain to switch between OS X and Ubuntu :)

---

### Post by benanzo on 2007-08-21
Just ignore the kernel panic at boot - that seems to happen periodically but if you do a hard reset and try booting again it will probably boot fine.  No need to mess with the kernel boot options unless it happens *every time* you try to boot.

Is this a newer MacBook with a Core 2 Duo processor?  or and older one with a Core Duo?  It matters because the madwifi drivers that ship with Ubuntu Feisty don't support the newer chipset (I think).  I imagine you're running a first-gen MacBook because NetworkManager is working fine (ie you can see networks.)

Don't mess with the bcm43xx stuff, that's only necessary if you have a Broadcom wireless chip, which you don't.  I imagine you're just having a problem authenticating to your network due to a misconfiguration in the WEP options menu of NetworkManager.

You can see what's going on by doing these steps in a terminal (Applications -> Accessories -> Terminal):

Kill Network Manager:
```
sudo killall NetworkManager #then enter your root password
```
Wait for the NetworkManager icon to disappear from the Notification Area (by the clock) then do:
```
sudo NetworkManager --no-daemon
```
This will restart the network connection except it will print everything it's doing in the terminal.  Try to connect to your network while watching the terminal for errors.  Post the output back here.  You can stop it by either closing the terminal or hitting CTRL-C.

To restart it without requiring that the terminal be open do:
```
sudo NetworkManager
``` then close the terminal and everything will be normal.

---

### Post by moore.bryan on 2007-08-21
> **cyberdork33 said:**
> Should be lspci. No matter, you have an atheros based wifi card. I would suggest madwifi.
*yeah, sorry about the typo... madwifi should be the way to go.*

---

### Post by Davey8000 on 2007-08-22
It's giving me that same error everytime I try to boot. I have a Core Duo, the first gen.

---

### Post by shivathreya on 2007-08-24
use the boot option "noapic" in the grub prompt. Just edit in the boot prompt and add noapic at the end.

It should boot.

madwifi sucks. Try NDISWRAPPER. I have attached the windows drivers which I use with ndiswrapper.

Shiva

---

### Post by moore.bryan on 2007-08-24
> **shivathreya said:**
> use the boot option "noapic" in the grub prompt. Just edit in the boot prompt and add noapic at the end.
*shouldn't that be "noapci"?*
> madwifi sucks. Try NDISWRAPPER.
*why the hate on madwifi?  ;-)*

---

### Post by cyberdork33 on 2007-08-24
> **moore.bryan said:**
> *why the hate on madwifi?  ;-)*
Yea, I always thought madwifi was a pretty good package.

---

### Post by benanzo on 2007-08-24
I can't attest to Madwifi's quality on other wireless chipsets, but for the Atheros AR5006EG chipset, which is in the first-generation MacBooks, it works really well.  The one problem I do have with the Madwifi version in Feisty is that the driver doesn't interpret the signal strength from the router very accurately, so I get (at best) three bars from my router while standing about six feet away.  I get four bars with the latest Madwifi SVN code (and that's connecting through a floor and two walls.)  I'm also really impressed with how the bcm43xx code has matured (and so quickly.)  I have another machine that uses a Linksys WPC54Gv2 wireless card with a Broadcom chipset and it works out of the box on Feisty with great signal strength and quality.

I've never been much of a fan of NDISWrapper's performance, but it's a great project none-the-less.  If given the choice, I go for Madwifi (for Atheros) or bcm43xx (for Broadcom).

---

### Post by macaholic on 2007-08-24
Just wanted to add something, that not all broadcom chips work with bcm43xx, for example the 4328, which is in some core 2 iMacs and all Mac Pros w/ wireless, in which case your only option is NDISWrapper.

---

