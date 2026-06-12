---
title: "Wireless not working"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by kidob on 2007-06-13
So after some minor partitioning catastrophes while setting up a dual boot, my ubuntu is officially working; no problems whatsoever with the ATI card and got the resolution just right!

But the wireless isn't working and it doesn't seem to have detected my Broadcom 802.11 b/g card. I don't have ethernet where I am so I've had to boot into XP to get online for help. I have no idea what to do about this, any ideas would be much appreciated. Also, please note I'll have to download any drivers or other files from Windows so I'll need to know how to access them from Ubuntu in order to install them. Thanks! :D

-kidob

---

### Post by Brightbelt on 2007-06-13
Hi, Depending upon what Broadcom card you have this could maybe help you:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty) 

Also, I posted a short synopsis (referring to the same ubuntu.com tutorial but showing only which elements I did) of how I got my Broadcom 4318 to work:

[http://ubuntuforums.org/showthread.php?t=469927](http://ubuntuforums.org/showthread.php?t=469927) 

I hope this helps, Frank B.

PS If you're stuck, just Google "broadcom xxxx with Ubuntu" with "xxxx" being your model number. You can find that by running this in a terminal:
lspci      (that's the letter 'l', not a nymber 1)

---

### Post by kidob on 2007-06-13
> **Brightbelt said:**
> Hi, Depending upon what Broadcom card you have this could maybe help you:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty) 

Also, I posted a short synopsis (referring to the same ubuntu.com tutorial but showing only which elements I did) of how I got my Broadcom 4318 to work:

[http://ubuntuforums.org/showthread.php?t=469927](http://ubuntuforums.org/showthread.php?t=469927) 

I hope this helps, Frank B.

PS If you're stuck, just Google "broadcom xxxx with Ubuntu" with "xxxx" being your model number. You can find that by running this in a terminal:
lspci      (that's the letter 'l', not a nymber 1)


Thanx Brightbelt. I read your solution but it looks like you had an alternative internet access from Ubuntu. I'm stuck in Windows until I either get wireless going on Feisty or get an ethernet cable, so I'm not sure that will work for me.

---

### Post by Brightbelt on 2007-06-13
There is one possibility I see for you in windows since the tutorial gives you this link from which to download the firmware:

[Http://boredklink.googlepages/com/wl.apsta.o](Http://boredklink.googlepages/com/wl.apsta.o) 

You could download that in windows and copy it to a flash drive or whatever and then transfer it to your ubuntu desktop and go from there. 

I'll admit it, though, I downloaded that and tried to do stuff with it, but it eluded me. But the tutorial says it is the firmware you need. I would just try to follow the tutorial from there as best as you can.

I hope this helps, Frank B.

---

### Post by Brightbelt on 2007-06-13
Sorry for the typo - that's
[http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)

Frank B.

---

### Post by Brightbelt on 2007-06-13
There's also this link from which you can download a deb in windows:
[http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb](http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb)
 
Then copy it to a flash drive, transfer it to ubuntu and then follow the tutorial instructions etc....

Frank B.

---

### Post by kidob on 2007-06-13
Thanks I'll try the tutorials. I also read on the wiki you referred to that kernel 17 includes drivers for broadcom wireless. I think the installation CD's use kernel 15. I'm thinking the quickest fix may be to just update the kernel...

---

### Post by kidob on 2007-06-13
> **Brightbelt said:**
> There's also this link from which you can download a deb in windows:
[http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb](http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb)
 
Then copy it to a flash drive, transfer it to ubuntu and then follow the tutorial instructions etc....

Frank B.


You rock Brightbelt, that deb file you suggested worked like a charm! I just downloaded in Windows, burned to CD, ran the file in Ubuntu and my wireless was up like that. I just wish this was a file like that to get Photoshop working ;)

---

### Post by Brightbelt on 2007-06-14
Good Deal! I'm glad you got it going. 

Btw, Photoshop 7.0 works very well on wine. Plus, PS 7.0 was before Adobe got into the activations like MS etc. 

If you need to go to higher PS versions like CS or CS2, CrossOver might work better, but I have no hard data to back that up. 

Thanks for letting me know your wireless worked. It's really cool to hear the results of your efforts.

...Frank B.

---

### Post by Brightbelt on 2007-06-14
In case the wine option interests you, you can install wine (basically stands for "windows emulator") from the Synaptic Package Manager (System menu/Administration/Synaptic...).

Install Wine first. When you put your PS CD in to install, right-click on the autoplay.exe file and choose "open with another application".  Then at the bottom of the window, there's an option called "run your own command"  (I may not have that exact, but you'll know it when you see it).  Then type "wine" and click OK.

Sometimes it needs to reset and it won't get going right away. So right-click the autoplay.exe file again and usually, every time, Ubuntu "learns" your choice and you'll see the choice there "open with wine" or "open with windows emulator". And that's it... 

Make sure you have the most recent version of wine, since it can make the difference between programs freezing or running more smoothly.  Refer to [www.winehq.org](www.winehq.org) if necessary. 

Thanks, Frank B.

---

