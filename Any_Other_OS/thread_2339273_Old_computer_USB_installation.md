---
title: "Old computer USB installation"
date: 2016-10-06
forum: Any Other OS
---

### Post by yokelns on 2016-10-06
So I have a problem for you guys/gals. I have an exeptionaly old spare PC: Pentium4 1.6GHz, Radeon 7500Pro AGP Graphics card, 512Mb memory, 30GB hard drive and so on...

I wanted to istall Hydrogen OS onto it from the USB but it seems that the only removable media that the BIOS will boot are: ZIP, LS120, ATAPI MO and maybe something else. So USB is out of the window.

My question is: If I was to connect that 30GB as an external drive to the computer I am using now, could I somehow 'dd' the entire Hydrogen OS onto 30GB hard drive and then just put it back into the old computer?

---

### Post by C.S.Cameron on 2016-10-06
As long as the drive you are dding to is at least as big as the one you are dding to.
You could stick the 30GB drive in another computer for the install then move it.
I would unplug the existing drive first though.

---

### Post by Bucky Ball on 2016-10-07
*Thread moved to **Any Other OS**.*

> Hydrogen Operating System is a portable kernel framework whose components are ELF objects linked to a core providing thread scheduling and memory management in a single addressing space.

Unsure what this has to do with Ubuntu, unless it is using the Ubuntu kernel, but either way, Hydrogen OS is not supported in the specialised support areas here.

---

### Post by kurt18947 on 2016-10-07
Sorry if I'm Captain Obvious here but how about a DVD? If you can't write one, do you have a friend or acquaintance who could? I know optical disks are considered archaic but they still work and are sometimes the best choice, especially on older machines.

---

### Post by yokelns on 2016-10-07
Thx C.S.Cameron! I will definately install the Hydrogen OS by putting it into another computer and then move it to the old one:)

Sorry kurt18947, I forgot to mention that the DVD drive is not working properly, so that option is not possible. I should probably buy a new DVD drive (or at least second hand one that works) since as you stated, it is often the best choice for these old machines.

 Yeeesss...second hand one is probably the only option since motherboard doesn't have SATA connectors, only those old, clunky IDE ones..

Thx for feedback :)

Hey Bucky Ball :) I know it's not Ubuntu but the question, i thought, was more Linux related since I just needed to know weather or not the image file for installation could be dd onto another hard drive. The fact that it happened to be Hydrogen OS was just my specific situation. I thought it might be relevant.

Cheers! :)

---

### Post by C.S.Cameron on 2016-10-08
You can generally move a Linux install disk from machine to machine without problem, as long as no generic drivers have been installed.

---

### Post by kurt18947 on 2016-10-08
> **C.S.Cameron said:**
> You can generally move a Linux install disk from machine to machine without problem, as long as no generic drivers have been installed.

Now that's a thought - do the plain vanilla install in another machine then move the hard drive to the problem machine. The trick would be to find a desktop with at least one IDE/PATA port, the subject machine only has IDE I believe. There are SATA/PATA adapters but I don't know if they would work to install an OS or not.

---

### Post by sudodus on 2016-10-09
I have an ***adapter*** with the name ***USB 2.0 TO IDE & SATA cable***. I have used it to install into an IDE (PATA) drive (and also to boot from it, if the computer can boot from USB).

---

### Post by yokelns on 2016-10-09
Sooo...a weird thing happened when I tried istalling the Hydrogen OS by attaching the IDE drive to my current setup (it has one IDE port:)). 

Apparently it uses debian istaller and it started asking me setup questions ( which keyboard would you like, which language and so on) but then it asked for CD-ROM drivers so it could load up the install files from the CD which is weird since it was booting from USB drive which has all the installation files on it. 

Anyways, I have since learned that Lubuntu is pretty lightwight as well so I will try to istall that instead :)

sudodus, I have one of those as well :) So you just connect the IDE device to it and plug it into USB and it will recognize the device at boot? I was under impression that these adapters will only work in Windows enviroment...

---

### Post by yokelns on 2016-10-09
OK, I stuck an IDE into my new computer, installed the Lubuntu on it and put it back into the old computer. 

I am now sending you this message from the my old computer running Lubuntu 14.04 :)

Thx a lot for the help guys! :) 

The only issue that I have now is that monitor displays a black stripe for a fraction of a second every 8 seconds or so. It's noting serious, it's just a little anoying...But, I'm going to start a new thread for that.

---

