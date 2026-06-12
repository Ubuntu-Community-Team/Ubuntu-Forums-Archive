---
title: "Ubuntu noob, internet connection help needed!"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Swimmerboy196 on 2007-11-12
Today, I installed another hard drive on one of my computers and slapped Ubuntu 7.1 on it. Everything's going ok so far (I have to learn my way around the OS) but I can't connect to the internet. Strangely enough, when I start my computer with Windows 2000, I have no problem getting a connection. I'm using a Linksys router, but I'm not hooked up to the main router (I'm wirelessly connected, through a USB, to my router, which is plugged into the ethernet on my downstairs comp). Any suggestions? It's kind of gonna stink if I can't use the internet on an open-source OS...Please, help me if you can!

---

### Post by Iceni on 2007-11-12
We need to know what make your usb wireless "card" is :)

---

### Post by reckless2k2 on 2007-11-12
well if you're wireless then ubuntu doesn't know your device. you need to consult the wifi docs and possibly install ndiswrapper-utils to connect wireless. 

[https://help.ubuntu.com/community/WifiDocs?highlight=%28wifi%29](https://help.ubuntu.com/community/WifiDocs?highlight=%28wifi%29)

start here and go forward. you can also post the terminal output for this command:

```
lspci -v
```

that'll fast track us doing the work for you. haha.

---

### Post by Swimmerboy196 on 2007-11-12
The main router model is: Linksys BEFW11S4-VN Ver. 2
The "Wireless USB Network Adapter" model #: WUSB11-VN ver. 2.6
Don't know if that helps....

---

### Post by Swimmerboy196 on 2007-11-12
The return/ouput is:
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02) 
        Flags: bus master, fast devsel, latency 0 
        Memory at f8000000 (32-bit, prefetchable) [size=64M] 
        Capabilities: <access denied> 
 
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02) (prog-if 00 [Normal decode]) 
        Flags: bus master, 66MHz, fast devsel, latency 32 
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32 
        I/O behind bridge: 0000c000-0000cfff 
        Memory behind bridge: ff800000-ff8fffff 
        Prefetchable memory behind bridge: e6900000-f69fffff 
 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02) (prog-if 00 [Normal decode]) 
        Flags: bus master, fast devsel, latency 0 
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32 
        I/O behind bridge: 0000d000-0000dfff 
        Memory behind bridge: ff900000-ff9fffff 
        Prefetchable memory behind bridge: f6a00000-f6afffff 
 
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02) 
        Flags: bus master, medium devsel, latency 0 
 
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02) (prog-if 80 [Master]) 
        Subsystem: Intel Corporation Unknown device 4742 
        Flags: bus master, medium devsel, latency 0 
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8] 
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1] 
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8] 
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1] 
        I/O ports at ffa0 [size=16] 
 
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02) (prog-if 00 [UHCI]) 
        Subsystem: Intel Corporation Unknown device 4742 
        Flags: bus master, medium devsel, latency 0, IRQ 5 
        I/O ports at ef40 [size=32] 
 
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02) 
        Subsystem: Intel Corporation Unknown device 4742 
        Flags: medium devsel, IRQ 9 
        I/O ports at efa0 [size=16] 
 
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02) (prog-if 00 [UHCI]) 
        Subsystem: Intel Corporation Unknown device 4742 
        Flags: bus master, medium devsel, latency 0, IRQ 10 
        I/O ports at ef80 [size=32] 
 
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02) 
        Subsystem: Intel Corporation Unknown device 4742 
        Flags: bus master, medium devsel, latency 0, IRQ 9 
        I/O ports at e800 [size=256] 
        I/O ports at ef00 [size=64] 
 
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] (prog-if 00 [VGA]) 
        Subsystem: ATI Technologies Inc Radeon 7000/Radeon VE 
        Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 11 
        Memory at e8000000 (32-bit, prefetchable) [size=128M] 
        I/O ports at c800 [size=256] 
        Memory at ff8f0000 (32-bit, non-prefetchable) [size=64K] 
        Expansion ROM at ff8c0000 [disabled] [size=128K] 
        Capabilities: <access denied> 
 
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01) 
        Subsystem: Intel Corporation EtherExpress PRO/100 VM 
        Flags: bus master, medium devsel, latency 32, IRQ 11 
        Memory at ff9ff000 (32-bit, non-prefetchable) [size=4K] 
        I/O ports at df00 [size=64] 
        Capabilities: <access denied> 
 
02:0a.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02) 
        Flags: medium devsel, IRQ 3 
        Memory at ff9fe000 (32-bit, non-prefetchable) [size=4K] 
        I/O ports at d800 [size=256] 
        Capabilities: <access denied>

---

### Post by reckless2k2 on 2007-11-13
[http://ubuntuforums.org/showthread.php?t=611273](http://ubuntuforums.org/showthread.php?t=611273)

that should help you since i wrote the same thing over and over again about ndiswrapper yesterday. 

you'll find your driver here: 

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)

just go to linksys and find the model and version. it'll give you info about where the driver is and such. 

then read my link. you should be fine.

---

### Post by Swimmerboy196 on 2007-11-13
Will installing the driver mess up my use  of the internet on the Windows hard drive? I don't think so, since they're seperate hard drives, but correct me if I'm wrong - I just don't feel like messing up a perfectly good computer.

---

### Post by deep.tinker77 on 2007-11-13
> **Swimmerboy196 said:**
> Will installing the driver mess up my use  of the internet on the Windows hard drive? I don't think so, since they're seperate hard drives, but correct me if I'm wrong - I just don't feel like messing up a perfectly good computer.

Nope, not at all, just follow the instructions above from reckless very carefully and you should be fine. Good luck:)

---

### Post by Swimmerboy196 on 2007-11-13
I installed the ndiswrapper common and -utils- 1.9, then checked to make sure the .inf and .sys were installed. However, when I entered the command "sudo ndiswrapper -l", the output read:
autorun : invalid driver!
lswlusb : invalid driver!
lswlusb.sys : invalid driver!
thefile : invalid driver!

I guess i downloaded the wrong driver...the driver I got was for the Linksys model I have, but for ver. 2.5 (I have 2.6). Is this the problem? I have the CD that we used to install it, should I use that instaed of downlaoding another driver?

---

### Post by reckless2k2 on 2007-11-13
yeah if you have the driver cd you want to use that but in the XP folder. you want to install all the inf drivers in that folder accept AUTORUN. you will have to remove the inf you have in there now though:

remove the bad driver(s)
```
sudo ndiswrapper -r THEWRONGDRIVER.inf
```

confirm it's empty before installing new
```
sudo ndiswrapper -l
```

version to version is different and you should use the CD if you can. with linksys, the weird thing is that you sometimes have to install more than one INF from the folder. delete the bad stuff in home now, then copy over contents of the XP directory on the install CD. then install the INFs accept AUTORUN.INF. 

then you should be fine with the sudo ndiswrapper -l out. then you can move on.

---

### Post by Swimmerboy196 on 2007-11-21
So.....

Whenever I tried to use the " -i" command for ndiswrapper, on any of the driver files, the output always returned saying that the files could not be found. Where should I copy the files to? I put them in my user folder (/home/MY USERNAME)...should they be there? What's the problem?

---

### Post by Swimmerboy196 on 2007-11-21
So...

Any time i try to use the "-i" command with ndiswrapper (to install the driver), the output always says that the file can't be found. Where should I copy the driver files to? I have them right now in my user file (/home/MY USERNAME) but i don't know if that's right....anybody have any ideas?

---

