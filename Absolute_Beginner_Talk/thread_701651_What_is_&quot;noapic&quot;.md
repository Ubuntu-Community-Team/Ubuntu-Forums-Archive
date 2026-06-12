---
title: "What is &quot;noapic&quot;?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Morthian on 2008-02-19
I just tried making the switch to Linux from WinXP, but I am having some issues. When Ubuntu tries loading it always just stops and hangs when it says "Kernal alive" followed by some other line regarding tables and a bunch of numbers. Anyway, I found something on the web about replacing "splash" in the command line with "noapic". So I tried that, and Ubuntu loads.

So what the hell is "noapic"? Why do I need to put it in the command line every time I want to boot up Ubuntu?

Also, my sound is not working... but that is besides the issue. I just thought the two problems might be related. Maybe.

Any help here would be much appreciated. Thanks.

---

### Post by neurostu on 2008-02-19
For "noapic" look at this:
[http://ubuntuforums.org/showthread.php?t=334083](http://ubuntuforums.org/showthread.php?t=334083)

Your sound hardware not working is a different issue, what hardware are you using?

---

### Post by Morthian on 2008-02-19
I have a Creative Audigy 4 sound card.

Also, I was going to update my BIOS to see if that helps with the other problem, but I don't remember exactly what kind of motherboard I have. Could you recommend a way to figure that out? I have Phoenix Award Workstation BIOS 6.00 on an nVidia nForce motherboard. That's pretty much all I know about that.

And is there a program that I can download that would let me know what hardware in my computer has available updates?

---

### Post by neurostu on 2008-02-19
The easies way to figure out what Mobo you have is to open your case and to look for a serial number or a Model Number (probably better and easier to use). Then goto the manufacturer's website and search for BIOS updates on that Model or Serial number.  Then use whatever utility they provide to update your bios.

I'm pretty sure that Ubuntu ships the latests drivers as soon as they are ready.  So apt is what you can use to see if there are any updates waiting, but as far as looking on all the manufacturer's website and looking for bios and flash updates i am not aware of any programs that do this.

----Edit------

Again I stress get your EXACT model number. I recently updated the BIOS on 6 identical (so I thought) machines (2 of which had a different model number then the others). I didn't notice this slight discrepancy and spent the next 3 weeks trying to figure out why the network cards on those 2 machines just "stopped" working, when I had broken them with the BIOS update.

---

### Post by Morthian on 2008-02-19
I still can't figure out where to get an update for my BIOS. I figured out I have an nVidia nForce 590 SLI AMD 64. I went to nVidia's site and they don't have any drivers for Linux. As for Windows, the latest driver is from June 2006. I'm pretty sure I already got that one.

I went to Phoenix Award's site and they just tell me to go to my motherboard manufacturer's site for updates.

I am so frustrated...


Edit: When I search on Google, a lot of sites point to this:
[http://scan.esupport.com/?CFID=1825749&CFTOKEN=64113719](http://scan.esupport.com/?CFID=1825749&CFTOKEN=64113719)

Do you know if this is legit?

---

### Post by neurostu on 2008-02-19
nVidia nForce 590 SLI is probably the chipset of your MOBO. Is there a model number listed on your MOBO?

---

### Post by neurostu on 2008-02-19
> . I went to nVidia's site and they don't have any drivers for Linux. As for Windows...

The bios is platform independent. Meaning that it doesn't matter if you are running windows or linux, etc... a BIOS is a "Basic Input Output System". Your mobo uses the BIOS to turn itself on, configure the hardware, and start up the OS on the Hard drive (among other things).

---

### Post by neurostu on 2008-02-19
Doing some google searches for "nVidia nForce 590 SLI AMD 64" it is turning up mostly ASUS mother boards, but before you download a BIOS from the ASUS site you need to confirm that the mobo is made by asus. 

WARNING: Installing the incorrect BIOS on your MOBO will brick it. I personally don't know how to recover a system that has had the incorrect bios installed, I've heard that it is possible but it can't be easy.

---

### Post by neurostu on 2008-02-19
It might not be the BIOS that is causing the sound card not to work. I would recommend looking at this page before you try to upgrade your bios:

[https://help.ubuntu.com/community/HowToConfigureSoundBlasterAudigySEinBreezy](https://help.ubuntu.com/community/HowToConfigureSoundBlasterAudigySEinBreezy)

---

### Post by Morthian on 2008-02-19
I was going to upgrade BIOS to fix the other problem (the one where I have to add "noapic" to the command line every time I boot Ubuntu). Maybe I'll try out that esupport site before attempting to upgrade the BIOS myself. I just don't think I'm in the mood to brick my motherboard.

And I actually found that I get sound by setting playback to Multichannel in the sound options. But I want access to audio effects and equalizers. =/

---

### Post by neurostu on 2008-02-19
Before you pay some website to "Scan" your computer to tell you what hardware you have you should seriously just open your case and find the model number, post that here and i'll help you upgrade your bios. I've done it dozens of time and it isn't that hard.

---

