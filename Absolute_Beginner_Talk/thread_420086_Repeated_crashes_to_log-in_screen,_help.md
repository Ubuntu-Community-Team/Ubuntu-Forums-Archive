---
title: "Repeated crashes to log-in screen, help?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Spreggo on 2007-04-23
Every so often (sometimes a few times a as many minutes) Ubuntu just dumps and brings me back to the login screen. I know this isn't enough information but when I log back in it doesn't let me know what crashed. Is there a way I can access some log and get this information?

---

### Post by dannyboy79 on 2007-04-23
this normally means that your home partition is full and it can't write it's files it needs to in order to continue. OR that you have a misconfigured x-server. (xorg.conf) to reconfigure your x-server try

sudo dpkg-reconfigure xserver-xorg   
(NOTE: i sometimes get this mixed up, it may be ".........xorg-xserver" instead)

---

### Post by kc5hwb on 2007-04-23
This is the correct cmd:

```
sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by Spreggo on 2007-04-23
Okay, I tried that but ended up breaking my x-server. I went in and restored the back up and it is back to normal now. What I really need is a way to get at a crash log or something to see exactly what is crashing and where.
That way I could be more specific about the crash and the solution. Especially as this was happening on edgy and is still happening on feisty. I'm assuming it isn't reading my hardware properly at some point.
So, is there a crash log I could access??
Thanks in advance.

---

### Post by dannyboy79 on 2007-04-23
var/log/

contains all the log files you can handle. also, there is a file within your home dir called x-session errors or something like. I forget. maybe it's .Xserver-errors or something along those lines. I don't see how the reconfigure can break your xserver. did you just pick the defaults? what graphics adapter do you have?
post back what this returns
sudo lspci -v

---

### Post by Spreggo on 2007-04-23
It crashed while I was typing this :( The syslog it gave me looks a little funky, I'll attach it.

My original message:
I have an ATI radeon x1900xt which has been the source of many woes on the Ubuntu side of my computer.
I think the defaults totally mishandle my hardware configuration, and the Ubuntu installer creates xorg.conf to make it work, but reverting xorg.conf without the compensation is trouble. I have, as far as I can tell, properly installed the radeon in the best way the community has to offer, that is, without real accelerated graphics but usable functionality.
 Here's the info requested:
> 
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5000
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: e4000000-e5ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: [88] Subsystem: Giga-byte Technology Unknown device 5000
        Capabilities: [80] Power Management version 3
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at c000 [size=32]



**The syslog looks like this:**
> Apr 23 14:31:41 The-Ugly-Bream dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 23 14:31:41 The-Ugly-Bream dhclient: send_packet: Network is down
Apr 23 14:31:52 The-Ugly-Bream dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 23 14:31:52 The-Ugly-Bream dhclient: send_packet: Network is down
Apr 23 14:31:52 The-Ugly-Bream NetworkManager: <WARNING>^I nm_device_802_11_wireless_set_mode (): error setting card wlan0 to Infrastructure mode: Operation not supported 
Apr 23 14:31:55 The-Ugly-Bream dhclient: No DHCPOFFERS received.
Apr 23 14:31:55 The-Ugly-Bream dhclient: No working leases in persistent database - sleeping.
Apr 23 14:31:55 The-Ugly-Bream avahi-autoipd(wlan0)[7985]: SIOCSIFFLAGS failed: No such device
Apr 23 14:33:57 The-Ugly-Bream NetworkManager: <WARNING>^I nm_device_802_11_wireless_set_mode (): error setting card wlan0 to Infrastructure mode: Operation not supported 

Something like that for the entirety of it, if that is important.
I also noticed these EE (errors) at the end of my Xorg.0.log:

> drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.

I am using Xgl and not AIGLX so perhaps there is a conflict somewhere?

---

### Post by dannyboy79 on 2007-04-23
> **Spreggo said:**
> It crashed while I was typing this :( The syslog it gave me looks a little funky, I'll attach it.

My original message:
I have an ATI radeon x1900xt which has been the source of many woes on the Ubuntu side of my computer.
I think the defaults totally mishandle my hardware configuration, and the Ubuntu installer creates xorg.conf to make it work, but reverting xorg.conf without the compensation is trouble. I have, as far as I can tell, properly installed the radeon in the best way the community has to offer, that is, without real accelerated graphics but usable functionality.
 Here's the info requested:


**The syslog looks like this:**


Something like that for the entirety of it, if that is important.
I also noticed these EE (errors) at the end of my Xorg.0.log:



I am using Xgl and not AIGLX so perhaps there is a conflict somewhere?


well the info you gave me from lspci -v wasn't helpful at all, i needed all of it to determin your graphics card but since you have now told me what it is, I no longer need all of lspci -v.

not sure what to tell you about the Network Manager errors with dhclient and dhcpdiscover. I didn't know they renamed them to have The-Ugly-Bream within their name??? I don't use dhcp nor do I use network manager. give wifi-radar a try.

the errors regarding the wacom devices are nothing, they put that stuff in the default xorg.conf for people with tablets and whatnot. just comment out all of the inpout devices that you don't need/have but make sure you leave a mouse input

We really need to look at the .Xsession-errors file. or whatever it is. you could find it with

sudo find / -name *error

I am sure that it'll be in your home directory but it's hidden so you'll have to show hidden files using 

ls -la ~/

or show hidden files within nautius. I am guessing it's realted to your graphics card. have you tried the ati driver? also, what does the kernel log say? or even dmesg?

sudo gedit /var/log/kern.log   (i think??)

dmesg

---

### Post by Spreggo on 2007-04-23
Wow. Okay thanks for the help :)
I just realized it's actually all my fault, this one chalks up to human error.
What keeps happening is my finger is lingering much too long on the left shift when I reach to hit back space.
AKA restarting the xserver :|
Sorry for being such a noob, thanks for all the help though :D

Can I change the binding for that?  lol thanks.

---

