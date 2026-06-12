---
title: "Videos and DVDs running funny"
date: 2005-08-15
forum: Absolute Beginner Talk
---

### Post by Muhammad on 2005-08-15
Where did I go wrong?

I did download and install the codecs, also I have WinXP on another partion.

---

### Post by KingBahamut on 2005-08-15
[QUOTE=Muhammad]Where did I go wrong?

I did download and install the codecs, also I have WinXP on another partion.[/QUOTE]
 Define Funny?

---

### Post by TristanMike on 2005-08-15
Hmmm, have you enabled DMA?
```
sudo hdparm -d1 /dev/hdc
```
assuming, of course, that the "hdc" is YOUR dvd drive. If you don't know, I just checked my device manager. I found my drive and clicked on the advanced tab and the top one told me it was hdc.

This will enable it for your session, but will have to re-enable it if you reboot. Enabling it permenantly is a little more tricky and I wouldn't feel comfortable explaining it to you as I haven't been able to set it up yet either. perhaps someone else might.

---

### Post by Muhammad on 2005-08-15
It's lagging alot.

---

### Post by Muhammad on 2005-08-15
[QUOTE=TristanMike]Hmmm, have you enabled DMA?
```
sudo hdparm -d1 /dev/hdc
```
assuming, of course, that the "hdc" is YOUR dvd drive. If you don't know, I just checked my device manager. I found my drive and clicked on the advanced tab and the top one told me it was hdc.

This will enable it for your session, but will have to re-enable it if you reboot. Enabling it permenantly is a little more tricky and I wouldn't feel comfortable explaining it to you as I haven't been able to set it up yet either. perhaps someone else might.[/QUOTE]

Apperantly my DVD drive is hda, I tried the command, and I recieved the following messege:

> /dev/hda:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

But the videos are still lagging...

---

### Post by TristanMike on 2005-08-15
Ok, that turned it on, and if you tried the videos after you tried the command and they're still laggy, I don't know what to tell you, but then again, as I said, I'm an idiot.  :) 

If you haven't mentioned this already, what player are you using? Have you tried VLC (it's just my favorite).

---

### Post by Muhammad on 2005-08-15
I've tried Totem and RealPlayer, I'm going to try VLC now. :)

---

### Post by RastaMahata on 2005-08-15
maybe its not hda at all...
issue this and paste the resutls```
cat /etc/fstab
```

---

### Post by Muhammad on 2005-08-15
[QUOTE=RastaMahata]maybe its not hda at all...
issue this and paste the resutls```
cat /etc/fstab
```[/QUOTE]
 There you go:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


---

### Post by RastaMahata on 2005-08-15
[QUOTE=Muhammad]There you go:[/QUOTE]
 well... your cdrom is hdb, not hda ;)

---

### Post by the_purulent on 2005-08-15
I had that problem at first, but I switched to mplayer and poof!
It went away :)   Just had to make sure I had opengl support turned on in the preferences.

---

### Post by Muhammad on 2005-08-15
OK thanks everyone for the help, mplayer did the trick :)

I'm still wondering why Totem wasn't able to run the videos, although it was able to do so before re-installing ubuntu.

---

### Post by Stormy Eyes on 2005-08-15
[quote="Muhammad"]I'm still wondering why Totem wasn't able to run the videos, although it was able to do so before re-installing ubuntu.[/quote]

I don't know, but I've always found Totem to be flakier than a Manhattan croissant. Nice avatar, by the way. Glad I'm not the only *Digital Devil Saga* fan here.

---

### Post by Muhammad on 2005-08-15
LOL I'm glad I'm not either :D , can't wait for DDS2 to come out in November...

---

### Post by the_purulent on 2005-08-15
[QUOTE=Muhammad]OK thanks everyone for the help, mplayer did the trick :)

I'm still wondering why Totem wasn't able to run the videos, although it was able to do so before re-installing ubuntu.[/QUOTE]

Glad it worked!
*score on point for the newbie!*  :grin: 
I love this forum, it's nice to be able to help out once in a while too, instead of just asking all the questions ;)

---

