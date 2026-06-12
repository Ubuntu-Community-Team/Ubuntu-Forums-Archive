---
title: "Freezing Problem / WLAN problem"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by parmomike on 2007-09-15
First off, apologies for what may be a much repeated problem but I've searched and searched online and there's nothing specific enough to my problem and i've tried on IRC but the help comes in drabs. I decided to install Ubuntu yesterday and have no previous knowledge outside of Windows. I first loaded from the Live CD to try it out. It did crash a couple of times - I figured this was either to do with my RAM or the CD and proceeded with the installation. I had a few problems in installing in that it kept on freezing before the installation began or it wouldn't detect my partitions properly. Actually, the first time it crashed, I tried to restart into Windows and it had corrupted - hal.sys or dll file if I remember correctly. I'm not overly worried as I know all my data is still there and can repair Windows later (my CD is actually in storage). So I have (what I think was) a clean install on a another hard-drive - the one with Windows has been taken out.

After logging on, anywhere between 30 sec - 2mins, the system will freeze - the mouse don't move, num-lock won't toggle and I can't ctrl-alt-F1 (the only shortcut I've learnt). I have to reboot the system. Someone on IRC#Ubuntu told me to amend something in the bootup - pressing escape and 'e' and adding something to one of the lines - I don't know what it was off the top of my head but he mentioned it after confirming I had a dual core machine and it did appear to help at first. I thought that if all packages were updated then this may solve the problem but I can't connect to my WLan to do so. I also considered it might be a graphics issue and have the latest NVIDIA drivers in the form of a .run file on my desktop but can't figure out the next step.

To summarise - my 3 problems - system freezes up; can't access WLan - don't know how to install drivers. With regards to the WLan, it's a D-Link 54g router using a 64bit hex WEP key and no auth. The adapter is a Belkin PCI card (exact model no. unknown right now). The system detects the adapter and the WLan but won't connect when I enter the WEP key. Unfortunately, I can't try too many things before the system locks up! With regards to the graphics, the Restricted Driver Manager detects the card but when I click enable, it doesn't toggle to enabled after I accept the warning. The guide to install the driver says type "sh NVIDIA-x86.,......(filename)" but not where to type it?? Is it a terminal window? If so, it says it can't open it.

It's not such a smooth transition to linux thus far but I'm determined to make it work! Any help on any of the problems is appreciated. I know freezing problems can be caused by a million things (in Windows as least!). I believe there is a synaptic tool to debug errors or something? I'll run it if someone tells me how :)  

Regards,
Mike

System:
Pentium-D Dual Core @3.40GHz
2GB DDR2 RAM
GeForce 7900 GS Golden Sample
200GB Maxtor PATA HDD
Belkin 54g Wireless adapter

---

### Post by mikewhatever on 2007-09-15
With all the freezes using the live CD, I don't think you should have installed, but it's too late now. Consider checking the iso with [M5SUM]("https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29"). If the iso is corrupted redownload, reburn at low speed (max=x4) and reinstall. Once Ubuntu works properly we can deal with other issues.

---

### Post by parmomike on 2007-09-16
Yeh makes sense, though seeing all the other users problems with wlan and 7.04, I may try an earlier version. Thanks.

---

### Post by Crafty Kisses on 2007-09-16
Can you please post the following output:
```
lspci
```

---

### Post by parmomike on 2007-09-16
michael@michael-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0c.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 7900 GS (rev a1)
michael@michael-desktop:~$ 



Should I hold off uninstalling for now??
Thanks

---

### Post by mikewhatever on 2007-09-16
> **parmomike said:**
> Yeh makes sense, though seeing all the other users problems with wlan and 7.04, I may try an earlier version. Thanks.

Actually, every version has problems, otherwise why would we need the forum, other then Cafe and Backyard parts. The very nature of the forum is help and support, so people mostly post their problems. If everything is fine, a user probably would not post. By the way, it is the same on XP support forums, with the addition of security section.
Now, I am not saying earlier versions are not good to try. Anything that works would be OK. I've seen users here talking favourably of Linux Mint, Ubuntu based distribution.

---

### Post by parmomike on 2007-09-16
Hi again,

I've spent pretty much all day reading up possible solutions after deciding to try and fix the problem. I'm pretty convinced that reinstalling from a different cdwon't  make much difference. I've reinstalled from the same cd just to see if it helped and it didn't. I've ran a full memtest on it at boot (excluding test 9) and had no problems. I gather from what I've read that there's a full supplement of log files created. Is there someway of looking into these log files or running a synoptic to see what is causing the system to freeze. I think I've found a way to make the WLAN work based on my network card once this is sorted. Also, when shutting down once, I inadvertently switched to a command line screen which showed the stages of shutting down and the last error reported some fault with the network manager.

Any suggestions appreciated. Thanks again for your time.

---

