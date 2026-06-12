---
title: "LiveCD gives Login window that won't let me login"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Eagle 101 on 2007-05-29
I am currently dual booting Windows XP and Gentoo Linux. I would like to install xubuntu over either XP or gentoo linux. (I've not made up my mind yet). I have downloaded and burned a .iso of the graphical install CD, fiesty (7.04). The MD5 hashes match.

When I run the CD it will load 100%, but it comes up to a login window. Its blue, with two options below the username field, language, and something else I can't recall). There are also in the lower left hand corner two buttons that say restart and shut down.

For some reason I can't get past this window. I've tried leaving the field blank, and just pushing enter, that does not work. I have tried putting 'root', and pushing enter, and I have tried putting my old login name from gentoo linux. Other things I have tried include 'xubuntu', 'kubuntu' and 'ubuntu'.

None of the above attempts work, and I'm wondering if I have to do something special to make it allow me to play around in the LiveCD (I'd like to see if it can recognize my wireless, my main gripe with gentoo). Any and all help is appreciated. Thanks :)

-------- Edit --------
Just so you guys know I did check the forums, the only thing I could find was [http://ubuntuforums.org/showthread.php?t=68145](http://ubuntuforums.org/showthread.php?t=68145). Problem is that I've just burnt this CD.

-------- Edit -------
Here is my lspci information if it helps anyone.

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

---

### Post by sankarv on 2007-05-29
u could try root/ubuntu/linux combinations for username / password. possibly check if any boot parameters can be given accordingly and the better option is burn another cd (with low burning speed around 16-20x) and try it out.  it might work.

---

### Post by hyperair on 2007-05-29
Doesn't it auto login after a few seconds or so? Which Ubuntu LiveCD are you using?

---

### Post by Eagle 101 on 2007-05-29
I don't see any boot options that seem to apply for my situation. This is a CD that I burnt at 4x speed, as low as my burner would go. To clarify above I'm getting a screen that asks me for a username, no pass. I've tried putting in 'ubuntu', 'xubuntu', 'root', and a few other obvious usernames that I thought it might be. No avail. 

Again thanks for your help.

---

### Post by Eagle 101 on 2007-05-29
Ack, did not see the second post, no it does not auto login, I've left it sit for about 5 minutes in hope of it doing that. The CD is Xubuntu feisty 7.04.

---

### Post by Eagle 101 on 2007-05-29
In short, if you get said login message, get another CD and re-burn it... Thanks folks.

---

