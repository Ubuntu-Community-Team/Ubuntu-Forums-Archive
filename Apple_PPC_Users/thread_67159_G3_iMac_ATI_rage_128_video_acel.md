---
title: "G3 iMac ATI rage 128 video acel"
date: 2005-09-19
forum: Apple PPC Users
---

### Post by zxee on 2005-09-19
I have an iMac (G3 500Mhz 384MB ram) seperate partitons for OS 9 / X / Ubuntu 5.04.
I have searched and read the posts on XF86 & xorg.conf particularly this thread: [http://ubuntuforums.org/showthread.php?t=3723&page=7&pp=10](http://ubuntuforums.org/showthread.php?t=3723&page=7&pp=10) which has over seven thousand views and 67 replies.
No matter how I edit my xorg.conf If I don't have the default depth set to 24 I can't even log in (graphically) to ubuntu. 
I know these G3 iMacs are aging but mine is very functional with OS 9 & X, 10.3     It would be great to get video aceleration with these little macs as I have a hobby/small business interest in them.
The thread referred to above ends (April '05) with someone posting the exact problem I'm experiancing-is there any movement or change on this?  Thanks :)

---

### Post by DJ_Max on 2005-09-26
I have the same exact iMac, with the same video card, and haven't bothered to get video accleration working, since I don't play games, I have no need for it.

With that said, video acceleration is tricky, and even trickier with old ATI cards. The Linux and xorg drivers only seem to work when they want to.

Other than that, I can't really help.

---

### Post by zxee on 2005-09-26
[QUOTE=DJ_Max]I have the same exact iMac, with the same video card, and haven't bothered to get video accleration working, since I don't play games, I have no need for it.

With that said, video acceleration is tricky, and even trickier with old ATI cards. The Linux and xorg drivers only seem when they want to.

Other than that, I can't really help.[/QUOTE]

"...only seem when they want to." I guess that's a typo-but I don't get what you intended.
Also this isn't just a gaming issue since I can't change screen resolution either i.e. the desktop is stuck at 1024X768. No other resolution is available.
I don't know if this is the right place to say it-I have a homebuilt athlon and multi-boot several distros on it. Linux on a PC is far-far easier than getting it to work optimally on mac. :(  What I have done with the imac is run apple's X and now I have the Gimp running from OS 10.3. I'm either going to try FC4 on it or just forget about running linux on PPC. Thanks for the reply though.

---

### Post by DJ_Max on 2005-09-27
[QUOTE=zxee]"...only seem when they want to." I guess that's a typo-but I don't get what you intended.
Also this isn't just a gaming issue since I can't change screen resolution either i.e. the desktop is stuck at 1024X768. No other resolution is available.
I don't know if this is the right place to say it-I have a homebuilt athlon and multi-boot several distros on it. Linux on a PC is far-far easier than getting it to work optimally on mac. :(  What I have done with the imac is run apple's X and now I have the Gimp running from OS 10.3. I'm either going to try FC4 on it or just forget about running linux on PPC. Thanks for the reply though.[/QUOTE]
I had a late night the other day, so was half sleep in the evening. I meant they work when they want to.

I don't think the resolution problem has anything to do with video acceleration. That card max resolution is 1024x768.  I wish I knew the thread, but other people on different arch have had the same problem. I believe you can fix this in the xorg config. A quick search can reveal some answers.

Running linux on PPC(mainly Apple computers, since Apple doesn't put together hardware for Linux, unlike Pegasos) is not for the "weak". Linux on the PC is sometimes easier, unless it's AMD64. But anyway, the real problem is with you video card. I have the same issue, but it's not a problem, since 1024x768 is the best resolution the card can get, and I don't want anything lower.

Don't give up without a fight. You'll thank yourself later by what you've learned. Otherwise you're run away everytime somethings gets a little tough.

If you have any more questions, feel free to ask, and I'll try to help with the best of my ability.

---

### Post by stuporglue on 2005-09-27
To change resolutions, edit your xorg.conf again and edit the lines that say: 
                Modes           "1024x768"
Add the modes you want like this
                Modes           "1024x768" "800x600" "600x460"

Then restart X. 

The leftmost mode is the first one X will try, then the next one etc. Your screen's max is probably 1024x768 like someone said here, but if you want multiple screen sizes, or want it to auto resize for some games, you'll need those other sizes in there. 

As for acceleration, I don't know what to say, except good luck. :-)

---

### Post by zxee on 2005-09-27
[QUOTE=stuporglue]To change resolutions, edit your xorg.conf again and edit the lines that say: 
                Modes           "1024x768"
Add the modes you want like this
                Modes           "1024x768" "800x600" "600x460"

Then restart X. 

The leftmost mode is the first one X will try, then the next one etc. Your screen's max is probably 1024x768 like someone said here, but if you want multiple screen sizes, or want it to auto resize for some games, you'll need those other sizes in there. 

As for acceleration, I don't know what to say, except good luck. :-)[/QUOTE]

As I said in my 1st post-and I'm not being testy BTW It's just like others here have said running linux on a mac is a 2nd class linux user experiance-I have edited my /etc/xorg.conf file about hundred times now and yes I have the other resolutions in the correct place (display). I've even tried deleting the 1024x768 to no avail since it's still the only option I have. I'm not a linux newbie. I've actually built a new xfree86 on debian 3.0 on my athlon using only the command line. (I had changed the video card and the old xfree didn't work with it) So I can use a text editor, vi or vim and have done alot of learning on a PC. Macs on linux, on the other hand are just frustrating. :mad:

---

### Post by stuporglue on 2005-09-27
> 
As I said in my 1st post-and I'm not being testy BTW It's just like others here have said running linux on a mac is a 2nd class linux user experiance-I have edited my /etc/xorg.conf file about hundred times now and yes I have the other resolutions in the correct place (display). I've even tried deleting the 1024x768 to no avail since it's still the only option I have. I'm not a linux newbie. 

WooHoo! We used to be 3rd class! 

jk. Older Macs really do have a lot harder time with Linux. Not as many devs have them, so less work gets done to support them. 

I just mentioned the other dimensions because in most cases, that would fix it. 

Have you tried other depths? Does 2/4/8 work? 

Have you tried the new breezy installer, or added Breezy sources to your sources.list? (I know it's not stable yet, but it doesn't sound like this is in production mode yet either). There seem to have been a bunch of xorg upgrades, perhaps something fixed it. 

Depending how determined you are to get it fixed, you could try to either find Xautoconfig, or install YellowDog (then copy the xorg config and re-install Ubuntu, of course!). 

One last note, I'm not sure that that iMac has hardware acceleration. It might be the same one my dad has (2nd-ish generation?), and OpenGL doesn't work in hardware, even on Mac.

---

### Post by zxee on 2005-09-27
[QUOTE=stuporglue]WooHoo! We used to be 3rd class! 

jk. Older Macs really do have a lot harder time with Linux. Not as many devs have them, so less work gets done to support them. 

I just mentioned the other dimensions because in most cases, that would fix it. 

Have you tried other depths? Does 2/4/8 work? 

Have you tried the new breezy installer, or added Breezy sources to your sources.list? (I know it's not stable yet, but it doesn't sound like this is in production mode yet either). There seem to have been a bunch of xorg upgrades, perhaps something fixed it. 

Depending how determined you are to get it fixed, you could try to either find Xautoconfig, or install YellowDog (then copy the xorg config and re-install Ubuntu, of course!). 

One last note, I'm not sure that that iMac has hardware acceleration. It might be the same one my dad has (2nd-ish generation?), and OpenGL doesn't work in hardware, even on Mac.[/QUOTE]

 I haven't tried putting a default depth lower than 16. Not sure why 8 would work if 16 freezes the display but I'll give it a try later. I would like to be able to choose 800x600 which is what I use in OS X. I believe the slot loading iMacs had video acelleration the 400-500Mhz machines had 8MB of video ram and the 600-700Mhz had 16MB. On my imac in OS X the video is more responsive and I can play nanosaur :) I'm not on the iMac now, but earlier today I checked to see if the modules: r128, agpart, and uninorth (something like that) were loaded. They all are but no acel. I may try  FC4. I'd consider breezy if I knew that there has been change regarding these macs. Thanks!

Added 9-28-05: I'm not sure if this might help someone else (who has more time to read) but there is a DRI project [http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/) Which I found at [www.ati.com](www.ati.com)  Mostly it refers to x86 linux but perhaps some of it can apply?

---

### Post by chascon on 2005-09-28
> Depending how determined you are to get it fixed, you could try to either find Xautoconfig, or install YellowDog (then copy the xorg config and re-install Ubuntu, of course!).

Don't waste your time with ydl.  It does not have accel support for my 400mhz imac (which has a Rage 128).  In fact I think this may be normative with their distro.

As far as gnu-linux support not being good on macs.  This is imprecise.  Support is flackey on older macs, not new ones (AE excepted).  As for the issue with the Rage 128, it is not even a mac issue.  It is an ATI issue since they make the video card.  Even pc Gnu-linux users have the same issues with this video card.

---

### Post by chascon on 2005-09-29
>  One last note, I'm not sure that that iMac has hardware acceleration. It might be the same one my dad has (2nd-ish generation?), and OpenGL doesn't work in hardware, even on Mac.


Oh accel exists on a mac!!!

---

