---
title: "Error when loading ubuntu"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Burton062 on 2007-06-03
Heard about this from a co-worker and can't wait to get it up in running but I think I'm stuck..

I went ahead and burnt the Ubuntu 7.04 x64 edition iso and use it to boot up the computer on restart. I get what seems to be the main menu and select the run/install (Top option). It seems to complete some of the things it is suppose to do (Ubuntu progress screen loads) and then gets into loading seperate drivers. When it gets to that point I get an error about bcm43xx microde5.71.06400 not available or load failed. (Sometimes the # at the end seems different but the bcm43xx microde always is the same.) After the error comes up and the rest finishes the screen just goes black. My computer still runs but doesn't seem to be working/processing information. I've left it sit for about 30 mins and nothing. Just wondering how I can get this fixed so I can get this thing working.

System specs.
HP Pavilion dv9000 laptop
1 gig ram
AMD Turion 64 duel core
Nvidia go video card

Thanks for your help !! Can't wait to get this running :o

---

### Post by psyopper on 2007-06-03
A quick google search reveals that the failure is on loading your onboard Broadcom based wifi adapter.

Did you burn a LiveCD? For giggles see if you can get a 32bit LiveCD to boot into and see if it works better. 

By "black" is it totally black? Or is there a blinking cursor somewhere on the screen? If there is a blinking cursor you can try typing "startx" (without the quotes) to launch the GUI. The other option is to launch into "safe mode" and see if it boots differently.

---

### Post by shearn89 on 2007-06-03
Do you have a wireless card?

edit: just noticed that i'm a bit slow....

---

### Post by overdrank on 2007-06-03
> **Burton062 said:**
> Heard about this from a co-worker and can't wait to get it up in running but I think I'm stuck..

I went ahead and burnt the Ubuntu 7.04 x64 edition iso and use it to boot up the computer on restart. I get what seems to be the main menu and select the run/install (Top option). It seems to complete some of the things it is suppose to do (Ubuntu progress screen loads) and then gets into loading seperate drivers. When it gets to that point I get an error about bcm43xx microde5.71.06400 not available or load failed. (Sometimes the # at the end seems different but the bcm43xx microde always is the same.) After the error comes up and the rest finishes the screen just goes black. My computer still runs but doesn't seem to be working/processing information. I've left it sit for about 30 mins and nothing. Just wondering how I can get this fixed so I can get this thing working.

System specs.
HP Pavilion dv9000 laptop
1 gig ram
AMD Turion 64 duel core
Nvidia go video card

Thanks for your help !! Can't wait to get this running :o

Hi and welcome this thread may be of some help
[http://ubuntuforums.org/showthread.php?t=273767&highlight=HP+Pavilion+dv9000+laptop](http://ubuntuforums.org/showthread.php?t=273767&highlight=HP+Pavilion+dv9000+laptop)
Hope this helps and good luck!:popcorn:

---

### Post by Burton062 on 2007-06-03
I did try to other versions of live but receive the same error on both versions (the bcm43xx error). Yes I do have a wireless card in the laptop and noticed that it did have something to do with it when I was searching earlier. Thing is I'm very new to this and have no idea how it could be corrected.

In the thread links posted I was given some commands I can try to run to fix it. Thanks for the help.. I'll let you know how it goes in a few minutes.

Great community btw :)

---

