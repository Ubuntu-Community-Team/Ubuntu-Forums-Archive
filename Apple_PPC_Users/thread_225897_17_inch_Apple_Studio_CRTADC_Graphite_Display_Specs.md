---
title: "17 inch Apple Studio CRT/ADC Graphite Display Specs (M7770 &amp; M7768)"
date: 2006-07-30
forum: Apple PPC Users
---

### Post by LususX on 2006-07-30
It seems that only 3 people have attempted to install Dapper on a G4 Cube with a 17 inch Apple Studio Display CRT/ADC Graphite Monitor. Several websites have it's model number listed as M7768, but according to apple's website it is M7770. The HorizSync is 80 kHz and the VertRefresh is 60-160 Hz.

I configured my xorg.conf file with the following.

Section "Device"
        Identifier      "ATI Technologies, Inc. Rage 128 PF/PRO (AGP x2)"
        Driver          "r128"
        BusID           "PCI:0:16:0"
        VideoRam        16384
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Studio Display CRT ADC 17"
        Option          "DPMS"
        HorizSync       80
        VertRefresh     60-160
EndSection

my yaboot.conf

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
##      append="quiet splash video=ofonly"
        append="quiet splash video=aty128fb"

then in a terminal "sudo ybin -v" which will write your yaboot file to the firmware.

reboot and you SHOULD have a working 17" display. Unfortunatly you will not see it booting, but when GDM launches, it will look normal again.

---

### Post by ZekeG4 on 2006-07-30
It worked! Thanks a lot! I was pretty happy to finally be able to load up Xubuntu. This was my first linux install and I was kind of sad it was turning out to be a bust.

One quick and newbie question. What resolution does that leave it on? It's a bit high for the size of the monitor and the only other option it gives me doesn´t work. I would like to leave it a 1024x768.

Thanks a lot for the help. It really did the trick. :)

---

### Post by LususX on 2006-07-31
My screen is currently set at 1280 x 1024 @ 75 Hz. and that is the only selection I currently have. I haven't messed around with the xorg.conf file to see if i can change it.

---

### Post by ZekeG4 on 2006-07-31
Yep, that´s what happened to me. But xvfce dosn't recongize any other res. Well, dosn´t matter. I got used to having the extra real estate. :D

Thanks a lot. I know tha a lot of people online had this issue.

---

### Post by cmff34 on 2006-08-01
I have been trying to forever to get my cube to run ubuntu, kubuntu, xubuntu, you name it.  I can't wait to try this!  Thank you, thank you, thank you!  Sadly my cube is currently in storage, or I would try it right away.  Thanks again for all that you have done!

---

### Post by LususX on 2006-08-01
I didn't install dapper directly, I had an install CD from breezy and then upgraded to dapper. Has anyone been able to boot from the dapper live CD and install that way?

---

### Post by avtolle on 2006-08-01
[http://ubuntuforums.org/showthread.php?t=211620&highlight=ppc+live+cd](http://ubuntuforums.org/showthread.php?t=211620&highlight=ppc+live+cd) indicates at least one person did! (But not without reburning).

---

### Post by LususX on 2006-08-01
naw, i was referring to the video problems and installing with the live CD.

---

### Post by ZekeG4 on 2006-08-01
If you could get gdm to reload maybe you could. I coudn't get the live cd to restart after it crashed and I edited the xorg.conf file. Finally I had to use the Xubuntu install cd, and I use live if all hell breaks loose.

---

