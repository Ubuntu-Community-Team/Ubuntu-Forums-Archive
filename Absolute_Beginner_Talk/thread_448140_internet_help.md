---
title: "internet help"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by dzza on 2007-05-18
Hi.  I'm new to linux and have installed ubuntu 7.04 on a new computer- 

Intel penium 4 650 3.4 ghz w/ p23g via chipset

The installation finished successfully, I plugged in my ethernet cable, went to system-admin-network, and the only option i'm presented with for a network is a dial-up modem, which helps none with my high-speed ethernet connection.  I have no idea how to actually get the internet up and running on my comp.  

The driver disk that came with the motherboard has drivers for giga lan, but I was told at #linuxhelp that I shouldnt need any motherboard drivers, which is good because I wouldn't have a clue how to install them anyway since everything I've looked at about installing things on ubuntu involves the package manager.  Any help is appreciated, thanks

---

### Post by gavintlgold on 2007-05-18
You should have a network manager in the panel, and right-clicking it might help, perhaps? For me, it works automatically, so idk what your problem is exactly.

OR, try restarting with the cable attached, that may be a little bug in ubuntu.

---

### Post by dzza on 2007-05-18
Ok, still no internet-

There is no option in network manager that lets me add a new connection (high speed ethernet), all i can really do with network manager is look at modem properties for a dial up modem i do not have but rather is the default thing in network manager.  Properties, other tabs in network manager, its all just for the default modem connection.  Nothing seems to be available to let me add a new connection type.

Also, I've made sure that it isn't a matter of plugging the ethernet cable in before or after booting up.  Neither way makes a difference.

Following some advice on a linuxhelp irc channel, I was told to try entering lspci in the terminal, find the network card, and add it using the modprobe command (or something to this effect).

Unfortunately, after doing lspci, i can't find anything that outright resembles a network card:


00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)


By the way, the info I have on the network card is:

Integrated Realtek RTL8100 Chipset

Standards: IEEE 802.3 10BASE-T, IEEE 802.3u 100BASE-T

Use to connect to your network or Cable/DSL modem!

Well, hopefully some of the info I posted above will help someone help me, because I sure can't make sense of it : (  

Any help would be greatly appreciated- I want so bad to be an XP convert, if I could just get online !

---

### Post by gavintlgold on 2007-05-19
Sorry, I don't know enough about it to help you.

---

### Post by wormser on 2007-05-19
I did some searching for you and it does not look good.  It looks like the best bet would be to buy a supported card.

Check out the [2nd post]("http://ubuntuforums.org/showthread.php?t=241729&highlight=Realtek+RTL8100") from somebody else with the same question.  If you do get it working write up a tutorial.

---

