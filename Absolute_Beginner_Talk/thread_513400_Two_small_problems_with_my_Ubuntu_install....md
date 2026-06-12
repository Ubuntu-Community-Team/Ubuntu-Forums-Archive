---
title: "Two small problems with my Ubuntu install..."
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Turkish Hijinks on 2007-07-30
Hey folks,

Last night I was having some troubles installing Ubuntu... thanks to the great advice I got from these forums, I now have Ubuntu up and running on my system.

However, there are three small problems than I hope you guys can help me out with.

1. I'm not able to connect to my wireless network. The computer is detecting the networks, so I don't think it's a problem with the wireless card. When I click on my own network, it asks me to enter my network password. When I enter the password and click connect, it tries to connect but then fails. I tried this on all three security settings (WEP 128-bit, WEP 64/128-bit Hex, WEP 64/128-bit ASCII)... all gave the same result. Any idea how I might be able to get around this?

2. I can't increase the resolution. I think this is because I can't enable the graphics driver. Every time I go to Desktop Settings, it asks me to restart so that the graphics card can be enabled. However, after restarting, the graphics card is still not enabled. I have an nVidia GEForce 6800 GS.

Thanks in advance for all the help. :)

---

### Post by stchman on 2007-07-30
> **Turkish Hijinks said:**
> Hey folks,

Last night I was having some troubles installing Ubuntu... thanks to the great advice I got from these forums, I now have Ubuntu up and running on my system.

However, there are three small problems than I hope you guys can help me out with.

1. I'm not able to connect to my wireless network. The computer is detecting the networks, so I don't think it's a problem with the wireless card. When I click on my own network, it asks me to enter my network password. When I enter the password and click connect, it tries to connect but then fails. I tried this on all three security settings (WEP 128-bit, WEP 64/128-bit Hex, WEP 64/128-bit ASCII)... all gave the same result. Any idea how I might be able to get around this?

2. I can't increase the resolution. I think this is because I can't enable the graphics driver. Every time I go to Desktop Settings, it asks me to restart so that the graphics card can be enabled. However, after restarting, the graphics card is still not enabled. I have an nVidia GEForce 6800 GS.

Thanks in advance for all the help. :)

Give us an lspci output here.  Thsi will tell us the type of wireless card you have.


As far as your nvidia card just enable the restricted drivers.

---

### Post by Turkish Hijinks on 2007-07-30
> **stchman said:**
> Give us an lspci output here.  Thsi will tell us the type of wireless card you have.


As far as your nvidia card just enable the restricted drivers.

Thanks for the quick response man :)

How can I do both of those things (sorry, I'm new to Ubuntu).

---

### Post by shagster_ on 2007-07-30
Did you download the Nvidia drivers?  If so, then you need to enable them in System->Administration->Restricted Devices

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

and also, just open up a Terminal and type lspci ....it will list all of your PCI cards....post that output

---

### Post by kostkon on 2007-07-30
> **Turkish Hijinks said:**
> 2. I can't increase the resolution. I think this is because I can't enable the graphics driver. Every time I go to Desktop Settings, it asks me to restart so that the graphics card can be enabled. However, after restarting, the graphics card is still not enabled. I have an nVidia GEForce 6800 GS.

I think this happens because you use the wrong version of the Nvidia driver. In Synaptic there are three versions of the driver, *nvidia-glx*, *nvidia-glx-legacy* and *nvidia-glx-new*. Which one do you use?

If you use, for example, *nvidia-glx*, try to use *nvidia-glx-new*, or the opposite.

*nvidia-glx-legacy* is not for your card, for sure.

---

### Post by Turkish Hijinks on 2007-07-30
Thanks for all the responses.

I'll switch back over to the Ubuntu partition and I'll come back with the lspci report.

By the way, the wireless card that I'm using is a LinkSys wmp54g v. 4.0... if that helps at all.

---

### Post by shearn89 on 2007-07-30
if it can find access points, thats impressive - i thought that linksys cards weren't natively supported? Anyone clarify for me? I know i had to use ndiswrapper for mine...

---

### Post by shagster_ on 2007-07-30
this might help then (assuming you have Feisty)

[Problems with WMP54G (rt2500) wireless card in Feisty]("http://ubuntuforums.org/showthread.php?t=506487")

---

### Post by leodesol on 2007-07-30
For the wireless issue... are you putting in the WEP key, or the pass phrase (password) used to generate your key?

Log in to your router (10.168.1.1) and goto wireless security. Find the part that lets you choose what kind of security (WEP128, 64, etc) and then write down the Key generated in the field marked **Key 1** (should be the one you use, default one). Use this key as your password to connect the Ubuntu machine.

I am sorry if you already tried this.

---

### Post by Turkish Hijinks on 2007-07-30
> **leodesol said:**
> For the wireless issue... are you putting in the WEP key, or the pass phrase (password) used to generate your key?

Log in to your router (10.168.1.1) and goto wireless security. Find the part that lets you choose what kind of security (WEP128, 64, etc) and then write down the Key generated in the field marked **Key 1** (should be the one you use, default one). Use this key as your password to connect the Ubuntu machine.

I am sorry if you already tried this.

Hi there... thanks for the suggestion. I did what you said, and turns out that the password I was trying to enter was the same key given in the **Key 1** slot. So, I don't think I'm trying to put in the wrong password.

So, here is what I have for now...

1. My lspci report:

> 
mehmet@Turkish:~$ lspci 
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1) 
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2) 
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2) 
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2) 
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) 
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) 
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) 
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2) 
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) 
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2) 
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) 
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) 
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04) 
01:06.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04) 
01:06.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) 
01:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01) 
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) 
02:00.0 VGA compatible controller: nVidia Corporation NV41 [GeForce 6800 GS] (rev a2) 
mehmet@Turkish:~$  


2. Even after trying to enable the restricted drivers from the Restricted Devices Manager, I'm back to where I started from.

---

### Post by stchman on 2007-07-31
> **Turkish Hijinks said:**
> Hi there... thanks for the suggestion. I did what you said, and turns out that the password I was trying to enter was the same key given in the **Key 1** slot. So, I don't think I'm trying to put in the wrong password.

So, here is what I have for now...

1. My lspci report:



2. Even after trying to enable the restricted drivers from the Restricted Devices Manager, I'm back to where I started from.

The restricted drivers should enable 3D acceleration for that card.

---

