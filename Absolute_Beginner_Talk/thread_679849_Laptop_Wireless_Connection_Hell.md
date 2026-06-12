---
title: "Laptop Wireless Connection Hell"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by MoJoMoGo on 2008-01-27
I have come to the end of my brain capacity... Hopefully someone will be able to help! Thanks in advance!!

** - OS: **Ubuntu 7.10 - I-386

** - Laptop:** Compaq C717NR (C700 Family)

** - Router:** D-Link WBR1310 Rev.B1 - WEP - 64-Bit ASCII Key

** - lpsci output (Relevant): **
    01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

** - iwconfig output:**
     lo        no wireless extensions.  
   eth0      no wireless extensions.  
   eth1      IEEE 802.11b/g  ESSID:ff/any  Nickname:"Broadcom 4311" 
             Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid    
             Bit Rate=1 Mb/s   Tx-Power=18 dBm    
             RTS thr: off   Fragment thr: off 
             Encryption key: off 
             Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm 
             Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
             Tx excessive retries:0  Invalid misc:0   Missed beacon:0

** - ifconfig output:**
   eth0      Link encap:Ethernet  HWaddr 00:1B:38:83:5E:22   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:21 Base address:0xa000  
 
eth1      Link encap:Ethernet  HWaddr 00:00:00:1A:73:A7   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:993 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:43458 (42.4 KB) 
          Interrupt:11 Base address:0x8000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

The laptop has a small button that (normally) enables/disables the wifi. When enabled, the light is blue. Disabled, amber. 
This is what I have tried so far:

1 - Installed package bcm43xx-fwcutter
2 - Enabled restricted driver (Firmware for Broadcom 43xx chipset family)
3 - Directed the driver to wl_apsta-3.130.20.0.o

- - Now the restricted driver manager shows that particular driver (Firmware for Broadcom 43xx chipset family) in use.
- - The button is now functional.
- - No wireless networks are visible via the taskbar applet (nm-applet 0.6.5). Another computer (running Win XP) shows mine and 2 other neighbor's networks (I am about 15 feet away from my router).

4 - Tried the taskbar applet  "CONNECT TO ANOTHER NETWORK" option and entered all the relevant information (SSID, Security protocol and Security key).
4.1 - The applet displays the "trying to connect" animation and I keep getting a "Network Password Requested" window. I have entered all the different keys, under all the different protocols available to no avail. The same mesage keeps popping up.

This is about the nth installation attempt. I have tried installing SUSE 10.3, Sabayon and Linux Mint. I tried to follow instruction for ndiswrapper on each of those distros, but never even got past the visual display of the WiFi button on the computer.
 I cannot remember what I tried before (too many steps to recall), but the steps outlined above were just performed, hence my posting here (Ubuntu seems to be the best, most user friendly distro so far).

Thank you any and all for your input!!

Mojo

---

### Post by mikeyphi on 2008-01-28
Only one suggestion - I see from your post that your router access point is listed as 'invalid'
Do you have your system closed?
Try opening your router webpage and changing to 'Open system'  - keep the WEP.

---

### Post by MoJoMoGo on 2008-01-28
> **mikeyphi said:**
> Only one suggestion - I see from your post that your router access point is listed as 'invalid'
Do you have your system closed?
Try opening your router webpage and changing to 'Open system'  - keep the WEP.

No, the authentication is OPEN. I've also tried without any security (WEP, WAP, etc).

---

### Post by mikeyphi on 2008-01-28
> **MoJoMoGo said:**
> No, the authentication is OPEN. I've also tried without any security (WEP, WAP, etc).

When you tried without WEP - did you still get the request for Network Password?

---

### Post by igknighted on 2008-01-28
The 4311 Rev2 chip (which you have) is notoriously finicky with the bcm43xx driver.  You should try the ndiswrapper to install your drivers, I think you will find these much more successful (note: I hate ndiswrapper and always avoid it if possible.  If you are up for a challenge - compiling a new kernel and broadcom driver - it is possible to not use ndiswrapper, but that is the easiest soultion for you)

---

### Post by e_james on 2008-01-28
As a general rule each ubuntu release is an improvement on its predecessor but, in my very limited experience, it is not always so.

---

### Post by cubeist on 2008-01-28
I have the same Broadcom Card and this tutorial was the only way to get reliable wifi...

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc)

---

