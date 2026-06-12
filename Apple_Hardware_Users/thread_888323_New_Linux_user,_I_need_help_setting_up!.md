---
title: "New Linux user, I need help setting up!"
date: 2008-08-13
forum: Apple Hardware Users
---

### Post by Veovis Muad'dib on 2008-08-13
I just installed the latest Ubuntu on my Macbook Pro, along with OSX, Windows XP, Windows Vista on another drive, and rEFIt.  I'm trying to get Linux usable, but I have no idea how.

Here's what I want to do:

I want to know if it is possible to always default to starting in OSX, so that rEFIt is always started.  If that is not possible, could I get rEFIt in Linux and Windows?  I just want to always have rEFIt open first thing when I restart.  The thing that makes this difficult is that I use Startup Disk in OSX and Boot Camp's system tray icon in Windows to switch OS's.  Do I have to give that up to always start in rEFIt?

I would like my backlighting on my keys to work, even if I can't adjust the brightness at all, although manual change and ambient light sensing would be a plus.  Speaking of brightness, my brightness keys don't work either.

I would like one finger tap to left-click, two finger tap to right-click, and two finger scrolling to work, both horizontally and vertically.

Sound is very quiet in Linux compared to my other operating systems, so I'd like to get that fixed.

I'm not even going to bother getting my iSight up and running, I barely ever use it.

Also, could someone please give me a link to basic keyboard shortcuts in Ubuntu?

I'm not asking people to find all of this info for me, but if you can help with one of my problems, I would really appreciate it.  Thank you very much.

---

### Post by karlr42 on 2008-08-13
> **Veovis Muad'dib said:**
> 
Sound is very quiet in Linux compared to my other operating systems, so I'd like to get that fixed.
Try typing "alsamixer" into a terminal, then checking what volume your speakers are set at- they're probably too low. I had the same problem(though I'm not on a Mac).

---

### Post by Veovis Muad'dib on 2008-08-13
I tried that, but it didn't help. :'(  Thank you though, any kind of help is appreciated.

More info that might help:

This is the newest Macbook Pro, I just bought it a month and a half ago.

I cannot hear anything through my speakers or my headphones, but I can hear it if I use my Logitech X-540's and turn it all the way up.

---

### Post by Oscar Pradilla on 2008-08-13
Read the Macbook wiki post, is the first post of all in this forum. There's almost everything you need.

---

### Post by Veovis Muad'dib on 2008-08-13
I looked at that, but I wasn't sure if it applied to Macbook Pros as well.I guess it does, so I'll go take a look. Thank you.

---

### Post by cyberdork33 on 2008-08-13
> **Veovis Muad'dib said:**
> I just installed the latest Ubuntu on my Macbook Pro, along with OSX, Windows XP, Windows Vista on another drive, and rEFIt.  I'm trying to get Linux usable, but I have no idea how.
It would be more helpful if you identified the MacBook Pro version that you had. See the "Before you post..." link in my thread for details. Here are the MacBook Pro wiki pages though:
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)
[https://wiki.ubuntu.com/MacBookPro/Penryn](https://wiki.ubuntu.com/MacBookPro/Penryn)

> **Veovis Muad'dib said:**
> Here's what I want to do:

I want to know if it is possible to always default to starting in OSX, so that rEFIt is always started.  If that is not possible, could I get rEFIt in Linux and Windows?  I just want to always have rEFIt open first thing when I restart.  The thing that makes this difficult is that I use Startup Disk in OSX and Boot Camp's system tray icon in Windows to switch OS's.  Do I have to give that up to always start in rEFIt?
If you installed rEFIt properly, it will show on every boot, and by default, it starts OS X after a timeout period. rEFIt is not really "installed on OSX" it is an efi executable that is started from the Mac firmware directly, thus, it is not necessary to install it in "Linux and Windows". Changing the "boot disk" in OS X or Windows will defintely prevent rEFIt from starting on bootup. This is because using that utility is essentially telling the firmware, " do not boot refit, but rather boot this OS."

> **Veovis Muad'dib said:**
> I would like my backlighting on my keys to work, even if I can't adjust the brightness at all, although manual change and ambient light sensing would be a plus.  Speaking of brightness, my brightness keys don't work either. You probably need pommed. These things are covered in either the wiki page for your hardware or in the Apple Intel FAQ. Applicable Bug Reports:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125918](https://bugs.edge.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125918)
[https://bugs.edge.launchpad.net/ubuntu/+source/pommed/+bug/128786](https://bugs.edge.launchpad.net/ubuntu/+source/pommed/+bug/128786)

> **Veovis Muad'dib said:**
> I would like one finger tap to left-click, two finger tap to right-click, and two finger scrolling to work, both horizontally and vertically.
use the command 'man synaptics' and view the options that should be set there. There are also various threads in the forum on these topics. If you have one of the very latest MacBook Pros with the multitouch touchpad, then there is a new driver that you should use that enables the multitouch functions. [http://ubuntuforums.org/showthread.php?t=840040](http://ubuntuforums.org/showthread.php?t=840040)

> **Veovis Muad'dib said:**
> Sound is very quiet in Linux compared to my other operating systems, so I'd like to get that fixed. First make sure that you are following the directions in the wiki page. The low volume is apparently a bug on MacBook Pros. There is no solution as of yet. [https://bugs.edge.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125332](https://bugs.edge.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125332)

> **Veovis Muad'dib said:**
> I'm not even going to bother getting my iSight up and running, I barely ever use it.That is probably the easiest of your questions. It might "just work" try the applicaotions cheese or ekiga. If not, here is the how to, and linked in the FAQ:
[http://ubuntuforums.org/showthread.php?t=764616](http://ubuntuforums.org/showthread.php?t=764616)

---

### Post by Veovis Muad'dib on 2008-08-13
Thank you very much, I can't test it right now, since I'm on my iPod and not my computer.  However, it looks like you've solved just about every problem I have.

---

### Post by cyberdork33 on 2008-08-13
> **Veovis Muad'dib said:**
> Thank you very much, I can't test it right now, since I'm on my iPod and not my computer.  However, it looks like you've solved just about every problem I have.
I wouldn't say they will be solved, but rather you now have a lot more information on each of the issues you mention.

---

### Post by youfudoij on 2008-08-17
it is an unearthly world. There are all kinds of character. Some of them like promenade. Obtain delight in this far-flung course. Others like assault .fight the enemy. You could find interesting in slow journey.  Step by step. You also could leap in a short time by use safety powerleveling.
[www.8thgame.com](www.8thgame.com) provide safety pl. their gold is cheapeast also.
:popcorn:

---

