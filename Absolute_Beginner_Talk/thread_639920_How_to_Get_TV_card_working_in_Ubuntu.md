---
title: "How to Get TV card working in Ubuntu"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by hockeyfighter09 on 2007-12-13
I downloaded the TVTime television viewer from synaptic, but now I cant figure out how to configure it to watch tv on Ubuntu.  I dont know what tv tuner card I have is there anyway to find out?  I dont know if graphics card play a factor in this but just in case I have a nvidia Geforce 7800 gtx card.  Anyone have suggestions?:confused:

---

### Post by hockeyfighter09 on 2007-12-13
Nobody?

---

### Post by rsambuca on 2007-12-13
To see your hardware, post the output of 

lspci

Also, in the future, please wait a day or two before bumping your threads.

---

### Post by hockeyfighter09 on 2007-12-13
00:00.0 Host bridge: nVidia Corporation Unknown device 0071 (rev a3)
00:00.1 RAM memory: nVidia Corporation Unknown device 007f (rev a1)
00:00.2 RAM memory: nVidia Corporation Unknown device 0075 (rev a1)
00:00.3 RAM memory: nVidia Corporation Unknown device 006f (rev a1)
00:00.4 RAM memory: nVidia Corporation Unknown device 00b4 (rev a1)
00:01.0 RAM memory: nVidia Corporation Unknown device 0076 (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 0078 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0079 (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 007a (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 007b (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 007c (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 007d (rev a1)
00:02.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:04.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:10.0 RAID bus controller: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:11.0 RAID bus controller: nVidia Corporation CK804 Serial ATA Controller (rev f4)
00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1)
03:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
03:04.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
03:04.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
03:05.0 Multimedia video controller: NEC Corporation Dual Tuner/MPEG Encoder (rev 0b)
03:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1)



There is my output,  sorry about bumping the thread so soon.

---

### Post by rsambuca on 2007-12-13
It says:  NEC Corporation Dual Tuner/MPEG Encoder (rev 0b)

Sorry, I am afraid I know nothing of this card offhand.  If no one else can help out, I will see what I can dig up, but I don't have time right now.

---

### Post by markharding557 on 2007-12-13
do a google to see if any driver is available

---

### Post by hockeyfighter09 on 2007-12-13
I am not finding any drivers on google. Does this mean that I cant watch TV on Ubuntu?

---

### Post by nikoPSK on 2007-12-13
you can absolutely watch tv on ubuntu :p! I do not know your crad numbers but you can try this. I have a winfast TV2000 XP series card. The only thing I can't seem to use is the infared remote... here:

you need to remove the "wrong" drivers:

```
 sudo rmmod bt878
sudo rmmod tuner
sudo rmmod bttv
```then add the right ones. [http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV](http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV) for the complete list of card numbers.  Go to [http://www.linuxtv.org/v4lwiki/index.php/Tuners](http://www.linuxtv.org/v4lwiki/index.php/Tuners) for the list of tuners.

then you would do this:
```
 sudo modprobe bttv card=?? tuner=??
```replacing ?? with your card and tuner numbers.

---

