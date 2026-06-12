---
title: "Ubuntu hates audio for me."
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by The Titan on 2008-03-13
When i installed ubuntu i could not get it to recognize the onboard sound card.  I figured it was because it was onboard.  Now i stuck PCI soundcard in there and it dosent recognize that either.... Im really getting frustrated, can someone please help me?

---

### Post by NightwishFan on 2008-03-13
Did you search to see if the card was supported? My onboard stuff works well.

---

### Post by The Titan on 2008-03-13
I dont know what my onboard stuff is, and i dont know how to find out.  I tried alsamixer and got this:
```

titan@dungeon:~$ sudo alsamixer
[sudo] password for titan:

alsamixer: function snd_ctl_open failed for default: No such device
titan@dungeon:~$ 

```

i tried some command someone gave me that was supposed to tell me:
```

titan@dungeon:~$ lspci | grep audio
titan@dungeon:~$ 

```

i dont know what to do next...

---

### Post by The Titan on 2008-03-13
typical,  im getting REALLY PISSED OFF!

---

### Post by BandD on 2008-03-13
Well it's quite obvious that Ubuntu doesn't detect either of your sound cards.  If you could give us some information abot your computer (Make and Model) and some info about the PCI card you bought, it will make us eaiser to help you out.

Can you post the result of: ```
 lspci
```

in a terminal?

---

### Post by The Titan on 2008-03-13
```

titan@dungeon:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
titan@dungeon:~$ 

```

i just figured out that the onboard is a AC 97, i did a search and found some stuff except nothing worked... I have no idea what the other card is, i just took it from an old computer and stuck it in there.

---

### Post by BandD on 2008-03-14
I'm pretty sure your sound card is made by Intel.  I did a little google search with:

Intel ICH4 audio

And found that this Intel chipset ships with the AC97 card.  


I had a look here:  [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel")

And it seems that your sound card is supported in ALSA (The linux audio driver project.)  I'm not an expert in this field, and I too had some issues with my sound card.  But have a look through the ALSA documentation for your sound card and keep pluggin away.  

My guess is that you will need to configure your ALSA driver specifically to your card.  

This is going to be the key for you I think:

```
modprobe snd-card-intel8x0
```

But I'm in slightly over my head here.  I'm not confident enough to give you explicit directions.  So I hope this will at least point you in the right direction.  

If someone else reading this has more experience with ALSA modules, please chip in!

---

