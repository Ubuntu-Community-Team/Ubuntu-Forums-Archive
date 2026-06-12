---
title: "wobbly scrolling with edgy left and feisty fawn"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by relativity on 2007-02-09
I have been having this problem since edgy left and it continues with feisty fawn. When I scroll in any window the window wobbles, the scrolling is not smooth. It makes using browsers difficult. Is there any anyway to fix this or is it just that my hardware is not capable enough? I have the same problem to a lesser extent with openSuse 10.2 but no problem with sabayon o fedora 6/7.

---

### Post by shareMenaPeace on 2007-02-09
Can you provide a little more info please,
What are your hardware specs?

to find out post the content of

lspci

Also check your system Xorg.0.log - todo this see
System -> Administration -> System Log 
Check Xorg.0.log and browse the file for lines beginning with EE or WW - post those errors aswell.

And post a screenshot

---

### Post by relativity on 2007-02-09
Thanks for the reply 

From lspci 

```
 
 sudo lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)

``` 

xorg.log  


```
 
*(WW) (1920x1440,SyncMaster) mode clock 234MHz exceeds DDC maximum 110MHz

(WW) (1280x1024,SyncMaster) mode clock 135MHz exceeds DDC maximum 110MHz
(WW) (1280x1024,SyncMaster) mode clock 157.5MHz exceeds DDC maximum 110MHz

(EE) AIGLX: Screen 0 is not DRI capable

(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom

```

---

