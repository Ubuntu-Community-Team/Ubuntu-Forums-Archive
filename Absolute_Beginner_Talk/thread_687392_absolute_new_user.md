---
title: "absolute new user"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by silend on 2008-02-04
hi everybody!
I would like to run ubuntu on my laptop which is a "easy note MX67-t-048".
I would like to know, if somebody can tell me if it would run onto it.
I try to run the live cd yesterday but it didn't seems to work. Maybe is just that I do not know how to use it.
It was running with the presentation and after open me a black screen with some writting that I did not understand.
That is, for the moment, the only informations that I can give to you because I am at school. I will retry this night and repost on this topic with more informations.
I thanks you for the time wasted/spend to answer me.

---

### Post by papuccino1 on 2008-02-04
If it has little RAM, the installation will glitch during the LiveCD instalation. 

I'd suggest using the Alternate ISO instead as it's purely text based. :)

---

### Post by Benbow on 2008-02-04
Could you post the specification of your laptop, processor, memory etc. please

---

### Post by jan quark on 2008-02-04
run in terminal and post here the results
```

lspci
```

```
lshw
```

and I also recommend the alternate CD if the Live CD makes trouble

here an installation guide

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by silend on 2008-02-04
so my laptop's configuration:


Processor
Modèle 	Processeur Intel® Core™2 Duo T5300 (1,73 Ghz)

Mémoire cache 	2 Mo
busdriver 	533 Mhz

Memory
Type mémoire 	DDR2
Taille mémoire vive 	2 Go

hard disk
Taille disque dur 	160 Go SATA
Vitesse 	5400 tours/minute

Vidéo
videocard 	ATI Radeon™ Xpress 1100 896Mo HyperMemory™
Technology 	PCI Express

Monitor 
1280 x 800 Diamond View
Technology 	Ecran large TFT WXGA 15/10

Sound
Chipset sound 	Realtek ALC660 HD Audio

Communication
Carte réseau/ethernet 	Oui - Port LAN
Carte réseau sans fil 	802.11 b/g

Connecteurs
Port USB 	4 USB 2.0
Sortie moniteur 	VGA

hoping it will help you

---

### Post by Kingsley on 2008-02-04
You know I don't speak Spanish! (kidding)
Your specs look fairly new, so I'm very sure Ubuntu will run on the laptop.

---

### Post by silend on 2008-02-05
ok!
so! It's not spanish it's french :p
I have took my laptop configuration that will follows at the end of the post, my apologize, I was wrong about some information
I try the command <lspci> and <lshw> but I do not understand the meaning of those...
I retry to run my live Cd and it does not work. It delivers me this message
"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server outuput to diagnose the problem?"
and when I click YES it tells me that windows system version is 7.2.0 and the ubuntu one is 2.6.20. In the end, "Fatal server error: no screens found"

my laptotp:
-----------------
Dir
------------------
System Information
------------------
Time of this report: 2/4/2008, 22:26:23
       Machine name: PC-DE-SÉB
   Operating System: Windows Vista™ Édition Familiale Premium (6.0, Build 6000) (6000.vista_gdr.071009-1548)
           Language: French (Regional Setting: French)
System Manufacturer: Packard Bell BV
       System Model: EasyNote_MX61
               BIOS: Default System BIOS
          Processor: AMD Turion(tm) 64 X2 Mobile Technology TL-58 (2 CPUs), ~1.9GHz
             Memory: 2046MB RAM
          Page File: 1035MB used, 3274MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 10
DX Setup Parameters: Not found
     DxDiag Version: 6.00.6000.16386 32bit Unicode

---

### Post by hyper_ch on 2008-02-05
Hmmm, if the DesktopCD doesn't always run... if you want to test ubuntu, use it in a virtual machine... if you want to install & test it, repartition your harddisk and install it from the Alternate CD.

---

