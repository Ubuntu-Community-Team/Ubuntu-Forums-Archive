---
title: "Ralink card and ndiswrapper"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by .oops on 2007-03-18
I'm under a wireless network on windows, and I wanted to get it to work in Ubuntu, but since my Ralink card (chipset rt61 or rt2500, I don't quiet know) doesn't run out of the box, I have to get ndiswrapper or something to get it to work. However, I don't have a ethernet connection, so to install anything, I have to go on a wild dependecies chase, and, I don't have a DVD recorder, so no massive packages offline repo for me. I'm clueless here, can someone help me out?

---

### Post by ieee488 on 2007-03-18
Just a suggestion.
Write a more descriptive Title for this thread then you might get more help with your specific problem.

Otherwise, it sounds just like another post complaining about Ubuntu, and some people are going to bypass it.

---

### Post by shammon on 2007-03-18
this is what i used to get my ralink usb wireless adapter to work.

iwconfig  --wireless status

sudo iwconfig <device name> essid "SSID" -- sets the SSID for current session
sudo iwconfig <device name> key "WEP KEY" -- sets the WEP key for current session

sudo dhclient <device name> --initiate dhcp connection

in my case the device name was rausb1

if this works it will be for your current session, there is a network configuration utility under administrator or system that you can put the settings in to make it permanent as to when you login, but i currently don't have access to my ubuntu installation.

---

### Post by dstew on 2007-03-18
Hi .oops. The ndiswrapper utility is on your Ubuntu distribution CD. You can install it from there, using Synaptic or Add/Remove Programs.

---

### Post by .oops on 2007-03-18
Won't the native linux drivers work? I tried ndiswrapper before, but after rebooting I wasn't able to boot anymore, it just got stuck in Configuring Network Interfaces.

---

### Post by dstew on 2007-03-18
There are native drivers available. I see source packages in Synaptic (Networking Universe repository). They are small downloads. They depend on gcc, but you can install the compiler from the Ubuntu distribution. The Ralink web site has downloadable drivers.

---

### Post by .oops on 2007-03-18
I don't have a ethernet connection. Does gcc and all of it's dependencies come with the CD?

---

### Post by TheMono on 2007-03-18
Yes. If you install the package build-essential, which is on the CD, then you have GCC and everything else important.

---

