---
title: "Optimus/Nvidia laptop summary - do not upgrade to proprietary nvidia driver"
date: 2011-09-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ongchinonn on 2011-09-11
Optimus is a Nvidia Hybrid graphic technology and it’s currently [not supported]("http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work") by Ubuntu 11.04 straight away after installation.  


To check your laptop whether have hybrid graphic use command  
> lspci –vnnn | grep VGA  
it will have shown something like below(this is Asus U46SV with Geforce GT540M 1G)   
> 02:00.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] 
01:00.0 VGA compatible controller [0300]: nVidia Corporation [10de:0df4]
Because of the bug on Jockey(System -> Administration -> Additional drivers) , it will prompt you to install proprietary nvidia driver.  If you install, a reboot will cause system not able to boot into Unity which require OpenGL support – mostly after that you will need to boot into recovery mode – with Unity classic session. It’s mostly because Intel driver is used for primary purpose, two graphic card can’t be used at the same time.  
To check whether Nvidia graphic driver is loaded by X server correctly, 
in /var/log/Xorg.0.log 
You may see something similar(in short)  
> 
(--) PCI:*(0:0:2:0) 8086:0116:1043:1662 rev 9, Mem @ 0xdc400000/4194304, 0xb0000000/268435456, I/O @ 0x0000e000/64 
(--) PCI: (0:1:0:0) 10de:0df4:1043:1662 rev 161, Mem @ 0xdb000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288  
(II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:55:26 PDT 2011  
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs  
(--) using VT number 8  
(EE) No devices detected. 
Fatal server error: 
no screens found  
I have a problem where the Sandy Bridge intel graphic is not set as Primary graphic adapter. I check that intel Sandy Bridge support in 11.04 natty is bad, is there anybody successfully enable it?   The Sandy Bridge Graphic seems like working according to [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=intel_sna_desktops&num=1") 

This [site]("http://www.linuxquestions.org/questions/slackware-14/nvidia-optimus-samsung-rf711-877017/") have talked about the same issue 

This [hybrid graphic wiki ]("http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Main_Page")explain the various approach to enable linux to support Optimus concept on laptop  
Bumblebee/Ironhide is currently the primary linux optimus support 

I able to turn off nvidia graphic manually using the acpi_call method describe in the website below, it depends on the laptop model  [https://launchpad.net/%7Ehybrid-graphics-linux](https://launchpad.net/%7Ehybrid-graphics-linux)  
PS: From this [site]("http://www.techyv.com/questions/nvidia-optimus-inside-ubuntu-maverick") below, it’s said you can use nvidia graphic card as main graphic adapter, I didn’t try it, anyone have this kind of bios?  
> 
Some laptops have a BIOS setting that enables an option to choose either Nvidia Optimus or Intel Integrated graphics chipset. You may have to reinstall Ubuntu to allow reconfiguration of the detected graphics card you have chosen. In this case the switching capabilities will be disabled for all operating systems installed. On some Asus laptops, enter the BIOS by pressing F2 when the ASUS logo appears, go to “Advanced”, select "Boot VGA Controller Selection" and change it from "Windows 7" to "Others". Boot into Ubuntu where it will ask you to enable the Nvidia driver. After it installs the driver, reboot once more and test the 3d graphics performance.


---

### Post by realzippy on 2011-09-11
Welcome to UF!
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

I 3/5/7 sandybridge GPUs work fine,
if you run kernel > 2.38.x,and updated mesa,intel driver,libdrm...

Note that bumblebee has forked to 
ironhide and bumblebee_stable.

bumblebee_stable refuses to use the ACPI_call stuff,since
they call it ugly hacking...

---

### Post by ongchinonn on 2011-09-11
Ya, it's working fine now, i forgot to back up my xorg.conf so i need to manually change it to Intel graphic.

Question: 
For Ironhide installation, do i need to install nvidia-current and nvidia-settings myself before install it? 

What is recommended nvidia driver installation for ironhide, download binary from website or from ubuntu ppa? 

The nvidia driver seems like will change the xorg.conf - change the device to nvidia - after the installation.

I try install ironhide on 11.04 before, it will create configure file with name xorg.conf.nvidia, what is the usage of it? 

Thanks.

---

### Post by realzippy on 2011-09-12
Ironhide should install nvidia-driver itself.
The created xorg.conf.nvidia is used by the 2nd Xserver which starts when you run an application with ironhide/nvidia-card.
Don't know the command for ironhide (prefer bumblebee_stable),but
in old bumblebee (now ironhide) it was
```
optirun *application*
```
eg
```
optirun glxspheres
```

---

### Post by markc on 2011-11-14
So how would I run my whole Ubuntu 11.10 desktop via optirun?

I have it working on an Asus N53SV and get about 315fps with glxgears (only 75fps with glxspheres) but I want my entire desktop and all applications to use the nVidia gfx and driver.

---

### Post by lokutus25 on 2011-11-14
> **markc said:**
> So how would I run my whole Ubuntu 11.10 desktop via optirun?

I have it working on an Asus N53SV and get about 315fps with glxgears (only 75fps with glxspheres) but I want my entire desktop and all applications to use the nVidia gfx and driver.

Yep. That's the question I'm asking too. I mean, I don't care about the battery duration, I just need performance. My eeePC 1215N seems doesn't have a BIOS feature to disable one of the Graphic Card. I'd like to use only the NVIDIA card...but I still can't understand how.
Any help?

---

### Post by markc on 2011-11-14
It may be possible to put something like this in ~/.xinitrc and use startx to kick off the desktop.
```
exec optirun gnome-session --session=ubuntu-2d

```
I'd try it but I'm using my normal Archlinux desktop atm and I'm not sure about the best way to temporarily disable lightdm from starting up.

---

### Post by Nico0020 on 2011-12-02
so as of no, to get use out of my video card after installing ironhide, i have to run the optirun with specific programs? 

I am almost never running off my battery, so did anyone figure out a proper way to just have the driver running at all times during a session, thus controlling all programs started and the desktop environment in general?

---