### Post by silend on 2008-02-05
ok!
so! It's not spanish it's french :p
I have took my laptop configuration that will follows at the end of the post, my apologize, I was wrong about some information
I try the command <lspci> and <lshw> but I do not understand the meaning of those...
I retry to run my live Cd and it does not work. It delivers me this message
"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server outuput to diagnose the problem?"
and when I click YES it tells me that windows system version is 7.2.0 and the ubuntu one is 2.6.20. In the end, "Fatal server error: no screens found"

my laptotp:
-----------------
Dir
------------------
System Information
------------------
Time of this report: 2/4/2008, 22:26:23
       Machine name: PC-DE-SÉB
   Operating System: Windows Vista™ Édition Familiale Premium (6.0, Build 6000) (6000.vista_gdr.071009-1548)
           Language: French (Regional Setting: French)
System Manufacturer: Packard Bell BV
       System Model: EasyNote_MX61
               BIOS: Default System BIOS
          Processor: AMD Turion(tm) 64 X2 Mobile Technology TL-58 (2 CPUs), ~1.9GHz
             Memory: 2046MB RAM
          Page File: 1035MB used, 3274MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 10
DX Setup Parameters: Not found
     DxDiag Version: 6.00.6000.16386 32bit Unicode

---

### Post by jan quark on 2008-02-05
it is not bad to have a dual-boot system at the beginning

check out this site, choose your variant, read through the installation guide, and ask if you have doubts

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

sorry for the terminal commands
it is just a habit of linux

---

### Post by silend on 2008-02-05
ok!
so! It's not spanish it's french :p
I have took my laptop configuration that will follows at the end of the post, my apologize, I was wrong about some information
I try the command <lspci> and <lshw> but I do not understand the meaning of those...
I retry to run my live Cd and it does not work. It delivers me this message
"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server outuput to diagnose the problem?"
and when I click YES it tells me that windows system version is 7.2.0 and the ubuntu one is 2.6.20. In the end, "Fatal server error: no screens found"

my laptotp:
-----------------
Dir
------------------
System Information
------------------
Time of this report: 2/4/2008, 22:26:23
       Machine name: PC-DE-SÉB
   Operating System: Windows Vista&#8482; Édition Familiale Premium (6.0, Build 6000) (6000.vista_gdr.071009-1548)
           Language: French (Regional Setting: French)
System Manufacturer: Packard Bell BV
       System Model: EasyNote_MX61
               BIOS: Default System BIOS
          Processor: AMD Turion(tm) 64 X2 Mobile Technology TL-58 (2 CPUs), ~1.9GHz
             Memory: 2046MB RAM
          Page File: 1035MB used, 3274MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 10
DX Setup Parameters: Not found
     DxDiag Version: 6.00.6000.16386 32bit Unicode




ooops sorry for the multi post, I was just trying to refresh the page...

---

### Post by clovis_ll on 2008-02-05
i'm going to install mine in a few hours. i am currnetly at work but i'm so excited.

i have a sony cr320 laptop. im scared but i'll go for it! (fingers crossed) 

:grin:

---

### Post by silend on 2008-02-05
I hope it would work better than mine. :)
As I hope I will be able to try it one day (fingers crossed too)

---

### Post by Joeb454 on 2008-02-05
**silend** I've seen your laptop specs in 3 different posts :lolflag: just so you're aware :)

Also I'm seeing you can boot from the LiveCD...did you try the 2nd option - Run in Safe Graphics mode

I hade to do this to install it on my desktop :)

---

### Post by silend on 2008-02-05
Hum... yeah  I know that I am aware and as it is say 4 posts earlier, I'm sorry, I just try to refresh my page, the post was written 3 time, that wasn't my intention, I'm sorry.
As you said, I have already try the second option, to run it in safe graphics mode's... But it didn't work.
:(

---

### Post by Joeb454 on 2008-02-05
Oh ok sorry...must've misread it :) My mistake :)

Is using the entire drive to install Ubuntu an issue (i.e. do you still want Windows on the system?)

---

### Post by silend on 2008-02-05
yeah, I think I prefer to keep windows on my laptop, at first.
I really do not know ubuntu, maybe I won't like it.

---

