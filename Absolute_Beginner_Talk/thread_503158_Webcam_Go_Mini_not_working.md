---
title: "Webcam Go Mini not working"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by m4oz on 2007-07-17
I have an internet camera webcam go mini creativ.It is very old but it still works. unfortunately not on ubuntu.On a different  forum some one advised me to instal qcam(QuickCam). Bouth that whots wappend in terminal: 

dmesg|tail
paul@abbalah-doon:~$ sudo dmesg|tail
[   55.472206] Bluetooth: RFCOMM socket layer initialized
[   55.472219] Bluetooth: RFCOMM TTY layer initialized
[   55.472222] Bluetooth: RFCOMM ver 1.8
[   66.055464] eth0: no IPv6 routers present
[   82.585539] UDF-fs: No VRS found
[   82.851673] ISO 9660 Extensions: Microsoft Joliet Level 3
[   83.178377] ISO 9660 Extensions: RRIP_1991A
[  148.717686] ubuntu/media/ov511/ov511.c: No decompressor available
[  148.856280] ubuntu/media/ov511/ov511.c: No decompressor available
[  148.994873] ubuntu/media/ov511/ov511.c: No decompressor available

lsusb:
paul@abbalah-doon:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05a9:0518 OmniVision Technologies, Inc. OV518 WebCam
Bus 001 Device 001: ID 0000:0000  
paul@abbalah-doon:~$ 

When I rum webcam drivers installd from synaptic:
paul@abbalah-doon:~$ sudo webcam
reading config file: /home/paul/.webcamrc
v4l2: open /dev/video0: Function not implemented
v4l2: open /dev/video0: Function not implemented
v4l: open /dev/video0: Function not implemented
no grabber device available


Plz help!

---

### Post by linuxwizard on 2007-07-17
Try EasyCam 

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by m4oz on 2007-07-17
Thx

---

