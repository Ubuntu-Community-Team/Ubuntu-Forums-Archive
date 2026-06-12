---
title: "wifi problem (noob, sorry)"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by chirulais on 2008-01-21
well, i switched to ubuntu like 10 times but i keep going back to vista because of the wireless, i did the ndiswrapper thing and actually i could conect (near to my router) but when im in my room i just cant connect (i have lake 10% of signal strenght) but in vista im able to conect and it is not slow. then i got my gutsy cd in mail i installed and found out my wifi broadcom card was in the restricted manager driver thing an used that but i did not work again when im far from my router.
any help us going to be apreciated, thanks.
and i hope that when i learn more about linux i can help out, just like you do. =D
Sorry for my weak english (im mexican):lolflag:

[edit] im runing gutsy in a dell inspiron 1501 with 512mb ram and a amd mobile sempron =D
[EDIT]
Meborc gave me a great link, hope it works for you:
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

this is a great tutorial for installing your broadcom wireless chipset =D
Worked like a charm for me. =D
cheers
Happy New Year Homies!

---

### Post by meborc on 2008-01-22
i have dell inspiron 1520... using Broadcom Corporation BCM94311MCG wlan mini-PCI

i have used this howto - [http://blender.chaloupkovi.cz/tutorials.html](http://blender.chaloupkovi.cz/tutorials.html) to get it working

broadcom has is and will be a very bad card for linux systems just because their driver support is bad

please open terminal and post here what output you get when inserting ```
lspci
```

you should see a broadcom somewhere... after that is the chip model, this will help you to follow the tutorial i linked

---

### Post by chirulais on 2008-01-22
hey thankyou but the link you sent me is fot a 3d modeling program blender i think, would you mind posting the correct page, please?
Thank you for helping me =D

---

### Post by Hightide on 2008-01-22
> **chirulais said:**
>  wifi broadcom card 

[edit] im runing gutsy in a dell inspiron 1501 with 512mb ram and a amd mobile sempron =D

HI chirulais

have you had a look at Dark Noobs 'how to' with the Broadcom card?. It may provide additional help.

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

by the way, you English is fine

regards
:)

---

### Post by meborc on 2008-01-22
omg... i'm so sorry :D

i didn't even realize

this is the link - [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

sorry again

---

### Post by rosegarden78 on 2008-01-22
Too bad they don't have a package like BCM43xx in the repositories.  I hope you find the "firmware cutter" or try downloading fw-cutter.  Ndiswrapper never worked for my BCM43xx card and I doubt it would work for yours.  FW-cutter did work and I suggest trying it.  Basically the software is inside your wifi card and needs to be ripped out.

I think bcm43xx is included with Gutsy.  You could try typing modprobe bcm43xx.  That would load the driver for my card.  It might also work for your card.  And there are very good tutorials on bcm43xx here on the forums.

I don't want to upgrade a three-year old laptop so I'm using Xubuntu with Nautilus file manager.  If and when this laptop's hardware dies completely I'll consider a new computer ... for Linux of course.  If it comes with Vista so be it.

---

### Post by chirulais on 2008-01-22
meborc thankyou worked like a charm !!!
=D

---

