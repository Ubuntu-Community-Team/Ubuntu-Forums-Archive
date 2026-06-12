---
title: "Standard vs 64 bit Ubuntu -- DVD players"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by glenna on 2008-01-20
I loaded the 64 bit Ubuntu on my laptop.  First there was no sound...fixed, then I couldn't access wifi...fixed, and I still can't figure out how to play dvd's on my laptop.  Did I install the right ubuntu?  Should I have installed the standard ubuntu?  Any thoughts on DVD players that work well for the 64 bit structure?  Or should I go back to the standard ubuntu?  Do DVD players work better with standard?

So far I've tried Mplayer, Totem, Totem-xine, and VLC without success.

I have a travelmate 6292 and the specs are:
	
Operating System
		
Genuine Windows is authentic Windows software that is properly licensed and legally installed. Learn more about the special benefits reserved for genuine Windows customers by visiting [www.microsoft.com/genuine](www.microsoft.com/genuine).
genuine Windows® XP Professional
Intel® Centrino® Duo Processor Technology
		Intel® Core™2 Duo processor
Mobile Intel® GM965 Express chipset
Intel® Wireless WiFi Link 4965AGN network connection
Processor
		Intel® Core™2 Duo Processor T7300
(4MB L2 cache, 2.0GHz, 800MHz FSB)
Chipset
		Mobile Intel® GM965 Express
Memory
		1GB (1GB installed in one of two memory slots) DDR2 667 SDRAM

User upgradeable up to 4GB (one 2GB memory card in each slot)* subject to availability of 2GB cards

*If upgrading after initial purchase, one or more of the memory cards provided with the system may have to be replaced with optional larger memory cards in order to achieve the maximum capacity.
Storage
		120GB* hard drive with Acer® DASP (Disk Anti-Shock Protection)

Modular variable-speed Super-Multi drive (DVD+R, DVD-R, DVD-RAM):
-Read – 24X CD-RW, 24X CD-ROM, 24X CD-R, 8X DVD-ROM, 8X DVD-R, 8X DVD+R, 6X DVD-ROM DL (double-layer), 6X DVD-R DL (double-layer), 6X DVD+R DL (double-layer), 6X DVD-RW, 6X DVD+RW, 5X DVD-RAM
-Write – 24X CD-R, 16X CD-RW, 8X DVD-R, 8X DVD+R, 4X DVD-R DL (double-layer), 4X DVD+R DL (double-layer), 6X DVD-RW, , 8X DVD+RW, 5X DVD-RAM

5-in-1 card reader for optional MultiMediaCard™, Secure Digital card, Memory Stick®, Memory Stick PRO™ or xD-Picture Card™

Optional external USB 1.44MB* floppy drive

*When referring to storage capacity, GB stands for one billion bytes and MB stands for one million bytes. Some utilities may indicate varying storage capacities. Total user-accessible capacity may vary depending on operating environments.
Video
		12.1" WXGA (1280 x 800) TFT LCD, up to 16.7 million colors

Integrated Intel® Graphics Media Accelerator X3100

Microsoft® DirectX® 9.0 and DirectX® 10.0 support

VGA and S-video TV-out ports

Support for simultaneous display on notebook LCD and external monitor
Audio
		Acer® PureZone technology with two integrated stereo microphones featuring beam-forming, echo-cancellation and noise-suppression technologies

Two integrated Acer® 3DSonic stereo speakers

Headphones/speakers/line-out and microphone/line-in ports

Microsoft® DirectSound® compatibility
Interface Ports
		DC-in
RJ-11 modem
RJ-45 LAN
VGA
Headphones/speakers/line-out
Microphone/line-in
S-video TV-out
FireWire® (IEEE 1394)
FIR (fast infrared)
Three USB 2.0
Connector for optional ezDock II Docking Station
Card Slots
		Type II PC Card slot

5-in-1 card reader for optional MultiMediaCard™, Secure Digital card, Memory Stick®, Memory Stick PRO™ or xD-Picture Card™
Communications
		Intel® Wireless WiFi Link 4965AGN network connection supporting 802.11a/b/g/Draft N wireless LAN, Acer® SignalUp technology for enhanced antenna efficiency

Bluetooth® 2.0 + EDR (enhanced data rate) wireless PAN

Gigabit LAN, Wake-on-LAN ready

V.92 56Kbps* data/fax modem, PTT (postal, telegraph, telephone) certified in select countries, Wake-on-Ring ready

*Download speeds are limited to 53Kbps. Actual speeds may vary depending on line conditions. Uploads travel at speeds up to 33.6Kbps. Requires compatible digital sources.
Included Software
		Acer® Bio-Protection Acer® Empowering Technology (eDataSecurity, eLock, eRecovery, eSettings, eNet, ePower, ePresentation)
Acer® GridVista
Acer® Launch Manager
Acer® PureZone
Adobe® Acrobat® Reader
CyberLink® PowerDVD™*
Norton Internet Security™*
NTI CD-Maker™*

*OEM, not full-featured, version.
User Interface
		84-key, inverted T cursor layout, embedded numeric keypad, hotkey controls, 2.5mm minimum key travel, international language support

12 function, four cursor, two Microsoft® Windows® keys

Empowering Key

Web browser, e-mail, WLAN, user-programmable easy-launch buttons

Seamless touchpad with four-way integrated scroll button and Acer® Bio-Protection fingerprint reader
Dimensions
		12.0" (306.0mm) W x 8.9" (227.0mm) D x 1.1" – 1.4” (27.5mm – 34.5mm) H
Power
		65-watt AC adapter

Nine-cell lithium ion battery: up to 7.0 hours life depending on configuration and usage; 2.5 hours recharge time with power off, 3.5 hours with power on
Compliance
		ACPI (Advanced Configuration and Power Interface) 3.0
DMI (Desktop Management Interface) 2.0
Mobile PC2002
Wi-Fi CERTIFIED™

---

### Post by gn2 on 2008-01-20
Have you added Libdvdcss2? 
Instructions here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by cotcot on 2008-01-20
I got dvd play back on 64 bit with ```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse libdvdcss2
```

---

### Post by glenna on 2008-01-20
THANKS!!!  Finally it works!!  I uninstalled totem, ran the code, reinstalled totem and ungraded to xine and works!!  Totem won't play all movies, but VLC does!!!

Thanks again!!!

---

