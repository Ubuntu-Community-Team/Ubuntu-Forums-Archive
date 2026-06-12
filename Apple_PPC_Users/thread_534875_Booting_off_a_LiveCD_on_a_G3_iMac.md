---
title: "Booting off a LiveCD on a G3 iMac"
date: 2007-08-25
forum: Apple PPC Users
---

### Post by sionnachdrum on 2007-08-25
Hi there

Been mosing around the forums but can't seem to find anyone having the same problem as me. I just can't get the machine to boot from CD.

I have a 500Mhz G3 iMac, slot loader.  I got it second hand and Tiger 10.3.9 is installed on it with all the latest updates.  I've burned about 5 LiveCDs off the net - Ubuntu 6.06 and 7.04, PowerPC versions.  Two of these have been burned on a PC, three off my Macbook.  When it comes to booting, either one of two things happen: (1) I press down the Command key and up comes the boot menu.  But I can't select the CD to boot from.  It just hangs there and after a while boots from the hard disk.  or (2) I press down the command key and the CD is ejected.

I'm getting a bit fed up of having to continually burn LiveCDs.  Any help as to get Ubuntu installed on this machine would be much appreciated.

---

### Post by bodycoach2 on 2007-08-25
While someone may have accomplished this feat, I've never gotten a LiveCD to boot on a G3. It may have more to do with the amount of RAM than the processor speed.

You'll probably be able to get an alternate install CD to work on that machine. I'd also recommend Xubuntu on a 500 MHz machine. And, the CD must be burned at the slowest speed possible.

---

### Post by sionnachdrum on 2007-08-26
Hmm.  Ok - have you been able to *boot* the CD though?

What happens is that the boot menu comes up with the hard disk and the CD with a Linux Penguin.  But I just can't select the CD.  My problem is I can't even select the CD to try to boot it.  Is that what you have also experienced?  Or is it that once you get past the boot menu it falls over?

---

