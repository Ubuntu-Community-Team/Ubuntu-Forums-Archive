---
title: "[SOLVED] Resolution Problems - Unable to change from 800 x 600 @ 73 Hz"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by labinnsw on 2007-11-18
First of all let me advise that I am an absolute dunce to linux and ubuntu. I am not familiar with terminals or command lines. Please give all instructions in the simplest most basic terms or I will need to ask for instructions to be explained.

**My operating System is Ubuntu 7.10 (upgraded recently from 7.04)** I always install updates when the Updated manager alerts me. After one of these updates pertaining to Nvidia, my resolution went wacky. Once logged in the screen was scrambled. I was able to fix that after reading some of the forum articles. So now I can see what's on the screen but **I am unable to change the resolution from 800 x 600 @ 73 Hz.**

I have done many searches and **the only solutions I could find required making a clean install. This is not what I want. I am sure there must be some other way. Can any one help?**

[B]My video card is Nvidia RIVA TNT2 Model 64/Model 64 pro [microsoft corporation]
My monitor is BenQ FP91G+[/B]

In separate partitions on my computer I run:
Windows Xp - Resolution 1280 x 1024 @ 75 Hz - Works beautifully
Ubuntu 6.04 - Resolution 1280 x 1024 (Not sure of refresh rate) - Works beautifully

If this is not enough information please let me know and I will be only too happy to oblige with any additional information required.

I wouldn't mind changing my video card. Would that be recommended?

---

### Post by banewman on 2007-11-18
I use the same video card in my spare comp - you need to find the "restricted driver manager" in the menu - click applications and scroll through. That will install the right driver and allow you to change resolutions. :)

---

### Post by Qwerty_ on 2007-11-18
Make sure that you have all of the repositories selected as well. Otherwise you wont be able to install the restricted drivers.

System>Administration>Software Sources.

---

### Post by banewman on 2007-11-18
Good catch qwerty! :)

---

### Post by Qwerty_ on 2007-11-18
Well we have to look after our fellow Aussies as much as possible dont we :P

---

### Post by labinnsw on 2007-11-19
Thanks for helping out guys

I think I did install "Restricted Drivers Manager," however I did not have all the repositories selected. So I uninstalled "Restricted Drivers Manager" and then selected all the repositories before reinstalling the "Restricted Drivers Manager." When I tested it the screen goes blank for a while and then reverts to 800 x 600 @ 73 Hz.

Any other suggestions?

---

### Post by Partyboi2 on 2007-11-19
Have you tried reconfigure .xorg to see if that helps?
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by labinnsw on 2007-11-19
Not sure what to chose after "sudo dpkg-reconfigure xserver-xorg" Should I chose "Yes" or "No" regarding "Attempt to Auto detect video hardware?"

---

### Post by Qwerty_ on 2007-11-19
I would go yes. When it asks what driver to use select nvidia.

---

### Post by labinnsw on 2007-11-20
Thanks for the help so far. 

Where in the script below is the "video card's bus identifier"?

labinnsw@labinnsw-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:04.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
00:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:07.0 Communication controller: Conexant HCF 56k Data/Fax Modem (rev 08 )
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394 Controller
00:14.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:14.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:14.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:14.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:14.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
labinnsw@labinnsw-desktop:~$

---

### Post by labinnsw on 2007-11-21
Never mind the last question. The problem has been solved. For anyone else who might be looking for the same solution additional notes are given below.

You may also need to install "linux-restricted-modules-2.6.22-14-generic" (sudo apt-get install linux-restricted-modules-2.6.22-14-generic)

When you have completed all tasks restart the computer. On reboot you should see the Nvidia splash screen. (If you don't, you probably will still have a problem)

Now go to: System > Administration > Screens and Graphics. Under the "Graphics Card" tab select Nvidia. Under the "Screen" tab set your resolution and refresh rate. When you exit the you will be asked to log out. Log off then log on. Your resolution problem should be solved.

Thanks again for all the assistance guys.

---

### Post by Andre_3608 on 2007-12-16
Very diffidently, this suggestion:  System / Administration / Screen and Graphics / Screen - select the resolution you require.  Then System / Preferences / Screen Resolution - the option you chose in Screen and Graphics will now be available.  Hope this helps - it took me about three months to get there!
André

---

