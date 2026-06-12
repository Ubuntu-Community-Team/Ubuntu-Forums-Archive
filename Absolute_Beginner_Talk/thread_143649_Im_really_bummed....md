---
title: "Im really bummed..."
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by maddog39 on 2006-03-12
Hello all,

Okay so I get alot of support from members, after a week I finally get my CDs to boot and I am so happy, the weekend comes, I get my new HD, install it, i install Ubuntu 5.10 Breezy on it, it boots and oh no, X-server wont start because of a graphics issue. I go on the Ubuntu Wiki site, look at supported video cards in hardware and theres my chipset, un-supported, nVidia GeForce 6100. That just ruined my day, I wanted Linux SO BAD and it doesnt work on my computer. :( :cry: I even tried the Mac version but the installer doesnt let me resize the main partition so I couldnt do it on my Apple Laptop. This sucks more than anything, cuz just thinking about windows gets me pissed off, LOL. If anyone has advice for me im all ears..

-maddog39

---

### Post by mstlyevil on 2006-03-12
[QUOTE=maddog39]Hello all,

Okay so I get alot of support from members, after a week I finally get my CDs to boot and I am so happy, the weekend comes, I get my new HD, install it, i install Ubuntu 5.10 Breezy on it, it boots and oh no, X-server wont start because of a graphics issue. I go on the Ubuntu Wiki site, look at supported video cards in hardware and theres my chipset, un-supported, nVidia GeForce 6100. That just ruined my day, I wanted Linux SO BAD and it doesnt work on my computer. :( :cry: I even tried the Mac version but the installer doesnt let me resize the main partition so I couldnt do it on my Apple Laptop. This sucks more than anything, cuz just thinking about windows gets me pissed off, LOL. If anyone has advice for me im all ears..

-maddog39[/QUOTE]

I am going to move this thread to a area where you will more likely get the help you need.

---

### Post by kaamos on 2006-03-12
Have you seen this? [https://wiki.ubuntu.com/CommonProblemsGraphics](https://wiki.ubuntu.com/CommonProblemsGraphics)

---

### Post by Bandit on 2006-03-12
Try Dapper flight5. Its still in Beta, but pretty much stable enough for the average joe.. The newer xorg does offer support for that card in 2D.

> Supported Hardware
The nv driver supports PCI and AGP video cards based on the following NVIDIA chips:

RIVA 128
    NV3 
RIVA TNT
    NV4 
RIVA TNT2
    NV5 
GeForce 256, QUADRO
    NV10 
GeForce2, QUADRO2
    NV11 & NV15 
GeForce3, QUADRO DCC
    NV20 
nForce, nForce2
    NV1A, NV1F 
GeForce4, QUADRO4
    NV17, NV18, NV25, NV28 
GeForce FX, QUADRO FX
    NV30, NV31, NV34, NV35, NV36, NV37, NV38 
GeForce 6XXX
    NV40, NV41, NV43, NV44, NV45 
GeForce 7XXX
    G70 


I thought older version ( 6.8 ) still offered 2D support as well. try running with APCI turned off at the installation command line.

Cheers,
Joey

---

### Post by maddog39 on 2006-03-12
I think I forgot to mention though that this is an intergrated chipset. nVidia 6 series (intergrated).

---

### Post by Bandit on 2006-03-12
[QUOTE=maddog39]I think I forgot to mention though that this is an intergrated chipset. nVidia 6 series (intergrated).[/QUOTE]
It should still work in vesa mode regardless.

---

### Post by maddog39 on 2006-03-12
I looked at the CommonVideoProblems FAQ and none of the things in there worked. Also I do not know how to activate vesa mode.

[EDIT]
even more importantly what is vesa mode.

---

### Post by kaamos on 2006-03-12
> Also I do not know how to activate vesa mode.
When in "sudo dpkg-reconfigure xserver-xorg", choose vesa as the driver.

---

### Post by maddog39 on 2006-03-13
Ah, ok. Ill try that. :D

[EDIT]
W00t! Finally I got it to work. Screeny below...
[http://images.dx-h.com/files/1/screenshots/linux_working.png](http://images.dx-h.com/files/1/screenshots/linux_working.png)

Thanks Alot! :D

---

