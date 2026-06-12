---
title: "LiveCD boot problem"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by rorschach on 2007-03-20
I hope someone can help.
I am trying to install Ubuntu on my desktop. 
When trying to boot the liveCD, xserver fails to start.
I attempted starting in safe graphics mode - again, xserver failed to start.
I attempted doing an install in text mode - after setting my partitions, the screen cleared the ansi graphics and stayed a nice shade of blue until I rebooted and removed the liveCD.

I have two pieces of hardware that may be the problem:
The CPU - AMX64 X2 - Dual Core 4400+
The Graphics Card - ATI x800

I use Ubuntu on my laptop, and I want to put it on my desktop, however, I have been hesitant due to some of the issues I've seen with 64-bit linux, but, I want to give it a go, and I trust Ubuntu.

Amusingly enough, the Sabayon Linux LiveCD boots up happily and works - but I don't know that I trust their code for my 'production' desktop.

Any suggestions on how I can get Ubuntu to at least either boot on the LiveCD or *begin* the install?

---

### Post by annda on 2007-03-20
i suppose it is the graphic card that is to blame. you can try setting the VGA option on boot (F4 i think), or hit F6 for extra boot options: for example vga=791 (for resolution=1024x768)

if that doesn't work, use the alternate cd for text install (it's not for 64bit only) - or have you already tried that?

---

### Post by Sbarton on 2007-03-20
May be worth exploring the Graphics card support for x800 in Ubuntu. I believe the ATI driver supports RedHat & Suse. It may be worth searching further. Sorry that's all I can think of.
regards

---

### Post by rorschach on 2007-03-20
I've tried the text install - it crashes after partitioning (I'm going to try it again in a few moments.)
I tried VGA booting, and it failed as well - I checked the xserver output and the error included is :
No Screens Found!

ideas?

---

### Post by rorschach on 2007-03-20
well, that didn't work - text-only install is still hanging after partitioning

kinda frustrating.

---

### Post by annda on 2007-03-20
this really is frustrating.

have you checked the cd for errors?

but i suppose the trouble is your ati x800. it looks like it requires the binary driver fglrx (which probably is included in sabayon, since it is 3d & beryl by default).
(i read here: [http://ubuntuforums.org/showthread.php?t=190133](http://ubuntuforums.org/showthread.php?t=190133) that fglrx is best, but it refers to an installed system.)

am i right that you are trying to install dapper? maybe edgy would be a better idea - it includes later kernels, drivers, etc.

if you have a spare cd-rw, you can even try out the latest feisty - just to see if the live cd works, i'm **not** recommending installing an alpha version (although i've been testing since herd 3 and had only minor bugs that have been fixed - but it's just me).

try edgy if you're not too frustated yet.

---

### Post by rorschach on 2007-03-20
:| CD tests fine. (it is edgy by the way)
I see that the beta for feisty is out day after tomorrow. I'll give it a shot... or I'll walk away for a short while.

---

### Post by rorschach on 2007-03-24
Well, I just tried the feisty fawn beta cd - no luck.
I was, for once, able to get the splash screen to load by selecting safe graphics mode, however the monitor *turns off* after a few minutes.

The scenario:
I boot into 1024x768x32
the splash screen goes through its cycle, the progress bar fills up.
The screen goes blank, and goes into power-save mode.
I hear the cd spin up again, and a short while later, I hear my speakers go *thump* like they always do when they are detected.
then
nothing...
nothing else happens.
my monitor stays off.

For reference, my system has an ATI x800 video card. I know there are issues with the drivers, and from what I've seen googling the problem, apparently a whole movement dealing with ATIs linux support at all. However, it is what I have.

Is there some way for me to get past this?
Am I *really* going to have to change video cards just to get Ubuntu to work on this system?

---

### Post by medad on 2007-03-24
Not sure how this is going to appear on your screen, but I am attaching a link that had some information about your video card.  Hopefully maybe it will help.

[http://ubuntuforums.org/showthread.php?t=190133&highlight=ATI+x800+video+card]("http://ubuntuforums.org/showthread.php?t=190133&highlight=ATI+x800+video+card")

---

### Post by rorschach on 2007-03-24
Thank you medad, that got me into the 6.10 livedvd!
Unfortunately, it didn't detect my audigy2 correctly, but, as long as I'm in the system, I can at least work on it.

For reference of anyone else that runs into this problem, the solution that worked for me was on page 5 of that link - the 8 step process posted by paulajohnw


now, I get to install and work on the audio problem (probably due to the system using my on-board sound, instead of the audigy2 it has in it.)

Thanks again!

---

