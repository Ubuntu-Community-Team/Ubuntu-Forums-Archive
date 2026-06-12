---
title: "[SOLVED] Help needed"
date: 2008-11-26
forum: Apple Hardware Users
---

### Post by k.ashi.f on 2008-11-26
Hello geniuses, I am completely new to ubuntu. Well I was able to triple boot my Macbrook Pro with Apple, Windows and Ubuntu. I used terminal to create 3 partitions in my hard drive. Installed rEfit. Installed Windows on one partition. Installed ubuntu. Found some instructions on the forum. And finally it’s working. But for some reason the rEfit wasn't working. Checked on the forum and found that I needed to table the rEfit. Once I did that every operating system is working.

My Ubuntu is working fine. Installed upgrades. Wireless is working [with the help I found on the forum]. But I am completely new to ubuntu. Every day I am playing around with ubuntu. But here are the things I still need help with.

1)Sound is not working. Almost everything is working fine but the sound isn't.
I have checked so many different threads on the forum but didn't find anything. I have found some coding instructions on the forum but I have no idea how to implement those codes into the terminal. 

2)Is there a basic tutorial on gnome terminal available anywhere on this form where I can learn how to be able to enter the codes that users give out for different purposes.

3)It’s getting pretty hot. Any help in that department?

4)Another thing I needed help with is the settings for the 3D cube desktop settings. 

5)Any information on compiz fusion. I have installed compiz fusion. 

6)Any information on Emerald. I have installed Emerald theme manager. I also installed sceenlets.

7)Any good websites where I can download applications compatible with ubuntu. I want to use ubuntu for everything. Also I don't know how to install things. Every time I download something on my desktop to install and then open it. It opens the folder and then shows me the different files in the folder with different file extensions and I have no clue which one to open in order to install. I do not know which file extensions works with ubuntu.

8)Are they any basic tutorials for ubuntu and how it works and how different things work in ubuntu.

9)Any other update, upgrade, or something that I have missed but can help me use ubuntu more efficiently. 

I have been searching within these threads. I know the help is right here somewhere but for some reason I am not being able to reach it. So can anyone please point me to the right direction? Thanks in advance.

---

### Post by matchstich on 2008-11-26
look in the beginner section, there are  quite few tips on getting started and where to find help.

---

### Post by hyperboloid on 2008-11-27
When asking for help it is important to identify what hardware you have as well as which version of Ubuntu you are running. I will assume that you are running Ubuntu 8.10 (Intrepid), the most recent version.

Look here: [https://help.ubuntu.com/community/MacBookPro_Penryn]("https://help.ubuntu.com/community/MacBookPro_Penryn") and read carefully. It explains how to get sound going, for instance.

Also you should install *gnome-power-manager* and *hal-applesmc* from the MactelSupport repository [https://wiki.ubuntu.com/MactelSupportTeam/PPA]("https://wiki.ubuntu.com/MactelSupportTeam/PPA"). G-P-M might take care of your "running hot" issue: my MBP runs *cooler* under Ubuntu than it did under OS X.

---

### Post by k.ashi.f on 2008-11-27
Sorry, Here is the hardware information for my Mackbook.

Hardware Overview:
  Model Name:    MacBook Pro
  Model Identifier:    MacBookPro4,1
  Processor Name:    Intel Core 2 Duo
  Processor Speed:    2.4 GHz
  Number Of Processors:    1
  Total Number Of Cores:    2
  L2 Cache:    3 MB
  Memory:    2 GB
  Bus Speed:    800 MHz
  Boot ROM Version:    MBP41.00C1.B03
  SMC Version:    1.27f1
  Serial Number:    W8832BL2YJX
  Sudden Motion Sensor:
  State:    Enabled
---------------------------------------------
Intel High Definition Audio:
  Device ID:    0x106B00A3
  Audio ID:    56
  Available Devices:
  Speaker:
  Connection:    Internal
--------------------------------------------
Chipset Model:    GeForce 8600M GT
  Type:    Display
  Bus:    PCIe
  PCIe Lane Width:    x16
  VRAM (Total):    256 MB
  Vendor:    NVIDIA (0x10de)
  Device ID:    0x0407
  Revision ID:    0x00a1
  ROM Revision:    3212
Color LCD:
  Display Type:    LCD
  Resolution:    1440 x 900
  Depth:    32-bit Color
  Built-In:    Yes
  Core Image:    Hardware Accelerated
  Main Display:    Yes
  Mirror:    Off
  Online:    Yes
  Quartz Extreme:    Supported

---

### Post by k.ashi.f on 2008-11-30
Thanks, I am able to fix the "sound" and "running hot" issues. Can someone please help me with other issues. Thanks in Advance.

---

### Post by hyperboloid on 2008-11-30
> **k.ashi.f said:**
> Thanks, I am able to fix the "sound" and "running hot" issues. Can someone please help me with other issues. Thanks in Advance.

You don't say what "other issues" you need help on, so it is rather hard to help you. The more specific you can be, the more likely someone will have a solution. 

Some general tips: Have you looked at the documentation on the system, by clicking on the "Help" icon on the top munu bar? (Looks like a life preserver.) Also this page [https://help.ubuntu.com/8.10/index.html]("https://help.ubuntu.com/8.10/index.html") contains a wealth of information for beginners. 

Getting used to the command line is helpful, and for that you might want to get a book on Linux (the O'Reilly series is good) or google around on the net for basic documentation on Linux/Unix programming.

---

