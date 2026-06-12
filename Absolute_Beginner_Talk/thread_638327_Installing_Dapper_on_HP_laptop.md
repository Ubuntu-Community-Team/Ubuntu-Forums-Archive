---
title: "Installing Dapper on HP laptop"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by mrgordonz on 2007-12-11
Hi Fellow Linux People,

This is going to be a bit of a rambly post, so please forgive me if I waffle a bit too much.

I have been a Windows user for many years, and moving away has always seemed a little daunting.  Lately I had the opportunity to buy, setup and manage a server which is being co-located in a data centre.  I opted to use Ubuntu Server 6.06, and found the whole experience pretty rewarding.  A few years ago I dipped my toes in the Linux waters by running Fedora Core 2 for a while, but for work purposes found it a bit too restrictive - for example, the company used MS Exchange.

I am now self employed, and don't have those restrictions.  And after the success of getting the server setup, I have decided to switch to Ubuntu for my laptop.  It is a HP Pavilion dv6000.  It has AMD Athlon X2 dual core CPU; 2 GB RAM; 250 GB SATA HDD; nvidia graphics (not sure which); broadcom wireless.  I actually removed the original 80 GB HDD that had Vista Premium, and put in the new 250 GB HDD.  At least this way if I need to get back into Windows, it is just a case of swapping the HDDs.

My first question is regarding partitioning.  Seems there are a lot of opinions about what is the "right" or "best" thing to do when setting up one's partitions.  I won't ask what is the best partition setup, because I am bound to get twelve different opinions (which is fine - having different opinions is a great thing).  Instead, here is what I actually did.

/ (root)   30 GB
/home   218 GB
swap    2 GB

Can anyone see any problems with that configuration?

My second question has to do with the laptop itself.  I have been scouring the net for information about installing Linux on a HP dv6000, and the one thing that keeps popping up is a problem with "APIC".  I found one site, [https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)), which has some good info on it.  When I ran the installer, it froze until I changed the boot options to include ```
noapic nolapic
```

What is "APIC"?  By including the above boot options, am I disabling certain features of the laptop?  Is it going to cause me problems later on?

The install has just finished, and seems to have gone very smoothly.  I have logged in, and I can browse the internet (yippee!).  But I am still curious about this APIC thingy.

I am now going to see if other stuff works - wireless ethernet, CD/DVD writer, USB ports.  Already it appears that the touchpad doesn't work.

Cheers,

Paul

---

### Post by Threbus5 on 2007-12-12
Hi,

Welcome to laptop Ubuntu.

