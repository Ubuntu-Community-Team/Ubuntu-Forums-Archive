---
title: "installing drapihcs card"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by baskettplayr on 2007-05-31
sry for  the double post but i bumped the last one which wasnt smart so here it is again...
ok i'm trying to install a intel media accerator/ graphics card this what the dianogsitcs report said from my xp so u guys know what i need...
> 	Intel(R) Graphics Media Accelerator Driver Report


Report Date:		05/29/2007
Report Time[hr:mm:ss]:	19:29:18
Driver Version:		6.14.10.4764
Operating System:		Windows XP* Home Edition, Service Pack 2 (5.1.2600)
Default Language:		English
DirectX* Version:		9.0
Physical Memory:		501 MB
Minimum Graphics Memory:	8 MB
Maximum Graphics Memory:	128 MB
Graphics Memory in Use:	9 MB
Processor:		x86
Processor Speed:		3333 MHZ
Vendor ID:		8086
Device ID:		2582
Device Revision:		04


*   Accelerator Information   *

Accelerator in Use:		Intel(R) 82915G/GV/910GL Express Chipset Family
Video BIOS:		1295
Current Graphics Mode:	1024 by 768 True Color (60 Hz)



*   Devices Connected to the Graphics Accelerator   *


Active Monitors: 1


*   Monitor   *

Monitor Name:		Plug and Play Monitor
Display Type:		Analog
Gamma Value:		2.29
DDC2 Protocol:		Supported
Maximum Image Size:	Horizontal: 11.0  inches
			Vertical:   9.0  inches
Monitor Supported Modes:
640 by 480 (60 Hz)
640 by 480 (67 Hz)
640 by 480 (72 Hz)
640 by 480 (75 Hz)
720 by 400 (70 Hz)
800 by 600 (56 Hz)
800 by 600 (60 Hz)
800 by 600 (72 Hz)
800 by 600 (75 Hz)
832 by 624 (75 Hz)
1024 by 768 (60 Hz)
1024 by 768 (70 Hz)
1024 by 768 (75 Hz)
Display Power Management Support:
	Standby Mode:	Not Supported
	Suspend Mode:	Not Supported
	Active Off Mode: Supported

* Other names and brands are the property of their respective owners.                                                                                                                                                                                               

