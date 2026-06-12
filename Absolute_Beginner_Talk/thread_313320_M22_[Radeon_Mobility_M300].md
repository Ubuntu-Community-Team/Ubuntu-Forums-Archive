---
title: "M22 [Radeon Mobility M300]"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by flash2lightning on 2006-12-05
i recently installed ubuntu onto my brother's laptop, and i cant figure out how to get the ati drivers to work and the graphics card to do beautiful things...

its called a M22[Radeon Mobility M300]

---

### Post by Fully216 on 2006-12-05
ATI does not support linux until recently, at least to my knowledge, so don't try to go to their website looking for support (aside I have already done so).  I found that many people have had problems getting ATI video to work under Linux on laptops.  That is the bad news.

The good news is people have gotten the card to work on other systems like suse.  I believe the driver you need is fglrx_6_8_0-8.22.5-l.i386.rpm, or a newer version if available.

---

### Post by Fully216 on 2006-12-05
You might also try emailing customer care to see if they call tell you where the driver can be found.  It might be the case you card is no longer supported, which is why it is not listed.

You can try the default fglrx driver located in the repos:

sudo apt-get update 
sudo apt-get install xorg-driver-fglrx

Make sure fglrx is not disabled: 'sudo gedit /etc/default/linux-restricted-modules-common'

Generate a new set of module dependencies so the fglrx driver starts properly. 'sudo depmod -a'

now configure xorg to use your graphic card. 
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv

to make sure the video is not choppy, you might need to disable the composite extension (in /etc/x11/xorg.conf)

Section "Extensions"
        Option      "Composite" "0"
EndSection

There still might be a lot of troubleshooting, as it is a trial/error process for most people.

I hope this helps! :-)

---

