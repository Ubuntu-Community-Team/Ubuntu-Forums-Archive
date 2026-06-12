---
title: "hdparm"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-11-30
when ever i try to use hdparm i get this error

```
  HDIO_SET_DMA failed: Inappropriate ioctl for device 
```

what is it? how do i fix it?

---

### Post by skymera on 2007-12-01
bmup

---

### Post by huwnet on 2007-12-01
[http://ubuntuforums.org/showthread.php?t=628009](http://ubuntuforums.org/showthread.php?t=628009)

Please try and keep everything in one thread ;). Hopefully someone will come along soon that knows the answer to your question.

---

### Post by skymera on 2007-12-01
when i do post one i get no replies >_<

---

### Post by PmDematagoda on 2007-12-01
skymera, while I realise that this may not really pacify you, why are you worrying about something that may not even play a role in your HDD's performance when you know that your own HDD works properly?

---

### Post by skymera on 2007-12-01
it hasnt appeared on any of my other hard drives.

and wondering why on this.

---

### Post by PmDematagoda on 2007-12-01
Hmm, could you give any details on this specific hard drive, may be that might give us a clue as to what is happening.

---

### Post by skymera on 2007-12-01
uhhh its a Dell, so im guessing thats the problem.

nothing on my pc can be detected, fan speeds etc.

i was just curious what that error meant and if there was a way around it.

---

### Post by PmDematagoda on 2007-12-01
As I have never used hdparm, I don't know anything about it.

Could you give me the details of what it does? Then I will try it out and if I get the same error we can get together on the streets and start protesting or whatever you do to tell people about our problems:).

---

### Post by skymera on 2007-12-01
enables DMA on my drive, supposedly speeds up, and ive noticed improvements on my laptop.

---

### Post by PmDematagoda on 2007-12-01
Ok, I will give it a try, see if it can turn up anything weird on my WD disk.

---

### Post by Teknyk on 2007-12-01
skymera,
when you do sudo hdparm -v /dev/hda it says DMA is off?

What does it say under "capabilities" when you do sudo hdparm -I /dev/hda

---

### Post by mahiyar on 2007-12-01
Enabling DMA/UDMA on SATA drive was a problem long time back ( a year or so ago) in linux, at that time time even "hdparm" command used to work only for ide drives. I do not know whether that has been changed. try using this command just for info about your drive >>sudo hdparm -i /dev/sda (replace sda appropriately)

---

### Post by skymera on 2007-12-01
thats what i did

and the error i posted, was the answer.

---

### Post by mahiyar on 2007-12-01
You set dma by the -d1 switch, -i is just for getting information. This link talks about setting the parameters during boot in grub [http://lists.linuxcoding.com/rhl/2007q4/msg08959.html](http://lists.linuxcoding.com/rhl/2007q4/msg08959.html) hope it helps.

---

### Post by Teknyk on 2007-12-02
From what I have found you can't use hdparm to set the DMA on a SATA drive as they will already be using the best it can.

That is why I asked him to do sudo hdparm -I /dev/hda and post the results of the capabilities. The asterisk will show what it is set at... as below.

```
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Vendor, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: 254 (0xfe)
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=240ns  IORDY flow control=120ns
```

*edit*
err...if the OP is using a SATA drive they will need to use sda instead of hda

---

