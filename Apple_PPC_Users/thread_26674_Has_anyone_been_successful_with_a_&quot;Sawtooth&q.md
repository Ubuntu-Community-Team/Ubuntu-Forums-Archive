---
title: "Has anyone been successful with a &quot;Sawtooth&quot; G4?"
date: 2005-04-13
forum: Apple PPC Users
---

### Post by Tofu on 2005-04-13
Has anyone managed to get Ubuntu running on a "Sawtooth" G4? These are the PowerMacs from around 1999-2000 vintage.
[CENTER][IMG]http://www.cupertino.de/data/models/g4.gif[/IMG][/CENTER] 

I had previously posted threads ([1](http://ubuntuforums.org/showthread.php?t=24043) , [2](http://ubuntuforums.org/showthread.php?t=24957)) about trouble I'd had with the monitor and CD drive.

Maybe a better approach is to ask if anyone else has actually got Ubuntu working on one of these machines. I'd like to know if anyone has succeeded.

(My machine specs: 350MHz G4, AGP, ATY 128 Pro card)

---

### Post by Rxke on 2005-04-13
This answer won't be of much use for you, I'm not running on G4, but have the older G3 in same case...

Initially I had similar problems installing Ubuntu, too, it's been awhile so i don't recall 100%, but my first tries were also half successful, like you, in that it started the install ok, then rebooted, and then the problems began, it didn't find stuff etc...

Strange thing was, when I installed in exactly the same way, but connected the box via ethernet through a hub, so I could access online repositories, it worked ok all of a sudden... DHCPed without a hitch and started downloading lots of stuff..

About your videoproblems... Yeah, probably missing driver or something, my ATY 128 does not have digital out, but even OSX reports issues with its old ROM etc... Your version is only marginally younger, so I'd guess it's a similar problem, concerning recent drivers...
IIRC, ATI only released binaries, so it's hard to impossible to write drivers for GNU/Linux ..

---

### Post by ssam on 2005-04-13
i imagine it would work. especially as you have a ati graphics card (the open source ati drivers are better than the nvidia ones).

try the live cd. in hoary there are far less differences between the live and the install cd than there were in warty. so if the live works then an install should.

sam

---

### Post by fire59 on 2005-04-13
Didn't know the name is sawtooth, but that's the machine i have.  Got kubuntu running on it.  Sound doesn't seem to work and graphic is a bit slow. Other then that it's running smooth.

---

### Post by Rxke on 2005-04-13
There's a Sawtooth and a Yikes! version of this model.
the yikes! is basically a Blue and White G3 tower (which I use,) with a G4 slapped on, the sawtooth is more optimized for G4, has some faster interfaces etc... 

so they look the same, but there's a big difference internally...

---

### Post by Tofu on 2005-04-13
Apple also calls this model the "AGP Graphics" model, as it was the first to sport the AGP port.

[ [img]http://www0.info.apple.com/images/kbase/58418/58418_2.jpg[/img]](http://docs.info.apple.com/article.html?artnum=58418)

There's a page at Apple that describes in more detail what the various G4 models were, and what they're called.
[http://docs.info.apple.com/article.html?artnum=58418](http://docs.info.apple.com/article.html?artnum=58418) 

Anyone with Ubuntu running successfully on a 'Sawtooth'/'AGP Graphics' G4? I'd like to know if it can be done, and if the install disk worked.

---

### Post by fire59 on 2005-04-14
I can confirmed that I have it installed.  My(company) G4 is exactly like that AGP.  It has the vertical sound port and ati rage 128 agp card.   I used the kubuntu iso but I imagine the ubuntu iso should work too.

---

### Post by Tofu on 2005-04-14
[QUOTE=fire59]I can confirmed that I have it installed.  My(company) G4 is exactly like that AGP.  It has the vertical sound port and ati rage 128 agp card.   I used the kubuntu iso but I imagine the ubuntu iso should work too.[/QUOTE]

Does it recognize disks placed in the CD-ROM drive?

Thanks for your replies. The fact that other people have got this working must mean I'm doing something wrong on my end  :(  I guess I'll just keep trying.

---

### Post by fire59 on 2005-04-15
Yea it recognized my kubuntu cd.  Downloaded on my IBM laptop and used k3b to burn the iso.

---

### Post by Tofu on 2005-04-15
fire59, it's good to know that you had a flawless install on the same machine.

It confirms that this machine should work fine, so I must have done something wrong. I'll follow through the specific problems on other threads.

Thanks for your responses, everyone.  :)

---

### Post by zubun on 2006-08-29
I installed Ubuntu on a Sawtooth (400mhz, 896MB) at the weekend because I was so impressed with the Live CD. Unfortunately, it ran better and faster from CD than it did as an install. I'm new to all this but after the install the system hung/froze within 15 minutes of staring up every time, and while it was running parts of the interface would disappear or not allow me to click on them. I tried to reinstall OS 10.3 on an empty partition but Mac OS won't recognise the formatting Ubuntu does so I cleaned the HD and started over. Ubuntu then wouldn't install on any of the partitions created by the Mac Disk Utility, so I'm back to OS X only! Anybody have a better result? (I had no sound or video problems while Ubuntu was running) Maybe Xubuntu is better for older macs?

---

### Post by f1sh3r on 2006-11-03
ahhhh. im having problems with my sawtooth. i was trying to install ubuntu edgy tonite, and nothing is happening. or perhaps something is happening and i cant see it.

i am attempting to install the server edition. ive tried the apple+ctrl+shift & delete. ive tried holding c. nothing is working. ahhhh. someone help me. 

ive got edgy running on my non-mac laptop. the cd is showing up in os x, but its not live cd-ing for me or whatever its supposed to do :(

---

### Post by f1sh3r on 2006-11-04
anybody? is there something else i can do to try this? 
im going to download the ISO again and burn it with a different computer. maybe its my laptops fault...

Has anyone been successful with a "Sawtooth" G4?

---

### Post by SgtT on 2006-11-05
I have had success with loading Ubuntu 5.10 on my G4.  I think that I have the same model.  A friend gave me the  motherboard, processor and video card and I put it in a pc case and modified the powersupply.  

I couldn't get my mac to work with 6.06 or 6.10, I have an issue with the xserver and was tired of playing around with it.

I like Ubuntu better than OSX (not trying to flame OSX), OSX was really slow on my system and Ubuntu 5.10 runs better.

I have a G4 with a Rage 128 video card, I think I have 1GIG worth of memory.  I really didn't have a hard time with 5.10.  When I have more time I may try 6.10.

---

