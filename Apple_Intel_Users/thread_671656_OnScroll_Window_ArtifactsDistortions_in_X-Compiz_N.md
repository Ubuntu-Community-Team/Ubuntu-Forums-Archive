---
title: "OnScroll Window Artifacts/Distortions in X-Compiz NVidia 8600M GT"
date: 2008-01-18
forum: Apple Intel Users
---

### Post by devnater on 2008-01-18
Problem description: "artifacts" stay remenant on the screen... i.e. window contents are not redrawn correctly after something on it moves (see screenshot attached.)  happens whether manual or auto scroll.  minimize/maximize refreshes but not fix problem as it reappears as soon as another scroll event.

I have tried everything I could possibly think of or hope to have fix by upgrading or changing configurations.  Additionally, I have been searching for weeks for anyone with a similar problem with no results.

this is on a Macbook Pro 3rd Gen w/the Nvidia 8600M GT card.  Ubunutu 7.10 fully updated running compiz.

things I am pretty sure of:

- only happens when compiz-fusion / emerald effects are loaded
-> maybe related to composite extension!?

- happens with all nvidia driver versions (100.x and 169.x)

- only happens after a 4+ hours of use without any problems prior

- does not stop until I restart X (or reboot)

- maybe related to my dual monitor config?  (tried many xconf options w/no success, see xorg.conf attached)

attached is a screenshot of the prob in the Opera browser but it happens in every window except for terminals.  

Help!?!?! Thanks in advance!

---

### Post by devnater on 2008-01-21
bump... 

seriously? I am the only one having this issue!?  :( :( :(

---

### Post by MichaelSwengel on 2008-01-22
What version of the graphics driver are you running? Do you even have one installed?

---

### Post by devnater on 2008-01-28
yes - driver installed - as previously mentioned; I have installed and use the Nvidia linux drivers.  I am presently using the latest beta - 169.09.

---

### Post by davidbenson on 2008-02-17
No, you are not the only person having problems with this...  I don't know why more people aren't bitching about it...  For me, the problem started after the last xserver update that Ubuntu shoved down to my machine (do yourself a favor and turn off updates then second your machine is working)...  I had the older Nvidia driver (the one still in the repo) but have since updated to 169.09 (thank god for Envy, I don't know why Ubuntu takes soooo friggin long to update stuff).

Anyways, sorry to rant...  I'm just really getting burned out on Ubuntu...  Everyone raves about the great support but I just don't see it...  Even on my Thinkpad (which should be fairly stable), it's just a nightmare...  Suspend/Resume sucks...  Wifi sucks...  Doesn't detect CD's when you insert them...  Cant adjust the brightness...  Now Compiz is unusable and I have to refocus Firefox to repair the garbled window every time I scroll up/down (also happens in Nautilus)... WTF!

The best discussion I have found about this topic can be found here:
[http://forum.compiz-fusion.org/showthread.php?t=6742](http://forum.compiz-fusion.org/showthread.php?t=6742)

They have lots of advice...  However, I've tried all of the solutions without success...  I finally just turned off Compiz and gave up...

Good luck...


PS: Don't mean to offend the loyal folk...  I hate Windows and haven't used it for years...  Normally I wouldn't complain about stuff not working but with a mainstream distro like Ubuntu, I expect that the updates WONT break my machine - every time...  I shouldn't have to fear auto-update...  But I do...

---

### Post by cyberdork33 on 2008-02-17
> **davidbenson said:**
> No, you are not the only person having problems with this...  I don't know why more people aren't bitching about it...  For me, the problem started after the last xserver update that Ubuntu shoved down to my machine (do yourself a favor and turn off updates then second your machine is working)...  I had the older Nvidia driver (the one still in the repo) but have since updated to 169.09 (thank god for Envy, I don't know why Ubuntu takes soooo friggin long to update stuff).

Anyways, sorry to rant...  I'm just really getting burned out on Ubuntu...  Everyone raves about the great support but I just don't see it...  Even on my Thinkpad (which should be fairly stable), it's just a nightmare...  Suspend/Resume sucks...  Wifi sucks...  Doesn't detect CD's when you insert them...  Cant adjust the brightness...  Now Compiz is unusable and I have to refocus Firefox to repair the garbled window every time I scroll up/down (also happens in Nautilus)... WTF!

The best discussion I have found about this topic can be found here:
[http://forum.compiz-fusion.org/showthread.php?t=6742](http://forum.compiz-fusion.org/showthread.php?t=6742)

They have lots of advice...  However, I've tried all of the solutions without success...  I finally just turned off Compiz and gave up...

Good luck...


PS: Don't mean to offend the loyal folk...  I hate Windows and haven't used it for years...  Normally I wouldn't complain about stuff not working but with a mainstream distro like Ubuntu, I expect that the updates WONT break my machine - every time...  I shouldn't have to fear auto-update...  But I do...you don't have to download the updates. It only notifies you that updates are available, you choose to download and install them.

Secondly, if an updates breaks something that was working on your machine. REPORT A BUG. regression is a big issue and is usually looked at very quickly. Unfortunately, I don't think you are getting much "support" here, because nobody has an answer. This is the first time I have seen someone post about it, and without information about how to fix something, there is no reason to reply and just say "sorry". I understand that you are frustrated, and if you think it is bad with nvidia, try having ATI hardware.

I would love to help, but unfortunately, I don't have a clue how! This question may be better suited in a different forum (something more general, since this is the Apple Intel Support forum.

---

### Post by davidbenson on 2008-02-18
No, you're right...  I was having a bad night when I sent that post...  I didn't even notice it was the Apple forum!  Truthfully, I've never filed a bug here so I'll have to learn how...  I guess it's not fair to complain if I'm not providing feedback when something breaks...

Sorry forum...  Temporary insanity...

---

### Post by sojusnik on 2008-05-01
I also have this extremly annoying bug. It seems that it only occurs with the nvidia 8600 graphic card series. Now I am using Hardy 64-Bit version and after some time I get corrupt screens when I am scrolling. It's extremly annoying, when i turn off compiz, everything is ok. But until today I didn't find a solution for this problem.

I appreciate every advice!

---

### Post by tidewatcher on 2008-06-26
Just to throw in a fact -- the same happens on my Quadro FX 360M (rev a1). The effect is exactly the same. No, it doesn't have anything to do with the dual-headed setup, as some similar threads suggest.

---

### Post by MichalisS on 2008-07-19
It also happens on 8400M GS with latest drivers (173.14.09).

---

### Post by leech on 2008-07-23
Not that it helps terribly much, but it's happening here as well with my 9800GTX, driver version 173.14.09.  Except I'm running Debian Sid, not Ubuntu, so it's not just Ubuntu's driver / X version.

Though I didn't see the same severity as that screenshot showed, it is easy to reproduce.  In Synaptic, if you click in the middle of the app to adjust the size of the window for the descriptions of the packages, it'll leave a square around where your mouse cursor was.

Leech

---

