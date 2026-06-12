---
title: "Sound not working!"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by EleFlameMax on 2008-01-05
I was on amaroK and I clicked play, but it started going through all of my music really fast, not playing it. I restored the window and saw an error message say:

```
Audio Output not available, the device is busy

Xine Paramters:
```

I looked at my speakers to see if they were on and they were, and then I tried to test the sound with a flash video. Still no luck. Halp meh!

---

### Post by exneo002 on 2008-01-05
if its ubuntu its probable a gnome problem or somthing try another media player then try linux mint or ubuntu ultimate 

If its a sound card problem just buy a cheap soundcard thats linux friendly like a 5.1 digital channel dolby or somthing If you cant afford it just look for linux drivers for your hardware

---

### Post by EleFlameMax on 2008-01-05
Please help?

---

### Post by SidewinderPro2 on 2008-01-05
This sound thing has been a disaster IMO. My onboard sound didn't work until yesterday when I finally broke through all the crap. The sound quality is still sub par to Vista.


What sort of card are you using? Do you have ALSA all setup?

---

### Post by EleFlameMax on 2008-01-05
I don't know what sound card I have, is there a way to find out?

---

### Post by Don1500 on 2008-01-05
In terminal 

> 
lspci

Should tell you what is installed
here's mine
>  lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:0c.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)


---

### Post by Dave Otter on 2008-01-05
Go to Applications-Accessories-Terminal

            type in asoundconf list  
              this will give a list of your soundcard(s)

---

### Post by EleFlameMax on 2008-01-05
My sound card is SI7012, and I check that ALSA matrix page for it, but no luck. My sound was working yesterday, it just stopped today. What should I do?

---

### Post by agim on 2008-01-05
First of all, try not to Panic :)

My sound card goes sometimes after I install new software. Its given me more trouble than the rest of my hardware combined.

First of all, sudo apt-get update. I'm not an expert by any means, but there have been times when I installed something new off of synaptic, my sound card didn't work, I installed the automatic updates about an hour later, and they worked like a charm.

There are other fixes for it as well, just keep looking on the forums. I will try to find some sites that have helped me and post them here.

Don't think that you immediately have to go out and by a new sound card, there likely is a fix or a workaround.

---

### Post by EleFlameMax on 2008-01-05
> **agim said:**
> First of all, try not to Panic :)

My sound card goes sometimes after I install new software. Its given me more trouble than the rest of my hardware combined.

First of all, sudo apt-get update. I'm not an expert by any means, but there have been times when I installed something new off of synaptic, my sound card didn't work, I installed the automatic updates about an hour later, and they worked like a charm.

There are other fixes for it as well, just keep looking on the forums. I will try to find some sites that have helped me and post them here.

Don't think that you immediately have to go out and by a new sound card, there likely is a fix or a workaround.

...I love you. :guitar:

Update worked, thanks man.

---

### Post by agim on 2008-01-05
Haha! Awesome. That the first time I have helped someone on this forum. Linux is spectacular. Hope you stick with it.
Always try the simple things first. As the other poster said, even if you can't get some hardware to work, there is probably a driver somewhere.

---

