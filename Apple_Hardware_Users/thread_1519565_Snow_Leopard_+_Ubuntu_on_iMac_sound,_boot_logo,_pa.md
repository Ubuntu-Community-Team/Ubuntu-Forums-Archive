---
title: "Snow Leopard + Ubuntu on iMac: sound, boot logo, partitions"
date: 2010-06-28
forum: Apple Hardware Users
---

### Post by mk12 on 2010-06-28
So I burned Ubuntu 10.04 LTS 64-bit onto a CD, tried it out then tried installing it. There was no option for side-by-side installing, however, so I went back to Snow Leopard and used Bootcamp to create a 95 GB partition for Ubuntu (the rest for OS X) in the iMac's (24" Model) 640 GB HD. I went to install ubuntu again, and this time there was an option to install side by side. I moved the slider so that Ubuntu had 95 GB, and this other partition had 8 GB.
I have three problems:

[LIST=1]
[*]I installed the proprietary NVIDIA accelerated grahics driver  (version current). However, when I shut down and booted up again, it did  some weird stuff and said there was a problem and asked if I wanted to  use the generic graphics driver. Instead I chose to create a new  modified one or something and it said to reboot. Now the accelerated  graphics work fine, BUT the ubuntu boot logo is always blown up and  fuzzy. Kind of annoying, is there a fix for that?
[*]There is no sound at all, speakers or headphones. I tried alsamizer, they aren't muted. The sound card is recognized.
[*]If I have just Mac OS X and Ubuntu, how many partitions should there be? Right now in the 640 GB hard drive (looking in Ubuntu's disk utility), There is EFI:210 MB FAT, Macintosh HD:537 GB HFS+, Free:8.1GB, Unknown:1.0MB(BIOS Boot Partition), 91GB:ext4(Linux Basic Data), 3.9GB:Linux swap. Which of these do I need? How can I grow either Ubuntu or Mac OS X into that free space?
[/LIST]
I also plan to install rEFIT, that should be straightforward right?

Aside from these problems Ubuntu seems amazing! I like the wobbly windows :P

Thanks!

---

### Post by linuxopjemac on 2010-06-29
which iMac exactly ?
```

sudo dmidecode -s system-product-name
```

---

### Post by mk12 on 2010-06-29
Actually I decided to uninstall Ubuntu and redo it to triple-boot my mac following [this guide]("http://lifehacker.com/5531037/"). Now I have the correct partitions, and I followed [this guide]("http://n00bsonubuntu.com/content/how-fix-big-blurry-and-ugly-logo-startupshutdown-ubuntu-1004-lts-lucid-lynx") to fix the blow up fuzzy boot logo (using 1920x1200 instead of 1200x1024). Here is the result of that command, linuxopjemac:
```
iMac9,1
```The audio still isn't working, but I'm going to try the various things listed [here]("https://help.ubuntu.com/community/Intel_iMac#Sound"). Also, since I'm using rEFIT I don't really need grub because If I chose Ubuntu at rEFIT I don't need another menu. Is there a way of disabling grub or hiding it? Thanks.

Update: Ok the things on that page didn't seem to do anything... Any help? Alsamixer is not muted.

---

### Post by linuxopjemac on 2010-06-29
ok, an iMac9,1

[http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=32](http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=32)

That's the only solution I got for you.

I guess when you compile the latest ALSA yourself, you may want to add
model=imac91
 or try backports:

[http://ubuntuforums.org/showthread.php?t=1486866](http://ubuntuforums.org/showthread.php?t=1486866)

---

### Post by mk12 on 2010-06-29
Thanks!! Just adding that one line worked perfectly, except there seems to constantly be a faint static noise. And when I raise the volume by clicking the F12 button, the static grows louder for a second, it sort of pulses. And earphones don't work, sound continues to come through the speakers and not the earphones. But I guess I should be happy that I have sound at all.

Also, headphones don't work. The sound continues playing through the speakers. Is there a fix for that?

update: The fuzzy/static/cracking/noise is getting *really* annoying. Sometimes I can't notice it, other times it's very audible. Usually changing the volume makes a little burst of static and sometimes moving the mouse does too. How can I fix this?

---

### Post by mk12 on 2010-06-30
The crackling sound is sometimes there, sometimes it isn't but when it is it is VERY annoying... I love using Ubuntu but not when it does this so please does anyone know how I can fix this?

---

### Post by linuxopjemac on 2010-07-01
Upgrade Alsa as I said earlier.

---

