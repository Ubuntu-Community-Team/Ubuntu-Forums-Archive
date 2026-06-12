---
title: "Install Ubuntu from PCMCIA CDROM"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by alart on 2007-07-03
Pls, help

I'm trying to install ubuntu on Compaq Armada M300, ( no CD, no floppy, no network ) 
only external CD-ROM via pcmcia.

I took out the HDD from Compaq and put in to IBM T40 with successful instalation of 7.04 afterwards.
Next step: Take out the HDD from IBM to Compaq.

System start up in safe mode with no errors, but not in graphic mode.

Is it any possibility to do next :

1. Mount PCMCIA CDROM ( as I can see the system found it and recoqnize perfectly )
2. From mount CDROM startup installation process for recoqnize all components of Compaq in right way.


Thank you in advance.

---

### Post by aquavitae on 2007-07-03
The mount part is easy - use the 'mount' command.  Its probably something like:
sudo mount /dev/cdrom /media/cdrom
See 'man mount' for more info on the command.
Once you're there, I'm not sure what you need to do though. 

It might be easier to try to repair the system you've got - it should be mostly working, just needs some kernel modules loaded and a few drivers. Does the system start in normal mode, or only in recovery mode? Try starting in normal mode without the splash screen, I wrote some instructions for that [here]("http://ubuntuforums.org/showthread.php?t=490222").  If it doesn't start properly it will display the error, which you can then post here.  Hopefully we'll get it working wthout a reinstall!

---

### Post by alart on 2007-07-03
Thank you.

Starting from end.

It starts in normal mode, but during the upload graphic environment error appeared. 

I'm not sure that CDROM appeared as /dev/cdrom. How could I check it ? 
When I will mount the CDROM how I could access to information on CD ?

Sorry for "dummy" questions, but I'm absolutely new in Linux

---

### Post by aquavitae on 2007-07-03
> **alart said:**
> It starts in normal mode, but during the upload graphic environment error appeared.

What exactly do you mean by "upload graphics environment"?  Do you mean whex the x server starts (i.e gnome/kde)?  It sounds like you just have the wrong display setup - not surprising as you installed on different hardware.  What did the error message say?  Start in recovery mode and post the last few lines of the file /var/log/Xorg.0.log.  You can do this by using 'tail --lines=20 /var/log/Xorg.0.log > logfile.txt'  Copy logfile.txt to another computer and post the contents of it.  Alternately just type 'tail --lines=20 /var/log/Xorg.0.log' and copy the output.

I'm not sure that reinstalling is the best solution here, and in any case I'm not sure how you would do it from a console off a livecd.  Maybe someone else can advise better on this, but I'd say try to fix the problems with the current install - if nothing else, at least you will learn a lot by it!

---

### Post by alart on 2007-07-03
At first : Thank you for yuo help. I mount the PCMCIA CD and USB. 
As you said I have a problem with display setup

```

        ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) Primary Device is: PCI 00:05:0
(II) ATI:  Candidate "Device" section "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]".
(II) ATI:  Shared PCI/AGP Mach64 in slot 0:5:0 detected.
(EE) No devices detected.

Fatal server error:
no screens found

```
 

Could you help me with solution please

---

### Post by alart on 2007-07-03
YES !!! I start it. no reinstall. I just use the sudo dpkg-reconfigure xserver-xorg and reconfigure X.

Thank you for help !

---

### Post by aquavitae on 2007-07-04
Glad you got it working.  Sorry - I forgot about dpkg-reconfigure xserver.org or I would have suggested it earlier!

---

