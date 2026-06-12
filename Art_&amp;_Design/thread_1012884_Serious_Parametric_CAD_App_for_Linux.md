---
title: "Serious Parametric CAD App for Linux?"
date: 2008-12-16
forum: Art &amp; Design
---

### Post by BastardNamban on 2008-12-16
I know from looking around a lot of others thought like me and wanted CAD on linux. It seems as though there are a bunch: [http://www.tech-edv.co.at/lunix/CADlinks.html](http://www.tech-edv.co.at/lunix/CADlinks.html)

I've used Autodesk Inventor, and I was thinking of buying a copy when I converted to pure Ubuntu. My question is, is there anything out there free, or COMMERCIALLY available for Linux that is on par with something like Autodesk? It seems like most of those CAD builds are in various stages of development, or simplistic- ideally, I'm looking for a parametric CAD modeler, with support for toolpath instructions, and able to save in multiple cross-formats like Inventor. If there isn't anything solid yet, has anyone tried using Autodesk stuff in linux with Wine? How did that work out for you, any issues?

Any thoughts?

---

### Post by BastardNamban on 2008-12-17
I take it from lack of reply, means I'm screwed? So no solution exists huh?

---

### Post by Peter76 on 2008-12-17
At the moment there is an absolute lack of an up to standards cad program. I use Qcad a lot, which suits my needs, but it is only 2d. Bricscad is going to release a linux version of their software which looks very promising, but that'll probably take another year.

---

### Post by cb951303 on 2008-12-17
There are 2 pro-level mechanical CADs for linux

1. [Unigraphics NX (Siemens)]("http://www.plm.automation.siemens.com/en_us/products/nx/")
2. [VariCAD]("http://www.varicad.com/en/home/")

Unigraphics is an all in one package CAD/CAM/CAE and by my experiences it's on par with CATIA.

---

### Post by BastardNamban on 2008-12-17
Unigraphics looks overly complex (for me), and I'm not sure it supports parametric modeling. I fear the price!

Varicad's interface looks great, but the same thing, and no mechanical simulation :( It is affordable, though, as CAD goes, which is nice.

Any good freeware CAD for linux that supports mechanical simulation and both 3D and 2D creation? With all those various builds, I would think there's something out there....?

---

### Post by ussndmac on 2008-12-17
It is interesting that the open source software world is lacking a serious free CAD software of any kind.

There are a few that are commercial, but the reason most of us went to Ubuntu is because we can't )or won't) afford things like that.

I'm told AutoCAD12 & 14 will run in wine. I've not tried my copy yet. I've also not tried my copy of Solidworks98.

Obviously, AutoCAD 12/14 don't address your issue, and probably not SW98 either.

It would be nice if the current owners of Medusa were to make it available as open source...but, I'm not holding my breath. ;-)

Regards,
Mac

---

### Post by BastardNamban on 2008-12-17
I haven't even tried wrapping my head around Wine yet, I only know what it does. I don't know how well it works.

Let's say I bought or had a copy of Autodesk Inventor, and I wanted to run it in linux. How well could Wine do that? Knowing Wine is an emulator, like ZNES, except for Windows instead of a Super Nintendo machine, I know ZNES back when I used it in XP gave me little glitches all the time. I wonder, how well do CAD programs written for windows run in Wine? And how would that work, anyway- a CAD program in Windows has to be installed. Since you can't install that program in linux, how does Wine run it- do you have to install it virtually each time you want to use it in Wine?

---

### Post by cb951303 on 2008-12-17
> **BastardNamban said:**
> I haven't even tried wrapping my head around Wine yet, I only know what it does. I don't know how well it works.

Let's say I bought or had a copy of Autodesk Inventor, and I wanted to run it in linux. How well could Wine do that? Knowing Wine is an emulator, like ZNES, except for Windows instead of a Super Nintendo machine, I know ZNES back when I used it in XP gave me little glitches all the time. I wonder, how well do CAD programs written for windows run in Wine? And how would that work, anyway- a CAD program in Windows has to be installed. Since you can't install that program in linux, how does Wine run it- do you have to install it virtually each time you want to use it in Wine?

wine = Wine Is Not Emulator
it's a compatibility layer between windows and linux.
Inventor doesn't work well with wine: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=5719](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5719)

Seriously though, you can't get a simpler CAD than varicad. And for what it's worth simulation is not the job of a CAD software. There other software for that and they work in linux (i.e. Ansys)
Also I don't think that Autodesk Inventor is any simpler than Unigraphics

cheers):P

---

### Post by grim4593 on 2008-12-17
Well, you could always try using Inventor in a virtual machine. Granted, the 3d performance is going to be abysmal so I am not sure how usable it will be. I have used AutoCAD in a virtual machine for mostly 2d stuff and it has performed okay.

---

### Post by cb951303 on 2008-12-17
> **grim4593 said:**
> Well, you could always try using Inventor in a virtual machine. Granted, the 3d performance is going to be abysmal so I am not sure how usable it will be. I have used AutoCAD in a virtual machine for mostly 3d stuff and it has performed okay.

inventor uses hardware acceleration. it wouldn't work

---

### Post by sges on 2008-12-17
Perhaps an IntelliCAD variant (Commercial)?

Brincsys has a Linux version of IntelliCAD under their own brand. The Linux version is a bit behind the Windows version but you can download a free trial.

[http://www.bricscad.com/](http://www.bricscad.com/) 

You will have to use **alien** to convert the .rpm to .deb. 


You could also try VARKON which is in the repository.

---

### Post by sges on 2008-12-17
You could also try VariCAD [http://www.varicad.com](http://www.varicad.com)

---

### Post by Peter76 on 2008-12-17
The good news is that as of today Virtual Box has support for harware acceleration with XP or Vista as guest. This might make it better to run cad in a virtual machine

---

### Post by cb951303 on 2008-12-17
> **Peter76 said:**
> The good news is that as of today Virtual Box has support for harware acceleration with XP or Vista as guest. 

great news :popcorn:

---

