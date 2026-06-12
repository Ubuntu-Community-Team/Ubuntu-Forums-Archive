---
title: "Live CD won't boot"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by phoenix23 on 2007-10-03
I burned the Gutsy beta to a blank CDR using the right click > "Write to disc" option. When I reboot from the disc, I'm able to to get past the orange loading bar, but then I get a blanks screen.

I presume this has something to do with my graphics configuration... I'm using a Nvidia Geforce FX 5200 at 1280x1024 resolution.

Any idea what's going on? I'd really like to try out gutsy before it's released and all...

BTW: I checked the CD for defects, and there aren't any.

---

### Post by Pumalite on 2007-10-03
Try Alternate CD . Use this guide:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by phoenix23 on 2007-10-03
Thanks

I used this method (as described in that wiki) and got the aforementioned results:> 

Find the downloaded ISO image in the file browser (available at Places &#8594; Home menu on top of the screen.) Right click on the ISO image file and choose Write to Disc and wait for burning to complete.

---

### Post by Pumalite on 2007-10-03
Are you in Linux or windows?. In Ubuntu (or other distro) try k3b and in Tools>Burn CD Image. In Windows:

#

Download and install [WWW] Infra Recorder, a free and open source image burning program.
#

Insert a blank CD in the drive and select Do nothing or Cancel if an autorun dialog pops up.
#

Open Infra Recorder, and select the 'Actions' menu, then 'Burn image'.

    *

      infrarecorder2.png

---

### Post by rfruth on 2007-10-03
Wonder if *any* CD boots, BIOS set okay ?

---

### Post by phoenix23 on 2007-10-03
Burned with k3b, same error...

What should bios be set to? I've booted from a cd before, but since added an extra hard drive...

---

### Post by Pumalite on 2007-10-03
In BIOS make sure CD is set to boot first in the boot order.

---

### Post by phoenix23 on 2007-10-03
Yes, I have CD first. Like I said before, I've booted the live cd, it just blacks out when I get past the the loading bar after "boot from cd" or "boot in safe graphics mode".

---

### Post by Pumalite on 2007-10-03
Try this:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

---

### Post by phoenix23 on 2007-10-03
> **Pumalite said:**
> Try this:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

I got an error:

> FATAL: Module piix not found.

---

### Post by ramjet_1953 on 2007-10-04
A few things to note.

1. Are you definitely burning it as an iso9660 image? Just burning it as a data CD doesn't work. Most burning software has the option to burn as an iso image in a drop-down menu.

2. What speed are you burning at? In a lot of instances, burning an iso image faster than 4 X can cause error problems.

3. Are you using high quality media? Quite often, cheap CDR's don't cut the mustard with iso images.

4. Have you checked the MD5 checksum of the image you downloaded? If it doesn't match, you have a corrupted image.

Regards,
Roger :cool:

---

### Post by phoenix23 on 2007-10-04
Yes, I have check all of those things.

I put in an old official Feisty disc I ordered from Canonical, and I'm getting the same error. Is there something with my Nvidia graphic driver that won't let me run live cds?

---

### Post by ramjet_1953 on 2007-10-04
Some hardware has problems without the correct drivers, when using the LiveCD.

A good option is to download the alternate CD iso and burn and use it.

It is a text based installer, but don't let that worry you, as it is very intuitive.

Once Ubuntu is installed this way, you can then load the drivers for your video card.

It is worth a try as many people have successfully installed this way.

Regards,
Roger :cool:

---

