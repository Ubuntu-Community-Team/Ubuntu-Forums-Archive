---
title: "Problems with: Grub, CD Drive, Sound, Freezes, Fear..."
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Enjeru on 2006-09-24
Hey all, I'm new here.  I just got Ubuntu (maybe I was crazy but I backed up the few important things I had on my hard driver and destroyed Windows XP all together...) installed and working.  After some searching around the forum I mananged to get my wireless card working, as well the nVidia drivers for my Geforce Go 6800.  After that I got my resolution fixed (1440 x 900 is so much better than 1024 x 768).  Ok now for my huge list of problems:

1.  I think this started after I installed the nvidia drivers, because now grub trys to start kernel 2.6.15.26-k7, when I have kernel 2.6.15-26-386.  Pretty much all I have to do is to hit Esc and choose 386.  Is there any way I can make it use 386 by default, since if it tries to load k7, it just sits there doing nothing.

2.  Also, my cd drive is acting kind of funny.  Most of the time it works fine, but sometimes it just turns off after I eject a CD, and wont turn back on.  Restarting fixes it, for a little bit atleast...

3. I'm not sure if Ubuntu is using my sound card right because the volume seems so off, especially in real player because changing the volume has no effect at all, it just plays at some default volume setting.

4. Sometimes the destop seems to freeze, as in I can still move my mouse around, but I can't click anything.  I also don't think I can type anything either.

5.  Lastly, and least important at this time, is how do I get F.E.A.R. to work on Ubuntu.  I used wine to install it, the installation went fine, I just can't get wine to run it.  I also can't seems to download WineX, so I'm kinda lost at this point.

Here are the specs of my PC (maybe they'll help you guys to tell me what wrong):

P4 3.4GHZ 650 2MB 800FSB LGA775 TRAY (Hyber Thread)
1024 MB RAM:
2 PDP 512MB DDR2 PC4200 SO-DIMM CL4
NVidia Gefroce Go 6800:
AREA-51M 7700 D900T NVIDIA 42M 6800FXGO WITH 256MB MODULE
Hard drive:
SAMSUNG 40GB 5400RPM PATA
CD-Drive:
AREA-51M 7700 24X RV3 DVD CD-RW COMBO PANASONIC
Sound:
INTEL MOBILE INTEGRATED HIGH-DEFINITION AUDIO

Thanks to all in advance.:cool:

---

### Post by bulldog on 2006-09-24
Well I think you should take a look here for the right kernel and how to install [how did you get the k7 kernel anyway?]

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

You can make your 386 kernel start by default by altering your GRUB
You should look at this section:

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         2

Remember counting starts with a zero.

About your sound,right click your sound icon to see if there's something wrong.
Double click your sound icon to see more options.

Have no clough about wine and F.E.A.R
The malfunction of your cd-rom could have many reasons.

Freezing desktop,do a search.I thought you aren't the only one must be a topic about it.

---

### Post by maaronB on 2006-09-24
> **bulldog said:**
> Well I think you should take a look here for the right kernel and how to install [how did you get the k7 kernel anyway?]

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

You can make your 386 kernel start by default by altering your GRUB
You should look at this section:

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         2

Remember counting starts with a zero.



Just for clarification. 
Is what you are saying that he should open up the 
/boot/grub/menu.lst 
and change the line that says
default 0
to become
default 2

---

### Post by bulldog on 2006-09-24
Which number he should use is depending on his GRUB and which entry he want to use,mine is 2,but as said counting starts at zero.

gksudo gedit /boot/grub/menu.lst

and count your entrys starting with zero and fill in what entry you want to boot.

---

### Post by Enjeru on 2006-09-24
ok i got the grub thing working (woot)

i checked out all my sound settings and everything is max and seems correct, yet the sound is really low no matter what.

thx for the help so far :D

---

### Post by xpod on 2006-09-24
Theres a couple of things you can do to check your sound like typing "alsamixer" in the terminal or checking in the "multmeadia system selector" that things aint got muddled...obviously the sound icon as bulldog said.

Sound can get messed up when you start using all sorts of different stuff and might just need some fiddling about with

EDIT:the multimedia thing can be enabled in preferences via alacarte menu editor.....you can test sound with it too

---

### Post by maaronB on 2006-09-24
On the CD problem is sounds like it might be umouting it after you eject a CD.
Try making sure it is mounted the next time it has problems.  
If that is the cause it should be easy to fix.

---

### Post by Enjeru on 2006-09-24
this is the second time i posting this cause first time desktop and mouse froze, but for whatever reason, music kept running...

ok well i got the sound fixed, i think ubuntu was using the wrong device to run my sound and was turning off my front speakers as well.

on the cd drive, how do i check if it's being unmounted? and how do i keep it from happening?

---

