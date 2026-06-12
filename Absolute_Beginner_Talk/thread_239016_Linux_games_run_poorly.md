---
title: "Linux games run poorly"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by jd65pl on 2006-08-18
Hi,

I have on board graphics (128mb) which I know wont help matters a 2Ghz processor and 1gig of ram. games in windows used to play fine. Movies and other resource heavy tasks work fine but when I play any linux game (out of repositories) my computer just slows up painfully. Any one got any ideas on how to sort this.

---

### Post by muep on 2006-08-18
Have you installed the correct graphics drivers?

Can you give the exact model of your graphics chip? Is it an Intel integrated one or some Geforce? At least Nvidias and ATis need a different than default driver to work well.

If you run this in the Terminal, what does it print? 
lspci

---

### Post by meng on 2006-08-18
Perhaps these are games that depend on 3D acceleration which isn't enabled on your system, I'm just guessing of course. Presumably games like solitaire aren't that slow.

---

### Post by zxee on 2006-08-18
What is the video card (GPU) and what is called out as a driver in device /etc/X11/xorg.conf?

---

### Post by mdelorme on 2006-08-18
Most games (if they are 3D, and even quite a few that are not) are written to utilize OpenGL.  If you do not have 3D hardware acceleration and the appropriate drivers, OpenGL will run poorly and cause your gameplay to suffer.

---

### Post by Klaidas on 2006-08-18
Hmm
I had this problem some time ago (on a default install)
But after installing the new kernel and drivers for Nvidia everything works fine, yay!

---

### Post by EdThaSlayer on 2006-08-18
What type of game were you playing?Was it 3D?
Or was it 2D?Did you install the graphics drivers?(Nvidia needs a unique driver...so does ATI)

---

### Post by Klaidas on 2006-08-18
> **EdThaSlayer said:**
> What type of game were you playing?Was it 3D?
Or was it 2D?Did you install the graphics drivers?(Nvidia needs a unique driver...so does ATI)

Penguin racer, trigger, etc. Actually, I don't really like linux games, but I just wanted to try.

I installed Nvidia's drivers for a new kernel. (686)

---

### Post by jd65pl on 2006-08-18
```
lspci
```

jamie@jamie-laptop:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03 )
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media I O] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev  a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound  Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fa st Ethernet (rev 91)
0000:00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controlle r (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741 /760/761 PCI/AGP VGA Display Adapter
0000:02:00.0 Network controller: 3Com Corporation 3com 3CRWE154G72 [Office Conne ct Wireless LAN Adapter] (rev 01)


How do I turn on 3D acceleration? I think Klaidas might be right are these games worth it?

---

