---
title: "Help w/ basic networking"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by shaunuel on 2007-01-16
Hi folks, 
I've just gotten out of a long and serious relationship with Microsoft, but in the end, we decided that it was best to part ways and just stay friends. On that note, I've recently installed Ubuntu as my second shot at linux (wasn't diggin' the Mandriva One KDE release). Thus far, I've found it quite enjoyable, I even installed my nVidia drivers via the command-line (a milestone for me). Anyway, I'm having some trouble setting up a network here in my home. Here's all the pertinent info: 

I have a Linksys WRT54GC 4-band router and I want to set up a home network. To this network, I want to be able to connect my laptop which is currently running WinXP Home (SP2), w/ wireless internet.  When I try using the Network Accessory, hook everything up, and restart, I cannot see the network via the Windows Wireless Network Detector utility, nor can I access the internet here, on my Ubuntu 6.10 (edgy) install.  

Can someone point me in the right direction with regards to this issue? I've searched around a little but haven't been able to dig up anything aside from Samba inquiries.  I'm sure its easy as pi and I'm just overlooking something. So in advance, thanks for any and all advice. 

Regards, 
shaunuel

---

### Post by riven0 on 2007-01-16
Can you tell us what is the make and model of your wireless card? You may need the drivers for it.

---

### Post by shaunuel on 2007-01-16
Hey, 
riven0, the wireless card is on the laptop (WinXP), it'd be connecting wirelessly to the network that I'll setup w/ Ubuntu. Would it need drivers? In any case, it's a Broadcom 801.11b/g WLAN installed in a Compaq Presario V5000. WinXP driver 3.140.16.0. Thanks for the help, and quick reply. :) 

shaunuel

---

### Post by redcow on 2007-01-16
I too just recently installed Ubuntu.
I however was able to get networked with out doing anything. Also my two printers (LJ 4000 using lpt1 and a jet direct connected Photosmart 7960) were working.

The next day we had a powerfailure which took down my systems. When I rebooted the Ubuntu machine I came up with CRC errors that wouldn't clear. I had to reinstall Ubuntu.

Now like you shaunuel, I have no network and no printers. The printers are working on my XP machines.

---

### Post by riven0 on 2007-01-16
Ahhh, the infamous Broadcom card. No wonder your not connected. You'll not only need a driver, but you'll need ndiswrapper, too. 

You didn't mention the model no. of your card, but I'm guessing you have the most popular type: 4318. In either case, [this howto should get you up and running]("http://ubuntuforums.org/showthread.php?t=197102&highlight=Broadcom"). Make sure you follow it step by step. If you run into any problems, post here again. Not sure if I can help, but I'll certainly try.

---