Regarding APIC - see [http://en.wikipedia.org/wiki/Intel_APIC_Architecture](http://en.wikipedia.org/wiki/Intel_APIC_Architecture)

A scan of that site appeared to indicate that disabling APIC, as you did, results in a Linux usable system. But read the site for detail.

I found that my Vista compatible laptop (although it arrived with Vista home premium, Ubuntu now resides there) behaves differently from an older laptop that came with XP pre-installed. Certain features on the newer laptop fail - in my instance microphone audio fails for Ubuntu. Perhaps the differences result from driver incompatabilities?

Regarding partitioning - according to [http://www.linux.com/base/ldp/howto/Swap-Space-7.html](http://www.linux.com/base/ldp/howto/Swap-Space-7.html) your swap size is ok.  A 30 Gb root directory seems a bit large. But, with 218 Gb for /home so what? I usually accept the installation defaults.



Have fun.

---

### Post by mrgordonz on 2007-12-12
> **Threbus5 said:**
> Welcome to laptop Ubuntu.

Thanks!  It seems to be a big family.  Hopefully not too dysfuunctional. :)

> **Threbus5 said:**
> I usually accept the installation defaults.

I thought about it but a lot of the stuff I read indicated that having a separate /home partition could be useful from the perspective of re-installing if something happened to the / partition - at least my personal stuff would be unaffected.

I read the Wiki article - thx for the link.  The bit that was of most concern was this:

**[FONT="Courier New"]In Linux, problems with I/O APIC are one of several causes of error messages concerning "spurious 8259A interrupt: IRQ7.". It is also possible that I/O APIC causes problems with network interfaces based on via-rhine driver, causing a transmission time out.[/FONT]**

I hope it doesn't affect my wireless network adapter.  As I mentioned in my opening post the install is complete and seems to have gone quite smoothly.  I have since swapped the drives again so I can use Windows to inspect my hardware and get the makes and models of all the bits and pieces.  I did notice while I was booted into Linux, however, that the touchpad didn't work (Synaptics PS/2 Port TouchPad), and when I flicked the switch on the laptop to turn on the wireless adapter, the LED stayed orange (under Windows it changes to blue).

Anyway, it will be an adventure to see if I can get everything working.  I also need to convert about 3 GB of Outlook PST files into a format that can be read by a Linux-based mail client.  Speaking of which - can you recommend a good mail client?  I noticed that there is one called Evolution in Ubuntu.  Is it any good?  I am used to Outlook, and at the risk of raising the ire of the MS haters, I have to admit I very much like Outlook.

Cheers.

---

### Post by beniwtv on 2007-12-12
Hey mrgordonz,

I also have a laptop form the dv6000 series - a dv6106eu.

Like you, my laptop freezes in console mode (which is the alternate installer). 

However, once everything is configured, all hardware works fine.

As for the WiFi, you might either have to install the firmware for the linux native wifi driver, or install the Windows XP driver (I use the XP driver, as the native one is not stable for me).

Also, the touchpad not working could be because of the ACPI switch. Did you try booting the installed system without these options?

NOTE: You might want to install the Nvidia proprietary drivers, if I try to use the nv (opensource) drivers, the laptop always hangs at starting X.

If you need more informations, don't hesitate to ask.

Hope this helps.

---

### Post by shadow-of-sin on 2007-12-12
> **mrgordonz said:**
> 
[B][FONT="Courier New"] Speaking of which - can you recommend a good mail client?  I noticed that there is one called Evolution in Ubuntu.  Is it any good?  I am used to Outlook, and at the risk of raising the ire of the MS haters, I have to admit I very much like Outlook.

Evolution is a good client (I like it due to its tight integration with GNOME) however it does have its disadvantages (for example if you have more than one email address by default all mail will go into one folder unless you setup filters for each address). Another client you could consider is Thunderbird- but it has less integration with GNOME.

---

### Post by mrgordonz on 2007-12-12
Progress update:

Took a bit of searching but I found a very nice way of getting my NVIDIA GeForce Go 6150 display adapter to work - Envy.  Worked a treat.  Now I can enjoy the full 1280 x 800 resolution, rather than the crappy 1024 x 768.

And for some reason the touchpad is working now.  Go figure.  I did apply all the updates that Ubuntu told me were available, so maybe that fixed something.

Next on the agenda is WiFi.  When I execute ```
sudo /etc/init.d/networking restart
```
I get the following:
```

 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:1b:24:66:9e:df
Sending on   LPF/eth0/00:1b:24:66:9e:df
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:1b:24:66:9e:df
Sending on   LPF/eth0/00:1b:24:66:9e:df
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 10.1.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.1.1.1
bound to 10.1.1.2 -- renewal in 73387 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

```
My laptop uses a Broadcom 802.11b/g WLAN (BCM4311)

When I execute ```
lspci | grep Broadcom
```
I get this:
```
0000:03:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 02)

```

I'll do some searching to see if I can find a reliable way to get this working.  If anyone has any suggestions ...

---

### Post by beniwtv on 2007-12-14
Hey mrgordonz,

As for the dhcp probelm, I think there's something messed up with your /etc/network/interfaces file.
There seems to be adapters which seem not present.

Can you give us the output of these 3 commands?

```
cat /etc/network/interfaces
lsmod
dmesg
```

With them, we might be able to see what's going on.

---

