---
title: "Natty on MacBook Air 3,1 (11&quot; late 2010)"
date: 2011-03-07
forum: Apple Hardware Users
---

### Post by wersdaluv on 2011-03-07
How's Natty compatibility on MBA 3,1? Last time I checked, there was no sound or only the headphone port didn't work. 

Thinking about upgrading to test Unity and GNOME 3.0 from PPA, but I can't afford incompatibilities like the sound issue.

---

### Post by Lusse on 2011-04-16
Hello!

I can confirm that the sound isn't working in latest Natty, even with "options snd-hda-intel model=mba31" in "sudo nano /etc/modprobe.d/alsa-base.conf".

:( I hope that it'll get fixed soon and will try to figure out the problem in any way I can :)

---

### Post by c3n on 2011-04-17
actually sound is already working. i upgraded from maverick to natty (64bit) and had to remove the snd-hda-dkms module since apparently sound is now supported with the original kernel. both intenal and headphones working now and even the microphone is now loud enough

---

### Post by Lusse on 2011-04-19
c3n you are my hero!

I've tried different kernels (I run 2.6.39.999 now), tried different alsa settings, googled and even tried looking at some source code in the kernel. I'm so glad that you pointed this out as I now have _everything_ working on my mac since I had some wireless issues with the driver used in maverick. Once again, thank you so much!

---

### Post by wersdaluv on 2011-04-19
> **c3n said:**
> actually sound is already working. i upgraded from maverick to natty (64bit) and had to remove the snd-hda-dkms module since apparently sound is now supported with the original kernel. both intenal and headphones working now and even the microphone is now loud enough
Awesome! Thanks! :D



I wonder how a clean install would look like.

---

### Post by eyerouge on 2011-04-30
> **c3n said:**
>  i upgraded from maverick to natty (64bit) and had to remove the snd-hda-dkms module

Great news. Thanks for sharing!

Would anyone want to elaborate on how I would do such a thing? Although I haven't gotten any sound on my 3,2 since the upgrade to 11.04 I can't seem to even figure out if I have the Mactel stuff loaded:
> 
snowdrop@air:~$ modprobe -l snd-hda*
kernel/sound/pci/hda/snd-hda-codec.ko
kernel/sound/pci/hda/snd-hda-codec-realtek.ko
kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
kernel/sound/pci/hda/snd-hda-codec-analog.ko
kernel/sound/pci/hda/snd-hda-codec-idt.ko
kernel/sound/pci/hda/snd-hda-codec-si3054.ko
kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
kernel/sound/pci/hda/snd-hda-codec-conexant.ko
kernel/sound/pci/hda/snd-hda-codec-via.ko
kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
kernel/sound/pci/hda/snd-hda-intel.ko
updates/dkms/snd-hda-codec-cirrus.ko

Edit:  Nevermind... just noticed it was easily done via Synaptic. Thanks again for sharing the love!

---

### Post by unagimiyagi on 2011-05-11
Hi, is there a detailed guide to install ubuntu 11 on the macbook air 3,1? I have this model and have a clean mac os x install and refit.  I've got "missing operating system" and don't know what else to do.  The macbook air is not recognizing the usb ubuntu install disk (i have it on a flash drive).

Thanks!

Edit: Fixed by finding an external cd/dvd drive to boot from.  If you're serious about ubuntu and of limited technical wizardry, just get one of these drives somehow.  It'll save you lots of headaches.

Incidentally, battery life is too good to be true.  Will need others to confirm that I'm not crazy.  7-8 watts being consumed at full brightness?  Seems impossible.

---

