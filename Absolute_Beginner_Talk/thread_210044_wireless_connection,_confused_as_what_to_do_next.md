---
title: "wireless connection, confused as what to do next?"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by ericmc783 on 2006-07-06
I have searched these forums and read through many threads and I feel like i am being told to do 3 or 4 completely different things. So i will start my own thread and see what your recommendations are.

I am attempting to use the Ubuntu Demo on Live CD. I have a wireless internet connection, Linksys 802.11B/G Router, and my PC has a built-in wireless adapter. My PC Is an [Averatec]("http://www.averatec.com/") 3700 Series. When I use liveCD, the Demo loads just fine and i must say it looks pretty cool. my only problem is, when I go into system > Administration > networking, and try to enable a wireless internet connection, the LiveCD freezes and i have to completely reboot my PC. 

Ive read that i should be using a utility called breezy, as well as some other utility with a weird oddball name, and a few other things. would anyone like to elaborate? thank you.

---

### Post by RaoulDuke on 2006-07-06
What you really need to know is what chipset your built-in wireless uses. Open a terminal and type in: lspci

In this list you should be able to determine which is your wireless. Then I would suggest googling your specific chipset to determine if there is already a linux driver out there for your card, or if you will have to use ndiswrapper.

---

### Post by Neobuntu on 2006-07-06
The Avertec 3700-ED1 reportedly uses the following:

The rt2500 kernel module from [http://sourceforge.net/projects/rt2400](http://sourceforge.net/projects/rt2400) 

...or use driver from Ubuntu Kernel.

As to your lock ups, you may have two driver/modules loaded for Wifi and/or DHCP may not be not finding a server and tries a long time.

You may need the Wifi switch "on" and/or set it up "always on" or not, in your notebooks "BIOS" startup settings. I realize there can be a chicken and egg thang, needing Internet to download but just direct connect it (or use a wireless bridge device if you want to stay wireless; now commonly called a "gaming adapter.")

In any case, yes, what does that lspci (after "Accessories > Terminal") tell us about the WiFi chipset?

Perhaps you need to install Ubuntu and settle in with a closer matching (Automagically installed) Ubuntu Kernel (with it's suport hopefully for your device; matching your better and auto installed Kernel (like a K7.) Ubuntu does an excellent job with multiple Kernel varitions so you don't have to. Just say go.

---

### Post by thedward on 2006-07-06
Add the DisableIRQ option to your video device in /etc/X11/xorg.conf:

```
Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
        BusID           "PCI:1:0:0"
        Option          "DisableIRQ"
EndSection
```

---

