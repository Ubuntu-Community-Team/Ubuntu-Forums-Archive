---
title: "I have an install problem that has to do with my ATI card."
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by thadiusdean on 2007-01-24
I've been looking around the forums and am seeing that ATI cards have been giving people problems. I've seen quite a few answers to some of these problems but in order to make sure everything is a-ok I'd appreciate direct instructions.

So here is the situation. I get to the first boot screen, and choose the run or install Ubuntu option or w/e it's called. I get to the point where it is nearly done loading up (the loading bar is maybe a 20th of the way finished.) Then the Ubuntu logo and text get white speckles around them, and just below the loading bar blue speckles go from one end of the screen to the other--then some green ones appear sometimes... but all that's not too important. I have read about changing the resolution using F4, and with a slightly higher resolution I discovered that it was trying to display a message. It's long winded but it gets down to the "no screens found" error that I've read so much about. It seems that I need to install some special type of the x.conf file or something that sounds similar to that. It appears to be easily remedied by just punching in a few lines into the command line/terminal but I need to know how to get to that when Ubuntu isn't even installed, and I also need to know what to type.

My graphics card is an ATI Radeon x850xt.

If you know of something else I can do, I'd appreciate it. I can use any help you throw at me. :)

---

### Post by mikewhatever on 2007-01-25
May be you can try installing from an Alternate install CD. Unlike LiveCD, it has text mode installer with just four colours. See this site for howto use it.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
If you're not making a dual boot setup, just disregard whatever it says there about resizing and Windows.
Usually, the links to downloading an Alternate CD can be found on the same page you download LiveCDs. Scroll down the page if needed.

---

### Post by letitsnow on 2007-01-25
did you try starting in safe graphics mode?

---

### Post by thadiusdean on 2007-01-25
> **mikewhatever said:**
> May be you can try installing from an Alternate install CD. Unlike LiveCD, it has text mode installer with just four colours. See this site for howto use it.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
If you're not making a dual boot setup, just disregard whatever it says there about resizing and Windows.
Usually, the links to downloading an Alternate CD can be found on the same page you download LiveCDs. Scroll down the page if needed.
I don't mean to be picky, but what I'm looking for is some way that I can access a terminal and update/install compatible ATI drivers before I go into Ubuntu. Is that not possible?
> **letitsnow said:**
> did you try starting in safe graphics mode?
Yes I did. The same exact thing happened.

---

### Post by r4ik on 2007-01-25
Try drop into a command-line Ctrl Alt F1
Login and try,

sudo dpkg-reconfigure xserver-xorg

Go for the defaults and at the driver section choose Mesa (or Vesa cant rememeber :) )

do a  sudo /etc/init.d/gdm restart

when you got a visual you could get you're driver here

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by mykalreborn on 2007-01-25
quite weird that it didn't work in safe graphics mode. you should download dapper. i have it and i also have an ati card - really really uncompatible when it comes to 3d and such. i had to boot the live cd in safe graphics mode and it worked. also i tried edgy but it failed to load past the ending of the boot sequence. :(
and after you install ubuntu be sure to download [this]("http://ubuntuforums.org/showpost.php?p=1728869&postcount=24") script to install 3d support for your graphics card. it's sure to work 99% as it is the only way i got 3d working on my card and trust me i've tried everything.

---

### Post by thadiusdean on 2007-01-25
> **r4ik said:**
> Try drop into a command-line Ctrl Alt F1
Login and try,

sudo dpkg-reconfigure xserver-xorg

Go for the defaults and at the driver section choose Mesa (or Vesa cant rememeber :) )

do a  sudo /etc/init.d/gdm restart

when you got a visual you could get you're driver here

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !
Muy bueno, JUST what I was looking for. But uh... assume I know nothing. when do I press ctrl alt F1? How do I log in? Don't I have to create a username and password? Will the driver section thing just pop up, or do I have to go there? Maybe it'll be a bit more self explanatory once I get there. I Appreciate putting up with me. :D

---

### Post by r4ik on 2007-01-25
First try this please have to look around myself.

---

### Post by thadiusdean on 2007-01-25
> **mykalreborn said:**
> quite weird that it didn't work in safe graphics mode. you should download dapper. i have it and i also have an ati card - really really uncompatible when it comes to 3d and such. i had to boot the live cd in safe graphics mode and it worked. also i tried edgy but it failed to load past the ending of the boot sequence. :(
and after you install ubuntu be sure to download [this]("http://ubuntuforums.org/showpost.php?p=1728869&postcount=24") script to install 3d support for your graphics card. it's sure to work 99% as it is the only way i got 3d working on my card and trust me i've tried everything.
He mentions the 9200 a lot. Will my x850xt work with it?
> **r4ik said:**
> First try this please have to look around myself.
...?

EDIT: Oh... gotcha.

EDIT: I tried pressing Ctrl Alt F1 at the main boot screen... nuttin'. I guess that's the first step.

...Ya know, I think I recall a black screen with a single white cursor blinking in the top left corner of the screen after I had recieved the message. Was that the command line?

Just making sure you guys know, I haven't installed Ubuntu or anything. This is all taking place on the LiveCD.

---

### Post by mykalreborn on 2007-01-25
> He mentions the 9200 a lot. Will my x850xt work with it?

yep. it downloads the drivers for ATI graphics cards, not for 9200. i don't think there will be any problem

---

### Post by r4ik on 2007-01-25
I go with mikewhatever try the alternate cd,
I have not got a solution perhaps somebody else does, sorry.

---

### Post by thadiusdean on 2007-01-25
Alright, I'm going with the alternate CD. Wish me luck!

---

### Post by r4ik on 2007-01-25
Good luck !
Keep us informed.

---

### Post by thadiusdean on 2007-01-25
Alright, I did the alternate install, and it worked like a charm. Now I need to install those ATI drivers through the terminal. It gets to the point where the loading bar for Ubuntu finishes, then it does the same thing I had described before. I'll look around a bit and try out that Ctrl Alt F1 thing again (now that the system is actually installed!!!)

---

### Post by thadiusdean on 2007-01-25
GUESS WHO&#346; POSTIN'FROM UBUNTU! :D :D :D

Thank you so much guys.

---

### Post by mykalreborn on 2007-01-25
happy for you dude!

---

