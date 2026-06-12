---
title: "Uh oh..."
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by evolushun on 2007-10-02
OK, so I am posting this thread where it seems it will get some attention.  I have been running Ubuntu for about 4 days and have installed a lot of stuff.  I have tried so many different things due to  a plethora of information.  Now, my PC is running slow, some things just stop working and I need to start over, I think.  Is there a way to restore back to the original state of Ubuntu with only the necessary drivers I had when it started or do I have to format?

If I do need to format, there are a few things I need help with, as I am a noob when it comes to Linux.  I need a way to install Java.  I use it for IRC chatting on a site I belong to and it's just nice to have that installed.  I have Sun Java 6 installed if that helps.  I also need the code to install WINE as I use that for uTorrent.  To be honest I never got it working so if you know of something better, that would be cool.  Other than that, that is all I absolutely require to get up and running.  So, if you find this message, either help me restore back or post some codes!  LOL

---

### Post by Steveway on 2007-10-02
I would recommend Xchat for your IRC.
And instead of Utorrent I would go with Deluge.
They should be both in the normal Repos, so you can install them with Synaptic.

---

### Post by tgalati4 on 2007-10-02
You say your system is running slow.

>top

See if there are processes that are sucking up your CPU cycles.

Control-C to quit top.  

>sudo killall nameofprogramthatismakingyoursystemrunslow

No reason to reinstall unless you want to put on a different distro.

---

### Post by dwhitney67 on 2007-10-02
If you are trying to get attention, you should have considered a better title to your thread!  "Uh oh..." conveys nothing whatsoever.

Just reinstall Ubuntu and this time try not to add anything unless you know what you are doing.  This forum can serve you if you post appropriate questions.  Right now, it is impossible to determine the state of your system, since it seems that even you don't know.

---

### Post by evolushun on 2007-10-02
OK...I have started over and I have followed a few guides.  I have an ATi graphics card and have run the tutorial but I still cannot access my desktop effects.  I have also enabled multimedia and had no issues with that, it seems.  This is the second install where I cannot access my desktop enhancements...am I missing something?

---

### Post by dwhitney67 on 2007-10-02
Can you please elaborate the terms "desktop effects" and "desktop enhancements"?  Do you mean the Gnome window manager?  Is X11 running or are you staring only at the "black screen" console?

---

### Post by evolushun on 2007-10-02
If I go to System > Preferences >Desktop Effects, I get this error message:

The Composite extension is not available.

Does that help?

---

### Post by tgalati4 on 2007-10-02
Well, you didn't post your hardware specs, so we're just guessing.

Post the output of:

>lspci -vv

---

### Post by evolushun on 2007-10-02
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

---

### Post by aparigraha on 2007-10-02
A good guide to utorrent with wine:
[http://ubuntuforums.org/showthread.php?t=295134](http://ubuntuforums.org/showthread.php?t=295134)[http://ubuntuforums.org/showthread.php?t=295134]("http://ubuntuforums.org/showthread.php?t=295134")
Works in feisty as well.

To save some time... next time you could make a backup of your drive, before trying out all those programs. A good and easy backup guide can be found [here.]("http://ubuntuforums.org/showthread.php?t=35087")
Good luck!

---

### Post by tgalati4 on 2007-10-02
You have an ATI Xpress M200 video card.  Perhaps you can do a search in the forums to see how well it is supported for 3D Desktop effects.

---