### Post by Auria on 2007-08-26
See PPC FAQ:
[https://wiki.ubuntu.com/PowerPCFAQ#head-def39b758fa5328bd61aaead82e4c0588b4a4f70](https://wiki.ubuntu.com/PowerPCFAQ#head-def39b758fa5328bd61aaead82e4c0588b4a4f70)

it does not look like your issue but it talks about iMac G3... and yeah you should try the alternate CD 

> 
have you been able to *boot* the CD though?

> 
I've never gotten a LiveCD to boot on a G3


:D

the alternate CD doesn't offer you to try the system first, but installing will surely work better even though it's not as nice

---

### Post by no-w-ay on 2007-08-27
I had to use the Disk Utility of Apple in order to burn a Live CD that would accept to boot on my iBook G3 500MHz. Toast Titanium would burn non bootable CDs for some reason.

---

### Post by Vincent_Lin on 2007-08-28
I purchased a 333MHz iMac off craigslist ($30) and installed xbuntu 7.04 onto it.

1. This machine has 192MB memory, so I chose xbuntu.
2. I boot this machine off CD by pressing "C" key while it boots, and it finds the CD to boot from.
3. LiveCD could never boot to its full glory.  So I use Xbuntu alternative CD.
4. Even eventually xbuntu installs, it still runs very slow.  Guess I am used to Centrino performance too much.
5. I plugged in a 54G USB stick (can't remember the brand at this moment), and xbuntu recognizes this wireless card without instance, and hops into my home wireless base right away.
6. Gnash and mozilla plugin installed, so flash works.  Except the performance is badddd.
6. So, my 4 years old daughter can draw some funny pictures using tuxpaint.  But pbskids online games are running too slow, and she does not play them on this machine at all.  She still likes my Thinkpad for "online gaming".  Ha!

That's my experience with ubuntu on iMac.

Vincent

---

### Post by bodycoach2 on 2007-09-01
> **Vincent_Lin said:**
> 
5. I plugged in a 54G USB stick (can't remember the brand at this moment), and xbuntu recognizes this wireless card without instance, and hops into my home wireless base right away.
Vincent

What brand 54G USB stick is it?

---

### Post by EuroCity on 2007-09-01
One of my computers is an old Bondi Blue G3 iMac and it only accepts CD-R media (burnt at slow speed) as bootable; CD-RWs don't work, strangely.

So the oldest models seem to have this problem in common; not sure, however, if it also affects the more recent slot-loading G3 iMacs: probably not...

---

### Post by Vincent_Lin on 2007-09-15
Hi,

Sorry I reply this late.

My USB 54g network card was made by Hawking.  Don't know the model, nor the chip.

I could not find the receipt either.  Guess what?  I bought a Motorola usb 54g stick from Compusa, but when I went to pick it up, they claimed that it is no longer in stock.  So they gave me this stick instead.  

I tried it first on a Pentium machine under ubuntu 6.10 and it worked.  So I was confident to simply plug it into my iMac.  and it works.

What can I run to get you some more information about the chip or any info you need about this usb 54g stick?

Vincent

---

### Post by stmiller on 2007-09-15
Hey Vincent:

Install the program hwinfo
```

sudo apt-get install hwinfo

```
then with your wireless card plugged in, run that program at the terminal
```

hwinfo

```

You should find a little blurb about your wireless device somewhere, which will include its chipset and driver being used.

---

### Post by Vincent_Lin on 2007-09-15
There you go.

The last entry of hwinfo:

6: None 01.0: 10701 Ethernet
  [Created at net.119]
  UDI: /org/freedesktop/Hal/devices/net_00_12_0e_04_2b_31
  Unique ID: L2Ua.vnwWAn0UAo4
  Parent ID: mQbf.GXIudaGXul4
  SysFS ID: /class/net/eth1
  SysFS Device Link: /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "zd1211rw"
  Driver Modules: "zd1211rw"
  Device File: eth1
  HW Address: 00:12:0e:04:2b:31
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #27 (Ethernet controller)


It's always good to lern new stuff.

Thanks.

vincent

---

### Post by garlicsalt2 on 2007-09-16
Well what do you know, another zd1211 chipset. It's called a Zydas zd1211. Great chipset. Originally make by the Zydas company in Taiwan, the company was bought out by Atheros.

I recently bought a WiFiMax, which uses the same chipset, as does the Belkin F5D7050 Rev. 4.

Enough ranting about the USB WiFi dongle.

I just wanted to mention that I got Ubuntu working on a Blue and White G3 @ 300 MHz. As mentioned in a previous post, you must hold down the "C" key, for (C)D-ROM, not the option or command key, to boot from the CD.

Oh, and if you can't make a CD yourself, try getting one of the free CD-ROM that Ubuntu ships out for free!! That's what I did. I've had the CD for quite some time, just in case it ever came in handy. I just got the G3 on Thursday.

Since it had only 128 MB of RAM, it was rather tricky getting Ubuntu installed in the first place. I had to boot an old version of Ubuntu (Breezy Badger) - which ran in text mode. From there, I had to partition and format the Hard Drive, and set-up the swap partition, and then boot into Dapper, and do a manual partition, being sure not to format the swap partition, which was auto-detected and mounted for use by the install CD.

I now have trouble running X-Windows, but the command-line interface works a charm!! X-Windows works faster than I thought it would under the circumstances, however. It helps, though, that I disabled cups, hplip, bluetooth/bluez, mdadm, and some others. I always run sshd though, just in case.

About the only thing I haven't yet figured out, is how to switch Virtual Consoles while I'm inside X. Outside of X, I just press, option with the left and right arrows. On a PC, it would be Alt-F1 through Alt-F6, or Alt-F7 to get back to X-Windows/Gnome. My ADB keyboard doesn't have any F-keys though. I suppose I could open a terminal, and run "sudo chvt 1", if I was desperate enough.

Oh, well, good night!

---

### Post by Cael on 2007-09-17
not sure if you have fixed this prob yet but sounds like teh same prob i have w/ making them boot cd's period

restart your mac and Hold in the (~) icon till it loads teh Open Firmware.

type this in to get it to boot the ubuntu cd.

**boot cd:,\\:ttbxi** its a prob w/ the firmware of your cd/dvd drive and its a known prob with Apple, as it affects even any OS X install cd

---

