---
title: "USB version"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by nicdal on 2007-07-20
How can I find out if I've got USB 2.0 (or not) on my Fujitsu/Siemens C Series Lifebook ?

---

### Post by Rocket2DMn on 2007-07-20
Try this in terminal:
```
lspci
```

---

### Post by nicdal on 2007-07-20
> **Rocket2DMn said:**
> Try this in terminal:
```
lspci
```

so an entry like:
0000:00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
tells me I've got 1.1 ?

---

### Post by Rocket2DMn on 2007-07-20
So it would seem.  How old is your laptop?  USB 2 has been around since 2000, how old is your laptop?

---

### Post by nicdal on 2007-07-20
> **Rocket2DMn said:**
> So it would seem.  How old is your laptop?  USB 2 has been around since 2000, how old is your laptop?
Not quite sure, found it in a skip 4 years ago.

---

### Post by Rocket2DMn on 2007-07-20
Hrmm, it could very well just be usb 1.1 since usb 2 should be detected automatically.  You can also run the command
```
sudo lshw
``` to show detailed computer specs.
Even further, I just found you can save the output as an html file :)
```
sudo lshw -html > lshw_output.html
```
Bam!

---

### Post by nicdal on 2007-07-20
Actually, I used sudo lshw -html > lshw_output.html some time ago and used the html output (after adding some colour and bits and bobs) as my homepage. I wasn't exactly sure what I was looking for regarding USB 2.0 (or not) in all that output; but all USB references include "1.1" , so it would seem that's what I've got - USB 1.1.

My reason for asking the question in the first place was because this machine only has a CD ROM drive, I'd quite like to burn CD ROMs on it and view DVDs but I've no interest in burning DVDs or using rewritable stuff. I looked around for an external USB DVD rewriter drive and found that most were USB 2.0 , so my first move was to ascertain whether I could use the things.

---

### Post by Rocket2DMn on 2007-07-20
You COULD run a USB 2 drive on a USB 1.1 port, it would just be slow as hell.
If you think your computer can handle playing DVDs, or at least writing CDs and/or DVDs, you can purchase an external USB or firewire drive and get a USB 2 or firewire PCMCIA or CardBus (if supported) adapter to plug into the expansion slot of the laptop.  
If that sounds confusing - there is a slot on the side of your laptop that is made for an expansion card, called a PCMCIA slot.  CardBus is just the newer version of PCMCIA.  You can buy cards that you plug in there that have USB 2 or firewire ports on them.
Post the whole output of "lspci" and we will see what you  have.

---

### Post by nicdal on 2007-07-20
> **Rocket2DMn said:**
> You COULD run a USB 2 drive on a USB 1.1 port, it would just be slow as hell.
If you think your computer can handle playing DVDs, or at least writing CDs and/or DVDs, you can purchase an external USB or firewire drive and get a USB 2 or firewire PCMCIA or CardBus (if supported) adapter to plug into the expansion slot of the laptop.  
If that sounds confusing - there is a slot on the side of your laptop that is made for an expansion card, called a PCMCIA slot.  CardBus is just the newer version of PCMCIA.  You can buy cards that you plug in there that have USB 2 or firewire ports on them.
Post the whole output of "lspci" and we will see what you  have.

Am confused, but here is output of "lspci" :

0000:00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Co ntroller (rev 01)
0000:00:0a.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Co ntroller (rev 01)
0000:00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 C ontroller (PHY/Link)
0000:00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 23)
0000:00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 23)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 30)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Contro ller (rev 70)
0000:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

---

### Post by Rocket2DMn on 2007-07-20
Ahhhah!
> 0000:00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Co ntroller (rev 01)
0000:00:0a.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Co ntroller (rev 01)
You have CardBus, this is good, however...
> 0000:00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 C ontroller (PHY/Link)
You also have a firewire port on your computer!  You can buy an external cd-rw or dvd/cd-rw or dvd-rw drive as long as it has a firefire attachment, and you won't need to purchase other hardware (except a firewire cable if you don't have one).  This is probably the best option since firewire has more consistent high speed transfer than USB 2.

However, if you still want USB 2 capabilities, you can buy a USB 2.0 CardBus adapter from pretty much anywhere.
I suggest using the firewire, but USB 2 is more universal.

---

### Post by nicdal on 2007-07-20
> **Rocket2DMn said:**
> Ahhhah!

You have CardBus, this is good, however...

You also have a firewire port on your computer!  You can buy an external cd-rw or dvd/cd-rw or dvd-rw drive as long as it has a firefire attachment, and you won't need to purchase other hardware (except a firewire cable if you don't have one).  This is probably the best option since firewire has more consistent high speed transfer than USB 2.

However, if you still want USB 2 capabilities, you can buy a USB 2.0 CardBus adapter from pretty much anywhere.
I suggest using the firewire, but USB 2 is more universal.

Last stupid question for today: what does this firewire's socket/connection look like and where does it live and what does the cable look like ?

---

### Post by Rocket2DMn on 2007-07-20
There are two types of firewire connection tips - a 4 pin and a 6 pin.  Check out [Wikipedia ]("http://en.wikipedia.org/wiki/FireWire")for some good examples for images.  Your firewire port is probably small little square though, like [this]("http://www.pana3ccduser.com/images/upload/Firewire_labeled_laptop_connectors.JPG") (found on google image search).  It is probably on the side of your laptop, but it could be on the back side.

---

