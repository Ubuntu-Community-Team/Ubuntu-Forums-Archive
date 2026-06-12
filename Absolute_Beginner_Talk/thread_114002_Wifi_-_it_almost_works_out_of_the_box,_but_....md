---
title: "Wifi - it almost works out of the box, but ..."
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by Steff_DK on 2006-01-07
After having installed Breezy, my PCMCIA card for wireless internet was present as eth1, and I could find my SSID "in the air" from the wireless router ...

However when I open Firefox it just hangs, and never finds google.com

Searched the forum, and here was some info that I think I have to provide for someone to help me:

Ran lspci -v and got:
```
0000:02:00.0 Network controller: Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (rev 01)
        Subsystem: Netgear: Unknown device 4800
        Flags: bus master, medium devsel, latency 80, IRQ 9
        Memory at 08800000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>
```

After that I unplugged the card, and then re-inserted it. Then ran dmesg:
```
...
[4294723.821000] eth1: resetting device...
[4294723.821000] eth1: uploading firmware...
[4294724.029000] eth1: firmware version: 1.0.4.3
[4294724.029000] eth1: firmware upload complete
[4294724.263000] eth1: interface reset complete
[4294724.293000] NET: Registered protocol family 17
[4294786.595000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[4294792.889000] NET: Registered protocol family 10
[4294792.889000] Disabled Privacy Extensions on device c02eb280(lo)
[4294792.890000] IPv6 over IPv4 tunneling driver
...
[4294803.141000] eth0: no IPv6 routers present
[4294803.206000] eth1: no IPv6 routers present
...
[4294881.131000] eth1: timeout waiting for mgmt response 1000, triggering device
[4295856.220000] eth1: hot unplug detected
[4295856.220000] eth1: removing device
[4295856.220000] eth1: islpci_close ()
[4295856.381000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[4295868.175000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[4295868.175000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKB] -> GSI 9 (le vel, low) -> IRQ 9
jesper@ubuntu:~$

```

Does anyone have a clue why I can't get online wireless???

Thanks all ;)

---

### Post by Derek Djons on 2006-01-07
Since it worked 'Out of the Box' for me I can't really deal with the commands you've executed in the terminal. My advice is to check the next settings (properties of your network connection):

1. See if there is something in the 'Host' tab. If not, than you can't even reach your Modem / Router.

2. Check wether there is a DNS address filled in! Sometimes Ubuntu get's that far but it doesn't always succeed in copy - pasting your Modem / Router's DNS Address. This results in being able to ping websites but not actually find them (using a browser) since the URL of a website isn't being resolved into a ip-address.

Hope I've helped you a bit.

[edit] - took care of some serious grammer problems :) [/edit]

---

### Post by poofyhairguy on 2006-01-07
You need network manager. 

Install with this command:

```
sudo apt-get install network-manager
```

Use with this command:

```
nm-applet
```

---

### Post by dotdot on 2006-01-07
try this

[http://ubuntuforums.org/showthread.php?t=70642](http://ubuntuforums.org/showthread.php?t=70642)

worked for me ...

..

---

### Post by leonneku on 2006-01-07
Hi,

I had also the problem with wifi a few months ago when i had Suse installed.
I had disabled the networkcard in my laptop and then the wifi card was working.

Leon

---

### Post by Steff_DK on 2006-01-07
I am presuming this is a router problem since I just successfully and "accidentally" :rolleyes: connected to someone else's unprotected network in the vicinity  ...

What do I write where it says DNS addresses?

---

### Post by Steff_DK on 2006-01-07
Greetings all!

Writing to you over the air ways :smile: 

Deleted the accesslist MAC addresses and WEP password, and reinstalled them - then it worked - no clue why ...(but who cares when it works)

One last simple task:

How do I add the network manager to the boot sequence so I dont have to write 'nm-applet' after i start the laptop?

---

### Post by el toro on 2006-01-07
Add it to your gnome-session:
System > Preferences > Sessions > Startup Programs
Hit "Add" and type in "nm-applet".  That should sort it.

---

### Post by Steff_DK on 2006-01-07
Indeed that did it! :D 

However it asks for a 'keyring' password because network manager (nm) is trying to access something when it starts.

Is there some place to switch this off, or enter it once and for all?

---

