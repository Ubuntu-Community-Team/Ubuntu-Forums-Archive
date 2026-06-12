---
title: "Wireless Help"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by ihappen on 2007-02-14
I have a D-link Wireless netwrok adapter (DWL-G122) which I am trying to get to work under 6.06 Havnt a  clue how  to do this... As I'm new to compoutors and Unbuntu I'm afarid I'll need baby steps


many thanks!

---

### Post by oilchangeguy on 2007-02-14
ok, first let's make sure ubuntu sees your wireless adapter. go to system, administration, networking. you should see etho1 (nic card), wlan0 (wirless), and maybe a modem. check this and let us know.

---

### Post by ihappen on 2007-02-14
All I see Is Ethernet connection (eth0) and a Modem Connection (ppp0)

---

### Post by oilchangeguy on 2007-02-14
it seems ubuntu does not recognize your wireless card. do a google search of the name, model number, and put ubuntu in the search box also. and see if your adapter works with ubuntu.

---

### Post by banditti on 2007-02-14
can you also do a lspci from a terminal window and post?

---

### Post by JAS510 on 2007-02-14
I'm also having the same problem.  Gotta linksys with booster.  I'll be watching for this post :):popcorn:

---

### Post by ihappen on 2007-02-14
aparently Unbuntu supports my adapter 


this is the lspci readout:

0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
0000:00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
0000:00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
0000:00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
0000:00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
0000:00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:04:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by sympeltun on 2007-02-14
I'm not an expert in ubuntu, but did any one try using ndiswrapper? you can configure your wireless cards using the windows drivers (.inf and .sys)

hope this helps..

---

### Post by ihappen on 2007-02-14
How do I use ndiswrapper??

---

### Post by oilchangeguy on 2007-02-14
try this [http://www.hotubuntunews.com/blog_2.shtml](http://www.hotubuntunews.com/blog_2.shtml)

---

### Post by ihappen on 2007-02-14
Thats dosent seemed to have worked... any other ideas??

---

### Post by JAS510 on 2007-02-14
I loaded Ndiswrapper on my USB drive (using windows) Now i dont know how to run program from the USB.

---

### Post by jml on 2007-02-14
Getting a file downloaded from within windows to install and run in Ubuntu is possible, but is rather complicated.  I haven't tried to do it, but hopefully someone here may have.

If you have the option to connect your computer to the internet via a hard wired connection then I would suggest using synaptic to download and install ndiswrapper that way.  Then if you search the wireless sub-forum for the term ndiswrapper you will find numerous instructions for configuring the application.  In general terms you need to use ndiswrapper with the windows driver that came with your device, (its loaded on the install cd that came with your device.  If you don't have a cd, then you can download the driver from the manufacturers web site here:

[http://www.dlink.com/products/support.asp?pid=334&sec=0#drivers](http://www.dlink.com/products/support.asp?pid=334&sec=0#drivers)

When I checked the product specifications I noticed that it is a USB wireless device.  To be frank, Linux support for USB wireless devices is spotty at best and can be quite a challenge to set up.  Here is a link to a thread talking about installing a Linksys USB wireless device.  Some of the details will differ, but it may give you a flaver of what is needed to be accomplished.

[http://www.ubuntuforums.org/showthread.php?t=192588](http://www.ubuntuforums.org/showthread.php?t=192588)

You might also want to download and burn an iso of Ubunu 6.10.  It seems to do wireless better than Dapper Drake, and it might just be able to recognize your hardware out of the box.  Just run it as a live CD with your wireless adaptor plugged in and see if it is recognized from within the networking utility.  Good luck.  Also, you may get quicker aswers to your networking and wireless questions if you post them on the networking/wireless sub-forum.  

Joe

---

