---
title: "HELP  ~.~.~.~  Wireless Network Card"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by smiley1213m on 2006-07-18
****I'm trying to install as wireless network card that I originally bought for use with XP. Now we don't need it for that computer, and I'd like to use it on Ubuntu. I'm a super-new beginner, and have hardly gotten started with Ubuntu. **If someone could please help me out, with step by step instructions for a beginner it would be awesome**. The card is a  Linksys 2.4 GHz Wireless - G PCI Adapter. It also sayss "Designed for Microsoft Windows XP" Here's a picture of the one I have.

[IMG]http://www.axiontech.com/product/images/3/34103/34103_M.jpg[/IMG]

---

### Post by Metacarpal on 2006-07-18
The model number on this is WMP54G, right?
Looking at the [wireless hardware support page]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), this is a supported device.

Go to your System menu, Administration, and Network Devices.  Is your card shown there (probably appears as "ra0")?

---

### Post by smiley1213m on 2006-07-18
Great, ubuntu won't even boot up now, it gets stuck on Configuring Network Interfaces, and won't get off it.

---

### Post by Trizik on 2006-07-25
I have a very similar card, but mine has RangeBooster (WMP54GR)

Ever since I activated it, Ubuntu hangs at "Configuring Network Interfaces..."

This seems to be a pretty big problem, lots of posts about it. I tried Ctrl+C and allowing Ubuntu enough time to timeout and load past the dark orange/mouse cursor screen, but after about an hour I figured nothing more was going to happen.

---

### Post by mdecler2 on 2006-07-25
Press ctrl-c to escape the "configuring network interfaces" on boot-up for now.

I haven't figured out how to get Ubuntu to boot wireless yet.
If you are planning on configuring your wireless card, I used ifconfig quite a bit, so you are going to want to read the man pages on that.

Im sorry I can't be more specific, I have this written down on my home computer...right now I am supposed to be working :D.

---

### Post by Trizik on 2006-07-26
I think my problem is a tad different. I made a new thread to focus on my exact problem @ [http://www.ubuntuforums.org/showthread.php?p=1301594](http://www.ubuntuforums.org/showthread.php?p=1301594)

Any help would be greatly appreciated!

---

