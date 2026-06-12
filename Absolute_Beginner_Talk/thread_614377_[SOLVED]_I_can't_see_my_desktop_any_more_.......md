---
title: "[SOLVED] I can't see my desktop any more ......"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by tahitiwibble on 2007-11-15
I just had to buy a new motherboard and because of not being able to configure the video properly, had to put up with very very low resolution on my monitor which meant huge characters, windows, icons etc. etc.

I did all kinds of research and eventually was able to designate the correct driver for my motherboards video (S3 Unichrome) .............. when I rebooted the computer the screen resolution defaults to 1600 x 1200 @ 60Hz (I can't decipher anything on the screen) which is too much for my monitor that wants 1280 x 1024 @ 85Hz.

Question is ........... How can I change the screen resolution at boot up? I have booted from 7.04 cd and can adjust the resolution to whatever I desire while working from live cd. How may I change the machines resolution from the 7.04 cd so that it holds good while booting from my hard drive?

---

### Post by tahitiwibble on 2007-11-15
sorry to bump this but I can't stop the cold sweats ............

---

### Post by tahitiwibble on 2007-11-21
I now have a completely useless computer and can no longer stop the machine from defaulting to a resolution that is not supported by my monitor .......... I really have no idea what to do .............. heeeeeeeeelp

---

### Post by daimaru on 2007-11-21
once you get to your graphical login or desktop hit ctrl+alt+F1 this gets you to terminal
login and then edit your xorg.conf file
```
sudo nano /etc/X11/xorg.conf
```
locate -- Section "Screen" --
under modes add your desired resolution (deleting any 1600x1200 stuff)
for example:

Modes		"1280x1024@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	

or whatever you need. note that the first mode in the line is the one that your xserver should default to. so make it your 1280x1024@85

get out of nano and save changes hit ctrl+x enter enter i think.

Option 2
you could also rewrite your whole xorg.conf file by executing
```
sudo dpkg-reconfigure xserver-xorg
```
but then you have to define everything from mouse to keyboard and monitors horizontal/vertical sync ranges. (use as last resort)

---

### Post by wolfprintAG on 2007-11-21
well while your waiting for a reply of some sort - not sure how your seeing this scrren - but did you try to boot in a safe mode I couldnt remember if Ubuntu had one so had to google it but from what I can tell it does so maybe start there first booting in safe mode if you havent already.... also I didnt really read in depth here [https://launchpad.net/ubuntu/+source/xorg/+bug/59618](https://launchpad.net/ubuntu/+source/xorg/+bug/59618) but it may be of some sort of help - good luck - now I think about it I know the install cdd has safe mode I remember when I first did it I could do to much of nothing cause everything was giant - good luck is all I can really give you!

Nevermind I see someone with some knowledge helping

---

### Post by tahitiwibble on 2007-11-22
Thanks to both of you guys for the help.

I just couldn't take it any more and I ended up doing a lovely fresh install of Feisty 7.04 and everything works perfectly again ........... I will not be re-installing the update to Gutsy for quite some time to come, if ever!?

---

### Post by tiachopvutru on 2007-11-22
> **tahitiwibble said:**
> Thanks to both of you guys for the help.

I just couldn't take it any more and I ended up doing a lovely fresh install of Feisty 7.04 and everything works perfectly again ........... I will not be re-installing the update to Gutsy for quite some time to come, if ever!?

Usually, it's more recommended to do fresh install of new version rather than upgrade.

---

### Post by tahitiwibble on 2007-11-22
> **tiachopvutru said:**
> Usually, it's more recommended to do fresh install of new version rather than upgrade.

I will not forget this ........ thank you. Is migration an easy thing in this case?

---

