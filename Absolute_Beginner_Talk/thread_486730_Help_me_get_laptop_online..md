---
title: "Help me get laptop online."
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-06-28
New install, need to get wireless going because it's the only way it can connect. In 'network settings' it's not showing a wireless option.

---

### Post by aberadam on 2007-06-28
terminal > iwconfig 

lo                 no wireless extensions.

eth0            no wireless extensions.

---

### Post by aberadam on 2007-06-28
persiaeus@ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) 
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03) 
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) 
02:01.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02) 
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01) 
persiaeus@ubuntu:~$

---

### Post by hyper_ch on 2007-06-28
can you make a screenshot of the "network settings"? Looks to me like your wifi card is recognized...

---

### Post by aberadam on 2007-06-28
Thanks for the reply, here is is: 

[IMG]http://img407.imageshack.us/img407/7963/screenshotte2.png[/IMG]

---

### Post by speaker219 on 2007-06-28
You need "ndiswrapper" if the card does not have a driver for linux.
ndiswrapper allows you to use windows drivers in linux.

---

### Post by speaker219 on 2007-06-28
Run the command in terminal:
```
sudo apt-get install ndiswrapper
```
then download the drivers for your wireless lan card:
[http://www.laptopvideo2go.com/forum/index.php?showtopic=7172&pid=47416&st=0&](http://www.laptopvideo2go.com/forum/index.php?showtopic=7172&pid=47416&st=0&)
then extract the files from the zip file.
go back to terminal and type:
```
sudo ndiswrapper -i i2220.sys
```
then ndiswrapper should install the driver for your wireless card
to make sure the driver is installed and the hardware is working:
```
sudo ndiswrapper -l
```
you should see "Driver installed, hardware present"
then run
```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo echo ndiswrapper >> /etc/modules
```
the wifi light on your laptop (if you have one) should have turned on and your wireless should be working

---

### Post by aberadam on 2007-06-28
Yeah, but the serialmonkey drivers may work... I don't want to use ndiswrapper unless I have to.

---

### Post by aberadam on 2007-06-28
Thankyou speaker, but the laptop's not connected to the internet, I'm using another computer right now.  Could you tell me how to get, transfer, and install ndiswrapper and the drivers on the laptop using a USB stick from this internet-connected PC. 

Thanks, I'm a beginner at this.

---

### Post by speaker219 on 2007-06-28
It's probably going to be alot more difficult to manually transfer over everything you need. Is there any way you can connect an ethernet cable to your laptop (ethernet is recognized in your networking settings). Otherwise, you could download the .deb files and the dependencies on your other computer and put them on your USB stick, and then run them on your laptop. You will need ndiswrapper-source, ndiswrapper-common, and ndiswrapper-utils, including all of the dependencies needed for those packages. You can download the packages and their dependencies here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Scroll down and use the search box to find ndiswrapper-source, and the other packages I listed above.
It would still be much easier if you could get an ethernet cable hooked up to your laptop =)
by the way, nice background =P

---

### Post by aberadam on 2007-06-28
I've connected an ethernet cable, and the laptop is showing up on it, but it won't connect because it won't accept the password. 

Would this be a way to get the laptop temporarily online to download ndiswrapper and the driver?

---

### Post by aberadam on 2007-06-28
Oh, actually no, I don't think there's a connection.  I'm getting confused. 

I'd have to do it all manually.

---

### Post by sci-fi guy on 2007-06-28
I know this sounds stupid, but is your WiFi switched on? On my Toshiba Satellite, there is a manual on/off switch on the case for the WiFi.

---

### Post by aberadam on 2007-06-28
Thanks a lot guys but he's decided he doesn't have the time to let me mess about with it getting it to work so he's put XP back on. 

Reader, [here's the foggy forest wallpaper if you want it. :)]("http://img517.imageshack.us/img517/7272/00663ghostfog1280x1024ol1.jpg")

---

### Post by aberadam on 2007-06-28
The button was switched on Sci Fi.

---

### Post by aberadam on 2007-06-28
He just put XP back on and it worked. 

Shame Ubunu doesn't come with ndiswrapper, I wonder why it doesn't...

---

