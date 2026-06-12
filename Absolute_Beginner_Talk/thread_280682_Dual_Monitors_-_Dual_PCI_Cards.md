---
title: "Dual Monitors - Dual PCI Cards"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by nickburns on 2006-10-19
Having trouble getting dual monitors with two identical PCI cards, both monitors are identical as well.  I only get one monitor to work, please help!
I have tried several posts/threads and can't seem to get it to work.  I think I have the right driver for the card, as I can get the cards to work indiviually if I only have one installed at a time.  

- I have one in PCI #1 (0:8:0) and one in PCI #2 (0:9:0) 

thanks in advance...

---

### Post by CatKiller on 2006-10-19
I don't think that you need the Screen 0 and Screen 1 parts in the Device sections - I'm pretty sure that that's only used for when you've got a single card with two outputs. X possibly can't find the second output on your 0:9:0 card.

I also don't think you need the MonitorLayout options in the Monitor sections.

Otherwise, I think it looks OK from the little that I know. Let us know how you get on.

---

### Post by nickburns on 2006-10-19
Commented out both the suggestions with no difference, my guess is that the second pci is not firing up.  The monitor does not even try to come out of power save.  Is there a way to force the PCI to fire up perhaps?

Any other suggestions?

---

### Post by CatKiller on 2006-10-19
> **nickburns said:**
> The monitor does not even try to come out of power save.  Is there a way to force the PCI to fire up perhaps?

I was wondering that myself. I've only tried this with one PCI and one AGP, and I need to start the PCI card first. Sometimes the AGP card doesn't start, and I need to restart X. I believe that it is INT10 that is used in some way to turn the second card on, but I really don't know that much about it.

---

### Post by nickburns on 2006-10-20
Tried to make my xorg.config from scratch again last night. No luck, so I have reverted back to the attached configuration.  Any other ideas to  help me figure out how to light up the other PCI card  and monitor?

---

### Post by CatKiller on 2006-10-20
> **nickburns said:**
> Any other ideas to  help me figure out how to light up the other PCI card  and monitor?

The [nVidia documentation]("http://download.nvidia.com/XFree86/Linux-x86/1.0-9625/README/appendix-d.html") mentioned this:

> Option "UseInt10Module" "boolean"

    Enable use of the X Int10 module to soft-boot all secondary cards, rather than POSTing the cards through the NVIDIA kernel module. Default: off (POSTing is done through the NVIDIA kernel module).


---

### Post by nickburns on 2006-10-22
Alright, have read up on tons of dual monitor threads, tried nearly everything in the book.  I am getting both cards to fire up, both monitors are coming out of power down and then I get my default monitor to display part of a correct desktop, the system freezes, and the other monitor has blue and gray lines all over.  I have looked through the log file and have found that it freezes up in all different places. (does not give me the same last line in the log file).  I have attached one of my latest xorg.conf files.  

I am having a hard time finding similar problems on the web, I am using dual cards that use the vesa driver, not an ati or / nvida cards.  I am using two Dell M991 monitors.

Is this even possible?

Please help...

---

### Post by CatKiller on 2006-10-23
Good that you've managed to get them both firing up. You don't appear to have **any** resolutions listed for your Screen Modes.

---

### Post by nickburns on 2006-10-23
I have tried all different types of resolutions, even change the default to 600x800 and i get the same result.

---

### Post by CatKiller on 2006-10-23
> **nickburns said:**
> I have tried all different types of resolutions, even change the default to 600x800 and i get the same result.

It's just that you don't have any. If you had one, even, it wouldn't look so mad to my eyes. One of my Screen sections looks like this: ```
Section "Screen"
        Identifier      "LeftScreen"
        Device          "NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
        Monitor         "Hansol 730E"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

``` I'm not saying that you **should** have resolutions in here, just that every working xorg.conf I've seen so far does. I still wish you luck with it, even though I can only really offer moral support, and thank you for letting us know how you're getting on.

---

### Post by nickburns on 2006-10-23
Thanks for the advise, I tried this (attached) xorg.conf file with still no luck.

---

