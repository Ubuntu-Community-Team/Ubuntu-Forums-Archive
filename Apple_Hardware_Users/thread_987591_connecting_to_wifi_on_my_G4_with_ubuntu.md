---
title: "connecting to wifi on my G4 with ubuntu"
date: 2008-11-19
forum: Apple Hardware Users
---

### Post by Linden84 on 2008-11-19
I just got Ubuntu loaded onto  my Macbook G4 and now I am having problems connecting to my WIFI network. I know the wifi card works because it did previous to installing Ubuntu (8.04). It is not picking up my network, nor any other networks in the neighborhood (and I know there are loads around here). 
Any Help would be WONDERFUL! 
Thank you free software enthusiasts. 
----------------
Now playing: [Cat Power - Good Woman](http://www.foxytunes.com/artist/cat+power/track/good+woman)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by drascus on 2008-11-19
hey linds glad you found the forums. step one in solving this problem would be to find out what type of wireless card you have. go to Applications -> Accessories -> Terminal
 when it opens type ```
lspci
``` hit enter. you will then get a bunch of information displayed. cut and paste that information into the forum and we can begin looking for a solution.

---

### Post by Linden84 on 2008-11-19
lindsey@ubuntu:~$ lspci

0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP

0000:00:10.0 VGA compatible controller: ATI Technologies Inc M11 NV [FireGL Mobility T2e] (rev 80)

0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI

0001:10:12.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O

0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB

0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB

0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB

0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)

0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)

0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI

0002:20:0d.0 Class ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100

0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)

0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)

lindsey@ubuntu:~$

---

### Post by drascus on 2008-11-19
ah so you have the Broadcom wireless card in your computer. if you can get your computer online somehow (hint: plug directly in) there is something that you need to install called the B43 driver for broadcom chipsets. if you open up your System -> Administration -> Hardware Drivers after connecting there should be b43 driver available for install. if not go to system->administration->synaptic packaging manager go for search and in the search type b43 you should see a package called b43-fwcutter click the check box on the left hand side of the package name and click apply. it will ask you if you want to download and install the driver that is the option you should choose. when it is finished configuring and installing you should restart your computer. Your wireless card should now work. if not I have some more tricks up my sleve.

---

### Post by tygoerlitz on 2008-11-20
Hey I did that on my Ibook G4 and when I go into hardware and drivers, I try to activate the driver, the progress bar comes up at 0% and doesnt move from there, if I leave it on for long enought the progress bar will just disapear. Can you please help me out?!

---

### Post by drascus on 2008-11-20
I would say try it from synaptic packaging manager and see if that helps. Just search for it like I said in my previous post and see if that makes any difference.

---

### Post by tygoerlitz on 2008-11-20
Hey, I have also tried that and had no luck when it downloads it tell me that I need to insert the cd, when I do that it still tells me I need to insert the cd. No luck, help it appreciated
Thanks

---

