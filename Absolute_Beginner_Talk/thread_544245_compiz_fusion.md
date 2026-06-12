---
title: "compiz fusion"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by drpas2k on 2007-09-06
I have installed Compiz fusion. I do not get any effects.

I get following result in terminal

$ compiz
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: Not present. 
aborting and using fallback: /usr/bin/metacity 
:confused::confused:
please advise me what to do .Thanks

---

### Post by funpop on 2007-09-06
whats your graphics card ?
and which drivers are you using ?

---

### Post by n3tfury on 2007-09-06
which guide did you use?  if you didn't use [[COLOR="DarkOrange"]this one,[/COLOR]]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty") i HIGHLY recommend it.

---

### Post by drpas2k on 2007-09-06
> **funpop said:**
> whats your graphics card ?
and which drivers are you using ?

Please tell me how to find my graphic Card ..thankx

---

### Post by n3tfury on 2007-09-06
in a terminal type:

```
lspci
```

mine was at the bottom of the output that came back:

01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by drpas2k on 2007-09-06
> **n3tfury said:**
> in a terminal type:

```
lspci
```

mine was at the bottom of the output that came back:

01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

This is what I have got.
$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 70)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8

---

### Post by n3tfury on 2007-09-06
you going to answer my first post?

---

### Post by drpas2k on 2007-09-06
> **n3tfury said:**
> you going to answer my first post?

I used this guide 
[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

I think it is same as you have recommended

Thankx

---

### Post by n3tfury on 2007-09-06
i have a feeling your onboard card is not going to cut it.  you could download the [sabayon]("http://wiki.sabayonlinux.org/index.php?title=Introduction") live cd that will give you a good indication if your onboard card will do anything at all.

---

### Post by drpas2k on 2007-09-06
Do you mean with hardware, I can not use Ubuntu 7.4 with compiz fusion?

Do you also mean I have to change my Pentium 4 PC

---

### Post by n3tfury on 2007-09-06
> **drpas2k said:**
> Do you mean with hardware, I can not use Ubuntu 7.4 with compiz fusion?

Do you also mean I have to change my Pentium 4 PC

no, i'm saying that your graphics card might not be able to handle compiz/bery or compiz-fusion.  remember, compiz-fusion is also not totally stable for some people using Feisty, although it has been for me.  

just burn the live CD or DVD that i linked to and see if it works.  that way you don't hose your Feisty install.

---

### Post by funpop on 2007-09-06
did you install nvidias drivers for that card ?

sudo aptitude install nvidia-glx-new
sudo nvidia-glx-config enable
sudo nvidia-xconfig --composite --render-accel --add-argb-glx-visuals

give this a try

after a restart start compiz with: compiz --replace

---

### Post by drpas2k on 2007-09-06
Thank you for all the help. I hope Gutsy will solve my problem when it is released.

thankx

---

### Post by n3tfury on 2007-09-06
> **funpop said:**
> did you install nvidias drivers for that card ?

sudo aptitude install nvidia-glx-new
sudo nvidia-glx-config enable
sudo nvidia-xconfig --composite --render-accel --add-argb-glx-visuals

give this a try

after a restart start compiz with: compiz --replace

nvidia driver for the prosavage card?  :confused:

anyway, seems i was correct:

[http://ubuntuforums.org/showthread.php?t=328273&highlight=S3+VT8375](http://ubuntuforums.org/showthread.php?t=328273&highlight=S3+VT8375)

---

### Post by n3tfury on 2007-09-06
> **drpas2k said:**
> Thank you for all the help. I hope Gutsy will solve my problem when it is released.

thankx

it won't.  see my post above.

---

### Post by funpop on 2007-09-06
sorry, i did read too fast, somehow i thougt there would be a nvidia 6xxx

---

### Post by afonic on 2007-09-06
The card you have cannot run Compiz as it doesn't support 3D acceleration under Linux AFAIK. I used to have one of those and the driver was 2D only.

But even if it had I don't think it would be fast enough. Just get another card (an nVidia one better) if you want to get Compiz.

---

### Post by drpas2k on 2007-09-06
> **afonic said:**
> The card you have cannot run Compiz as it doesn't support 3D acceleration under Linux AFAIK. I used to have one of those and the driver was 2D only.

But even if it had I don't think it would be fast enough. Just get another card (an nVidia one better) if you want to get Compiz.

Ok I will purchase one. Will you please tell me correct specification of nVidia.

thanks. mine is P4  1.5 GHz single hard disk. 512 Ram with WinXp dual boot.

---

### Post by afonic on 2007-09-06
You'll need an AGP card, be carefull not to get a PCI Express cause it won't fit in your PC.

Now if you are not interested in gaming you could get a Geforce 5200 that would be like $30. If you need a little more horsepower search for something better, like a 6200 or 6800 that should be around $50 - $90.

---

