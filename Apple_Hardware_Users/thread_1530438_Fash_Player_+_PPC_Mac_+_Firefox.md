---
title: "Fash Player + PPC Mac + Firefox ???"
date: 2010-07-13
forum: Apple Hardware Users
---

### Post by 828688 Ben on 2010-07-13
Here are the specs of my computer (no sure if they're necessary, but why not): > 
Hardware Overview:

  Model Name:	Power Mac G5
  Model Identifier:	PowerMac7,3
  Processor Name:	PowerPC G5  (3.0)
  Processor Speed:	2 GHz
  Number Of CPUs:	2
  L2 Cache (per CPU):	512 KB
  Memory:	1.5 GB
  Bus Speed:	1 GHz
  Boot ROM Version:	5.2.4f1

ATA Bus:

PIONEER DVD-RW  DVR-109:

  Model:	PIONEER DVD-RW  DVR-109
  Revision:	A912
  Detachable Drive:	No
  Protocol:	ATAPI
  Unit Number:	0
  Socket Type:	Internal
  Low Power Polling:	Yes
  Power Off:	No

PIONEER DVD-RW  DVR-109:

  Firmware Revision:	A912
  Interconnect:	ATAPI
  Burn Support:	Yes (Apple Shipping Drive)
  Cache:	2000 KB
  Reads DVD:	Yes
  CD-Write:	-R, -RW
  DVD-Write:	-R, -RW, +R, +R DL, +RW
  Write Strategies:	CD-TAO, CD-SAO, CD-Raw, DVD-DAO
  Media:	Insert media and refresh to show available burn speeds

ATI Radeon 9600:

  Chipset Model:	ATY,RV351
  Type:	Display
  Bus:	AGP
  Slot:	SLOT-1
  VRAM (Total):	128 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x4150
  Revision ID:	0x0000
  ROM Revision:	113-A58504-112
  Displays:
HF237:
  Resolution:	1920 x 1080 @ 60 Hz
  Depth:	32-Bit Color
  Core Image:	Hardware Accelerated
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported
  Rotation:	Supported
Display Connector:
  Status:	No Display Connected

Has _**ANYONE**_ made any headway on getting flash working on a PPC mac????

I WILL TRY ANYTHING!!!!

Thanks for the help,
Ben

---

### Post by linuxopjemac on 2010-07-13
forget flash. If you are in Lucid Lynx, you might want to try midori browser. It can handle html5 youtube video. I am hoping that lightspark will be ported to PPC one day...

---

### Post by barbaGNU on 2010-07-13
sad to say but i moved away from ubuntu. 
Now i've a working gnash plugin (gnash builded against ffmpeg with altivec support) on firefox that is quite usable on my _new_ dual 1.8 g5 with standard nv drivers without hw dri. It works (100% cpu) on my iBook too with radeon dri.

---

### Post by barbaGNU on 2010-07-14
ok, as asked in PM i'm now going to post a new reply.
now i'm using a different distro (the name is in my signature) on my ppc machines and this one has a different target from ubuntu. It's source based and is very hard to understand.
As 98% of gnu/linux distributions is free software thus everybody can read and study their sources (they named Pkgfile) to build a working gnash.

here two screenshot using the_gimp:
[firefox+gnash ]("http://i30.tinypic.com/2v96lvt.jpg")
[firefox+openjdk6+openoffice]("http://i28.tinypic.com/avo8eq.jpg")

---

### Post by sha.goyjo on 2010-07-14
BarbaGNU, I know there are ways to hand-compile gnash to work better than it does from the ubuntu repos. Could you perhaps post a thread with a how-to of how you compiled it?

---

### Post by barbaGNU on 2010-07-15
> **sha.goyjo said:**
> BarbaGNU, I know there are ways to hand-compile gnash to work better than it does from the ubuntu repos. 
i didn't compiled it by hand, i simply used cruxppc's port manager:
```
# ilenia -U gnash firefox-flash-plugin
```> 
Could you perhaps post a thread with a how-to of how you compiled it? i cannot, i moved to a gnu/linux distro that really supports my preferred arch. Maybe i'll move again in the next future.
You can read/study/understand how cruxppc uses to compile gnash (and its own deps) and then you are free to write by yourself that howto.

Anyway, if you have no skill or no free time, i suggest to use: [http://www.canonical.com/consumer-services/support](http://www.canonical.com/consumer-services/support)

---

