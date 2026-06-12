---
title: "Jaunty 9.04 on Macbook 4,1"
date: 2009-04-27
forum: Apple Hardware Users
---

### Post by hollyjester on 2009-04-27
I just installed Jaunty on my Macbook 4,1. The graphics driver is not recognized, and as a result compiz visualizations are disabled. Is there a plan to fix this issue?

---

### Post by transmition on 2009-04-28
I'm in the same boat as you. A fix is in the works. No idea when it will come. Could be days, could be months, or never...

---

### Post by -nat- on 2009-04-28
I also have the same problem (Although I have a Macbook 3,1 not 4,1). I tried a few different fixes, but none seem to have worked, but one of them has managed to stuff up my wireless internet on Ubuntu :(
Hopefully there will be a fix soon!

---

### Post by pxwpxw on 2009-04-28
Is this the same problem with the Intel 965 graphics?

[http://ubuntuforums.org/showthread.php?t=1139247](http://ubuntuforums.org/showthread.php?t=1139247)

[http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

---

### Post by __david on 2009-04-28
Graphics are working on my 4,1. Just installed the nvidia-drivers through jockey.

Did you try to manually install the drivers using synaptic?

---

### Post by maffix on 2009-04-28
I think that is a bug relative to "Driver hardware's" tool that don't  recognize ours graphic and wireless proprietary drivers.
You have to install manually by Synaptic.
For my wireless card (broadcom 4328) was enough to activate and downloaded(in Synaptic) the "b43-fwcutter" packet.
For my graphic card (nvidia 8600 GT) I have select the 183 driver.
Both solutions works perfect!

---

### Post by hollyjester on 2009-04-28
What about for the graphics driver for a Macbook 4,1.

---

### Post by phico on 2009-04-28
Hello,
I did not encounter any problem on mine, here is the
driver I use :

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=111571&stc=1&d=1240951435[/IMG]

My installation note are here :
[http://ubuntuforums.org/showthread.php?p=7170629#post7170629](http://ubuntuforums.org/showthread.php?p=7170629#post7170629)

Could you check your MBP version : 
sudo dmidecode -s system-product-name
should give
MacBookPro4,1


Hope this help

---

### Post by hollyjester on 2009-04-28
Well, that doesn't appear for me. I followed these instructions:
[http://ubuntuforums.org/showthread.php?t=765875]("http://ubuntuforums.org/showthread.php?t=765875")

Also, my iSight is not playing back the video properly, so that is a big issue, as I use Skype on Ubuntu often.

Can I reverse what I did?

---

### Post by __david on 2009-04-29
Hollyjester,

try out the instructions i gave to mclarenracer: [http://ubuntuforums.org/showthread.php?p=7174614#post7174614](http://ubuntuforums.org/showthread.php?p=7174614#post7174614)

---

### Post by elamericano on 2009-04-29
My MacBook4,1 shows Intel GMA X3100, not Nvidia. Shouldn't all MB4,1s be the same? (Maybe you have a Pro?)

Anyway, I see no desktop effects.

---

### Post by __david on 2009-04-29
> **elamericano said:**
> My MacBook4,1 shows Intel GMA X3100, not Nvidia. Shouldn't all MB4,1s be the same? (Maybe you have a Pro?) Oops, my bad :oops:
Yes, I am using a MBP

---

### Post by Claritux on 2009-04-29
Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1131754](http://ubuntuforums.org/showthread.php?t=1131754)

---

### Post by hollyjester on 2009-04-30
Well I am sort of a n00b. Hehe, how do I add the it to xorg.config?

---

### Post by hollyjester on 2009-05-02
The card is an Intel card not Nvidia. So I don't think _____david's solution will work. I bypassed the blacklist, but my video playback is distorted. Everything has a green hue to it. Is there a way to fix this?

---

### Post by hollyjester on 2009-05-02
Okay, I just realized my effects cannot be enabled as there isn't a recognizable driver. But since I bypassed the blacklist my video playback is not functioning properly. So now I have two problems?

---

### Post by hollyjester on 2009-05-02
Okay fixed the new problem. I just uninstalled the nViddia X packages. Still have problems with video playback though.

---

### Post by Tofuik on 2009-05-03
The proprietary drivers now show up if searched for (they didn't for a while)

I'm using version 180 on my 4,1 MBP

Everything seems to be working fine now, even games work (Warsow would glitch out until I got the driver)

---

### Post by hollyjester on 2009-05-03
Exactly what am I supposed to do?

---

### Post by Tofuik on 2009-05-03
System > Administrator > Hardware Drivers

A couple should pop up, I used 180

---

### Post by hollyjester on 2009-05-03
Except it doesn't show up for me. I have to manually install them, but I don't know the package name. There is a nvidia 180 package, but I am using a Macbook, not a Macbook Pro. So my driver I think is Intel.

---

### Post by Tofuik on 2009-05-03
mine didn't show up for a few days.  After I updated they popped up though.

---

### Post by cyberdork33 on 2009-05-03
> **hollyjester said:**
> Except it doesn't show up for me. I have to manually install them, but I don't know the package name. There is a nvidia 180 package, but I am using a Macbook, not a Macbook Pro. So my driver I think is Intel.
and nothing will show up. The correct driver is already used for your machine.

---

### Post by hollyjester on 2009-05-05
Well, I have visualizations. My driver doesn't appear. And my iSight doesn't register, even though I have the isight.fw file in /lib/firmware

---

