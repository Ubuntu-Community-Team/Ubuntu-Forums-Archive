---
title: "Getting Wireless Working"
date: 2007-05-08
forum: Apple PPC Users
---

### Post by megabenman on 2007-05-08
Hi.  I'm trying to get airport extreme working on an iMac G5, Rev B, with Kubuntu 7.04.  Here are the steps I've done:

Ok, I've gotten blacklist ndiswrapper in the file thanks to the kdesu command. But now, it still isn't working! Every time I try to connect to the network it stops at 28 % (configuring device). Only a couple times it reached 57% (configuring IP address... I think). I can't see what's wrong. Here is what I've done (remember I'm using Kubuntu, not Ubuntu).

1. Updated repositories.
2. Ran sudo apt-get install bcm43xx-fwcutter with success.
3. Downloaded the wl_apsta.o file to my desktop.
4. Ran sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o with success.
5. Ran sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` -/Desktop/wl_apsta.o with success.
6. Ran modrpboe bcm43xx.
7. Ran sudo ifconfig eth1 up.
8. Put blacklist ndiswrapper in the blacklist file.

Nothing seems to work. Any suggestions?

(Note:  I did step 8 because I had a 4318 card, so I needed to add that line.)

Also, the network I'm trying to connect to is called default, and it has a hex code of cccccccccc (10 c's).

---

### Post by stmiller on 2007-05-08
So when you do

sudo modprobe bcm43xx

it loads okay and without errors? And you can verify that it is loaded? (Do a lsmod)

---

### Post by megabenman on 2007-05-08
Yes, it works without errors.  When I type lsmod, it displays (among other things):
```
bcm43xx     189644     0
```

---

### Post by megabenman on 2007-05-09
Ok... for some reason..... I logged into Kubuntu and my wireless just magically worked... I don't get it but I'm not going to argue with it :)

But now I have new problems.  I looked on the wiki to figure out how to configure bluetooth (I'm using the apple wireless mouse + keyboard).  I managed to configure my mouse to work, but I can't figure out the keyboard.  For some reason, this little white K symbol with blue around it in the bottom right of the screen says that it's connected to my keyboard, but it's not working.  When I double click the symbol, it opens up bluetooth:/ which shows two larger versions of the symbol and one picture of a blurry pixelized joystick.  The symbols say localhost and megabenman's keyboard.  The blurry joystick says megabenman's mouse.  Any idea why this is?

Also, even before I installed bluetooth it would always "recognize" my keyboard (but not my mouse).  I can't figure it out.  I need to somehow tell kubuntu to stop connecting to my keyboard, and then run the search command.  Any ideas?

edit:  huh... I think I solved it.  I just shut off my keyboard... Hahaha.... guess I don't have any more questions (for now).

---

