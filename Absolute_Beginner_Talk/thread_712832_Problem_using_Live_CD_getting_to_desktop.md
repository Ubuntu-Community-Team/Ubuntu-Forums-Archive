---
title: "Problem using Live CD getting to desktop"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by licenced on 2008-03-02
Hi there,

I downloaded and burned ubuntu-7.10-desktop-i386.iso

This works fine in my laptop, booting up into the OS fine. However I am building a new PC and am trying it in there with issues.

The PC has all the necessary components plugged in:
ASUS P5E motherboard
Intel E8400 CPU
Nvidia 8800GTS 512MB GPU
Samsung SATA DVD-ROM
1GB PC-6400 RAM
Creative Audigy 2 Soundcard

The system turns on OK and I can get into the BIOS. Memtest86+ runs fine so I know there is no problem with the memory. When booting with the CD I get to the Ubuntu menu OK. It goes through the whole boot up process, getting to the end of the progress bar. 

If I booted up using the first menu option I get a dialog telling me that Ubuntu is running in Low Graphics mode - I can get to the next diaglog to select a resolution, but the only ones on offer are 800x600 and 640x480. When I continue from this the screen may flicker a few times, but I just end up with a screen with a flashing cursor and nothing else can be done except shut down using the power button. Same happens if I selected to start in Safe Graphics mode from the boot menu - except I don't get the dialog and once I got a message telling me that the graphics driver had been restarted 6 times in 90 seconds and this was probably bad.

Any suggestions? I don't think the graphics card is broken because I used it in my old PC OK a while ago. Could this card just be too new and Ubuntu not able to detect/use it properly? I don't think it can be a problem with not having any HDDs installed as this process shouldn't use them right?

Thanks,
Dave

---

### Post by jan quark on 2008-03-02
if you encounter graphic issues during the installation process the first method you should try is to install via the alternate CD

it is a text based installation ( but very easy) and it is more stable than the live cd

download the alternate CD from here:

[http://releases.ubuntu.com/gutsy/](http://releases.ubuntu.com/gutsy/)

and here is an excellent guide by herman:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by brendan.lefoll on 2008-03-02
Your issue is simple as the person above said, try the alternate cd and install in text mode.

Once you have installed it to your harddrive install the proprietary 3D nvidia drivers and you should be completely fine.

---

### Post by licenced on 2008-03-02
Thanks for the answers. 

Is this very common? 

It's a shame as I wanted to just use the Live CD for a while to get used to the OS, before installing it on top of Windows once I get my PC finished off with the HDDs and Windows installation later in the month. I'm reasonably technically-minded so can probably get through this, but I can imagine this type of issue putting someone else off and convincing them to stick with MS :-(

Cheers,
Dave

EDIT: Just found this  - [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia) - it shows the 8800GT card as not being detected, and not supporting 2D or 3D. Is that my issue? It doesn't list the 8800GTS512MB, but the 8800GT would be the same series/generation. Does this mean my graphics card is not currently supported at all?

---

### Post by PlagueHO on 2008-03-05
Hi Licensed,

I have very similar hardware to you:

Intel E8400
Asus P5E
NVidia GeForce 8800 GTS 512
2GB PC-6400

I get the exact same problem when running the Ubuntu 7.10 i386 Live CD. I haven't been able to resolve the issue yet, however I was able to get the Ubuntu 7.04 i386 Live CD to boot my system without a problem (but it couldn't see my 3rd SATA drive - the one I wanted to install on to). I was hoping 7.10 would fix my HD problem. I can confirm that I have been running Windows XP on this system for a couple of weeks and haven't had any problems. So I believe your hardware is probably fine as well.

I may have to give the Alternate install CD a try tonight and see what happens. I am also fairly inexperienced on Linux as well so I may just be doing something wrong. I have also been unsuccessful in booting PCLinux 2007 Live CD and Mandriva 2006.1 Live CD (all fail to boot with various strange errors that I didn't understand).

---

