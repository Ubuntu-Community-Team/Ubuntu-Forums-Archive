---
title: "[SOLVED] TV Tuner woes..."
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by blurryone on 2007-12-10
Hi All,

I have pretty much got my ubuntu box smoking away nicely, the final piece of the puzzle is my removable HP DVB-T Tv Tuner card...

I plugged her in and tried to run TVTime and well not alot happened... is this because i didn't have it plugged in at installation (so it could detect and install drivers for it)..
Is there a way that i can setup the card without having to re-installl ubuntu? more specifically does ubuntu support the plugging in of devices like this and will it install drivers on the fly?

lspci does not show me that the device is there....

Any info would be much appreciated!!!!

Peace
Blurry

---

### Post by nikoPSK on 2007-12-10
you need to remove the "wrong" drivers:

```
 sudo rmmod bt878
sudo rmmod tuner
sudo rmmod bttv
```

then add the right ones. [http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV](http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV) for the complete list of card numbers.  Go to [http://www.linuxtv.org/v4lwiki/index.php/Tuners](http://www.linuxtv.org/v4lwiki/index.php/Tuners) for the list of tuners.

then you would do this:
```
 sudo modprobe bttv card=?? tuner=??
```

replacing ?? with your card and tuner numbers.

---

### Post by blurryone on 2007-12-10
Ok, thanks, however none of those drivers where installed anyways and i cannot find my card in that list (did a search)

card is a...

HP ExpressCard
EC300 DVB-T TV Tune

---

### Post by nikoPSK on 2007-12-10
sorry, I cannot help with the number. I found mine manually with a quick Google :D.

---

### Post by blurryone on 2007-12-10
thanks for the help though.

It looks to me like when i plug it in nothing happens. is there a way to force ubuntu to check for new hardware?

---

### Post by nikoPSK on 2007-12-10
it's most likely a pci card, do this:

```
lspci
```

I'd like the output to see is ubuntu is actually recognizing it.

---

### Post by blurryone on 2007-12-10
ok here it is... i can't see it here...

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by nikoPSK on 2007-12-10
I do not see it either. Possibly your pc isn't recognizing it. Unfortunately I can be of no further assistance.

---

### Post by blurryone on 2007-12-10
Hey no worries niko. i really appreciate the help. i am going to reinstall now :S will let you know how i get on.

---

### Post by nikoPSK on 2007-12-10
sounds funn. (I've had to reinstall like 15 times...) but I have a tvcard fine so I can be of great assistance here.

---

### Post by blurryone on 2007-12-11
WOOP WOOOOOOP

got it going... had to reinstall with it plugged in.. it then install the drivers

the dmesg command confirmed in was being plugged in

using it with kaffeine.. fantastic.

will offer help to anybody with the same problem. let me know.

Search criteria...
DVT-t DVT

Sweet all peace out.

Blurry

---

### Post by nikoPSK on 2007-12-11
good for you. I underwent the same experience. After about six times of fiddling about I got it. Best to you and merry christmas.

---

### Post by sagui on 2008-02-15
What numbers did you end up using?

---

### Post by nikoPSK on 2008-02-15
> **sagui said:**
> What numbers did you end up using? I beleive card 34 and tuner 43. :)

---

### Post by sagui on 2008-02-15
Thanks for the #s.  Still no worky though.

Hey did you have to jump through any kind of hoops to get the expresscard slot to work?  I saw some dmsg listing before and nobody could see the inserted card.  Did you have to get that working first, or did it work and the card doesn't show up until the module is loaded with the proper numbers?

Also does the LED on the Card light up for you guys when you plug it in?

Also it seems that the solution is to reinstall the system with the card plugged in, is there a way around that?  'Cause I really don't want to.

---

### Post by mjwchapman on 2008-05-01
```
sudo modprobe pciehp pciehp_force=1
```
was the missing piece for me
i was up and running in kaffeine five minutes later

---

