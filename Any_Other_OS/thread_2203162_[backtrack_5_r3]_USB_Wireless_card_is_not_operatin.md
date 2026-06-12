---
title: "[backtrack 5 r3] USB Wireless card is not operating"
date: 2014-02-02
forum: Any Other OS
---

### Post by AmrE on 2014-02-02
Hi,

I would like to know if there is a solution to my problem as i connect TP-LINK TL-WN723N V3 to VM on VMware player 7.0.1 build-227600 and Guest is [backtrack 5 r3] Kernel [Linux bt 3.2.6 #1]
ifconfig shows only eth0 and lo0 and lsusb gives [Bus001 Device 002: ID 0bda:8179 Realtek Semiconductor Corp]. If someone can tell me if it is compatible with BT and if there is Drivers and firmware to use.

Thanks in Advance

---

### Post by varunendra on 2014-02-02
> **AmrE said:**
> lsusb gives [Bus001 Device 002: ID 0bda:**[COLOR="#FF0000"]8719[/COLOR]** Realtek Semiconductor Corp].

You mean **8179**, right?

This is a very new device and is not yet supported by any mainline kernels, as mentioned here : [https://wikidevi.com/wiki/TP-LINK_TL-WN723N_v3](https://wikidevi.com/wiki/TP-LINK_TL-WN723N_v3)
> USB ID not yet observed in any mainline kernel / this list

You may try an experimental driver from github : [https://github.com/lwfinger/rtl8188eu](https://github.com/lwfinger/rtl8188eu)

But please clarify this first - Are you trying to use the adapter in the Host (the OS running on the physical machine) or the Guest (the OS in the Virtual Machine)? You mentioned that you were trying to connect it to the VM (thus the Guest OS), but are asking the question for BT which you say is Host? A USB device has no connections to the Host once it is connected to the Guest OS (in the VM), so doesn't matter whether it is supported on the Host or not.

Or is it that the BT is actually Guest, not Host?

The steps to compile and install the above experimental driver on Ubuntu are as follows (should be same with BackTrack) -

[INDENT]1) Make sure the components to compile the driver are pre-installed -
```
sudo apt-get install --reinstall linux-headers-generic build-essential
```

2) Download the ['zip' package]("https://github.com/lwfinger/rtl8188eu/archive/master.zip") of the driver from the above github page.

3) Right-click the downloaded .zip file > Extract here. This will extract a folder named "rtl8188eu-master".

4) Open a terminal (Ctrl-Alt-T) > change to the extracted folder and compile/install as follows -
```
cd rtl8188eu-master
make
sudo make install
```

5) Either reboot, or manually load the driver -
```
sudo modprobe 8188eu
```

6) Post back your feedback to help us help you/others :)[/INDENT]

---

### Post by AmrE on 2014-02-02
Many Thanks for your help, your fast response is so much appreciated , i did not think there will be a reply so fast. I edited the post with the right number as you truly guessed and that BT is the Guest as you also truly guessed....

Results are:
1)lsusb command output still the same.
2)ifconfig command output: firstly it showed wlan0 and i connected to my wifi network through wicd but after that when i disconnected from it wlan0 was not in the o/p but still i can see wireless NWs in wicd GUI and wlan0 only shows when i connect to my wifi network through wcid.
3)i tried iwconfig and this is its o/p whether connected or not to wifi
> wlan0     unassociated  Nickname:"<WIFI@REALTEK>"          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


 

4)i tried airmon-ng while not connecting to wifi network and it showed nothing but while connecting its o/p is
> Interface	Chipset		Driver

wlan0		Unknown 		r8188eu





I can now use the USB device and connect to WIFI.I would like to ask if there will be in the future a BT Drive for it so as to use it in monitor mode or I try to get another one?

---

### Post by varunendra on 2014-02-02
So may I assume the driver is working fine other than the 'monitor mode'? If yes, please mark the thread as [SOLVED] as the support of this forum is limited to making the devices work, and that purpose is solved.

The drivers are part of the kernel and that is more or less the same (versions maybe slightly older or newer between distros) across all Linux based distros. So unless the BT community can patch the driver themselves to provide the monitor mode functionality, you can get that feature only if the original driver already has it. I'm not sure if that is going to happen or not, maybe you'd get a better and more precise answer if you ask the question in the BT community itself.

The BT forums have been officially closed and it seems the forums as well as most of the community has moved to Kali Linux, as mentioned in this (now read-only) BT Forum announcement : [http://www.backtrack-linux.org/forums/announcement.php?f=143](http://www.backtrack-linux.org/forums/announcement.php?f=143)

---

### Post by ANSELM_KEREM on 2014-05-07
Hello,

I am a new user of Ubuntu and have baught the same version of the same usb wireless card. Also downloaded the same driver as you metioned but I have no idea wht it still doesn't work. Could you please show me the way to run it?

Also I've opened a new Thread with "TL-WN723N v3-RTL8188eu" the link is below before reading this one.
[http://ubuntuforums.org/showthread.php?t=2222597&p=13016773#post13016773](http://ubuntuforums.org/showthread.php?t=2222597&p=13016773#post13016773).

Regads.

---

### Post by varunendra on 2014-05-07
Hello ANSELM_KEREM,

You are already getting help from the best person for wifi issues on your other thread. Please just follow what chili555 suggests, and don't try anything else while doing this. Trying multiple solutions/suggestions at the same time will most likely only confuse and further worsen the problem.

Be assured, you are getting best help possible on this forum. Good luck!

---