then on another thread a kid said i needed to type "lspci -v | less", then scroll down until you find something relating to graphics... and i did and this is what i got ..... > 00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller
 Hub (rev 04)
        Subsystem: Gateway 2000 Unknown device 4038
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated 
Graphics Controller (rev 04) (prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 4038
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 30200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ffe0 [size=8]
        Memory at 20000000 (32-bit, prefetchable) [size=256M]
        Memory at 30280000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High
 Definition Audio Controller (rev 03)
        Subsystem: Gateway 2000 Unknown device 4038
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 302c0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

now what do i do and if i could i would like to install that hd audio too or does this mean there installed?

---

### Post by kernel tom on 2007-05-31
here is my answer again... messed up the order last time

sudo apt-get install xserver-xorg-video-intel

---

### Post by baskettplayr on 2007-06-01
how do i know if it worked? this is what it said
> kodey@kodey:~$ sudo apt-get install xserver-xorg-video-intel
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xserver-xorg-video-i810
The following NEW packages will be installed:
  xserver-xorg-video-intel
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 188kB of archives.
After unpacking 73.7kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe xserver-xorg-video-intel 2:1.9.94-1ubuntu3 [188kB]
Fetched 188kB in 4s (45.2kB/s)                         
dpkg: xserver-xorg-video-i810: dependency problems, but removing anyway as you request:
 xserver-xorg-video-all depends on xserver-xorg-video-i810 | xserver-xorg-video-intel; however:
  Package xserver-xorg-video-i810 is to be removed.
  Package xserver-xorg-video-intel is not installed.
(Reading database ... 133275 files and directories currently installed.)
Removing xserver-xorg-video-i810 ...
Selecting previously deselected package xserver-xorg-video-intel.
(Reading database ... 133266 files and directories currently installed.)
Unpacking xserver-xorg-video-intel (from .../xserver-xorg-video-intel_2%3a1.9.94-1ubuntu3_i386.deb) ...
Setting up xserver-xorg-video-intel (1.9.94-1ubuntu3) ...



---

### Post by kernel tom on 2007-06-01
you have to reboot, reconfigure your xorg.conf file to use the "intel" device

sudo dpkg-reconfigure xserver-xorg

---

### Post by baskettplayr on 2007-06-01
so after i reboot just enter that in ?

---

### Post by kernel tom on 2007-06-01
yes

through the terminal, after u edit ur xorg file then reboot, you should be set

---

### Post by baskettplayr on 2007-06-01
its asking this.... >                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; The X server configuration file associates your video card with a name    &#9474;  
 &#9474; that you may provide.  This is usually the vendor or brand name followed  &#9474;  
 &#9474; by the model name, e.g., "Intel i915", "ATI RADEON X800", or "NVIDIA      &#9474;  
 &#9474; GeForce 6600".                                                            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Identifier for your video card:                                           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Generic Video Card_______________________________________________________ &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>                                     &#9474;  
 &#9474;                                      
what should i type???

---

### Post by baskettplayr on 2007-06-01
hello?

---

### Post by kernel tom on 2007-06-01
the name of your video card....

---

### Post by baskettplayr on 2007-06-01
soo like..... Intel(R) 82915G/GV/910GL or
Intel(R) 82915G/GV/910GL Express Chipset Family

---

### Post by kernel tom on 2007-06-01
your graphic card seems to be Intel GMA 915G... ha you don't know what it is?

---

### Post by baskettplayr on 2007-06-01
lol hey!!! i kno im a noob

---

### Post by baskettplayr on 2007-06-01
what about for this? 
>          &#9484;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                     
                    &#9474; Video card's bus identifier:        &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474; PCI:0:2:0__________________________ &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;               <Ok>                  &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;                     
                                                                      

---

### Post by kernel tom on 2007-06-01
leave everything else the way it is... the only things you should have to change are ur device name, the name of ur card, and the resolutions u want for ur card

---

### Post by baskettplayr on 2007-06-01
so leave this the same too?
>                                                                          
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; Typically, the amount of dedicated memory used by the video card is       &#9474;  
 &#9474; autodetected by the X server, but some integrated video chips (such as    &#9474;  
 &#9474; the Intel i810) have little or no video memory of their own, and instead  &#9474;  
 &#9474; borrow main system memory for their needs.                                &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; This parameter should usually be left blank and specified only if the     &#9474;  
 &#9474; video card lacks RAM, or if the X server has trouble autodetecting the    &#9474;  
 &#9474; RAM size.                                                                 &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Amount of memory (kB) to be used by the video card:                       &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; _________________________________________________________________________ &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>                                     &#9474;  
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  
                                                                                
                                                                                
                                                                                
                                                                                



---

### Post by kernel tom on 2007-06-01
yes

---

### Post by baskettplayr on 2007-06-01
are you sure not 128 mb?

---

### Post by kernel tom on 2007-06-01
trust me

---

### Post by baskettplayr on 2007-06-01
what about this?
>                                                                     
                                                                                
                                                                                
                                                                                
                                                                                
                                                                                
                                                                                
                    &#9484;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                     
                    &#9474; Keyboard model:                     &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474; pc105______________________________ &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;               <Ok>                  &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;                     
                                                                                
                                                                                
                            

---

### Post by kernel tom on 2007-06-01
trust me i've been through the setup a million times, the only things you have to worry about are driver, card name, and resolutions...

the file already knows the rest

---

### Post by loathsome on 2007-06-01
Just LEAVE things like they are.

And Intel GMA950 is supported out-of-the-box in Feisty??

---

### Post by kernel tom on 2007-06-01
in my experience, it was only "partway" supported... had to get the drivers, then there was a noticable difference in video quality, resolution choices, and graphics

---

### Post by baskettplayr on 2007-06-01
well for resolution which one is it?
>  Please keep only the resolutions you would like the X server to use.     &#9474;  
  &#9474; Removing all of them is the same as removing none, since in both cases   &#9474;  
  &#9474; the X server will attempt to use the highest possible resolution.        &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; Video modes to be used by the X server:                                  &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;    [ ] 1920x1440                                                     &#8593;   &#9474;  
  &#9474;    [ ] 1920x1200                                                     &#9646;   &#9474;  
  &#9474;    [ ] 1856x1392                                                     &#9618;   &#9474;  
  &#9474;    [ ] 1792x1344                                                     &#9618;   &#9474;  
  &#9474;    [ ] 1680x1050                                                     &#9618;   &#9474;  
  &#9474;    [ ] 1600x1200                                                     &#9618;   &#9474;  
  &#9474;    [ ] 1440x900                                                      &#9618;   &#9474;  
  &#9474;    [ ] 1400x1050                                                     &#8595;   &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;                                  <Ok>                                    &#9474;  
  &#9474;                                                                          &#9474;  
  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  
                                            

---

### Post by kernel tom on 2007-06-01
go up to the highest resolution ur monitor and graphic card support... then select all the ones underneath it to using the space bar

---

### Post by baskettplayr on 2007-06-01
kk finished now do i have to restart again?

---

### Post by kernel tom on 2007-06-01
yea then it will load ur newly configured xorg file

now just hope it works

---

### Post by baskettplayr on 2007-06-01
how do u load xorg?

---

### Post by fastpakr on 2007-06-01
Save the file, it'll load the new settings on restart.

---

### Post by kernel tom on 2007-06-01
xorg.conf is automatically loaded everytime you boot ur computer, and the way u configured it automatically saves it too

so all u need to do is reboot

---

### Post by baskettplayr on 2007-06-01
i resstarted and nothing popped up so i guess its all good.... ty

---

### Post by kernel tom on 2007-06-01
yea should be all worked out now... if u got the graphical interface when u rebooted u should be good to go

---

### Post by baskettplayr on 2007-06-01
ididnt get a graphical interface

---

### Post by fastpakr on 2007-06-01
Instead of telling us what you didn't get, how about telling us exactly what you DID get?

---

### Post by kernel tom on 2007-06-01
do you see your desktop? you are fine

---

### Post by baskettplayr on 2007-06-01
lol ok i hit restart and it shut down then started back up i logged in and it started like normal but nothing poped up

---

### Post by loathsome on 2007-06-01
What the heck are you talking about?

---

### Post by baskettplayr on 2007-06-01
what i was saying was something suppose to pop up after i restarted my computer?

---

### Post by loathsome on 2007-06-02
> **baskettplayr said:**
> what i was saying was something suppose to pop up after i restarted my computer?
No.

---

