---
title: "Can't boot X in live CD: no screens found"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by limitedmage on 2006-11-04
Hi everyone,

I have been using Ubuntu for a while now, and I've been telling everyone how amazing it is. One of these people want to try it with the live CD, but when I try to boot it, a blue screen with a lot of gibberish says "X Server fatal error: no screens found".

The computer is a Dell Dimension 9150. It has a ATI Radeon X300 SE 128MB Hyper Memory graphics card, 2GB of RAM, 250 GB SATA drive.

I have tried multiple times. With Ubuntu Edgy, Ubuntu Dapper and Edubuntu Dapper, this error appears. With Kubuntu Dapper, the screen freezes after everything apparently loads, with a Kubuntu logo and an empty progress bar.

I have even booted by safe graphics mode and different screen settings via F4 in the boot menu.

Can anyone please help me?

---

### Post by Fittersman on 2006-11-04
i had this same problem and it took me so long before someone would help me out.

so here is what i had to do....

cd /etc/X11/

sudo pico xorg.conf

go down to the part where it says something along these lines
```
Section "Device"
        Identifier      "RADEON 7500 SERIES"
        Driver          "vesa"
        BusID           "PCI:1:9:0"
EndSection

```

change the PCI part to where the video card is located
driver must be set to 'vesa'
and change the identifier to what your video card is called

then scroll down to the part like this
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "RADEON 7500 SERIES"
        Monitor         "Q71B-8"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720$        EndSubSection

```

and change the device to match what you put by the identifier earlier

now type

sudo startx


it should work now hope that helps...

---

### Post by limitedmage on 2006-11-04
mmm okay, so, how do I use the command line throught the live cd in  order to do this? And also, in the Windows device manager, there are 2 video cards: one that's apparently the main, and another one that says "Secondary" after the name. Which should I use? The main one says "PCI Slot 10 (PCI bus 1, device 0, function 0)" and the secondary says "PCI Slot 10 (PCI bus 1, device 0, function 1)". How do I write this in BUSID?

---

### Post by Fittersman on 2006-11-05
when i had this problem there was a blue screen and it said something about diagnosing the problem and you click ok and keep going until it turns to a black screen and then you log in there and it should be the terminal i think then just type in what i said and about the video card just try em both i guess...

---

### Post by taurus on 2006-11-05
> **limitedmage said:**
> mmm okay, so, how do I use the command line throught the live cd in  order to do this? And also, in the Windows device manager, there are 2 video cards: one that's apparently the main, and another one that says "Secondary" after the name. Which should I use? The main one says "PCI Slot 10 (PCI bus 1, device 0, function 0)" and the secondary says "PCI Slot 10 (PCI bus 1, device 0, function 1)". How do I write this in BUSID?
You have two video cards!  Try connecting your monitor to the other one if the first one doesn't work!!!

---

### Post by rccharles on 2006-11-05
> **limitedmage said:**
> mmm okay, so, how do I use the command line throught the live cd in  order to do this? 

Press control+alt+F1

This will get you to a console.  You may have to press the keys more than once.

Robert

---

### Post by limitedmage on 2006-11-05
So, I finally got it working. Just had to change the driver from "ati" to "vesa". But no sound is working. The sound card is a Sound Blaster X-Fi, which apparently will not work on Linux whatsoever. Thanks anyway.

---

### Post by taurus on 2006-11-05
Are you sure the soundcard doesn't work or just that the volume is muted?  See if you can increase the volume of your card with

```
alsmixer
```

---

### Post by limitedmage on 2006-11-07
mmm... isn't it *alsamixer*? I'll try it out, but I doubt it'll work.

---

### Post by Redache on 2006-11-07
If it's registering two video cards then I reckon that some onboard video card might be enabled somewhere. it'd be worth checking out, or it's just a side effect of hyper memory.

---

### Post by dschmitt on 2007-05-03
> change the PCI part to where the video card is located
Sorry, for the ignorant question but where do I find out "where the video card is located"?

---

### Post by oswaldkelso on 2007-09-18
[http://en.wikipedia.org/wiki/Lspci]("http://en.wikipedia.org/wiki/Lspci")

the command is 

lspci

---

