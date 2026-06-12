---
title: "Firefox crashing in Feisty"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by JJFO on 2007-04-21
The upgrade went well and everythings fine, except now firefox usually crashes when i hit the back button on a page with a video. Its really annoying when I'm trying to watch porn or looking at reddit. Anyone know how i can fix this? Thanks.

---

### Post by zerosystem on 2007-04-21
You're quite honest, you know that?

You might want to try reinstalling totem and the gstreamer packages. At the moment, I can't remember what the gstreamer packages are named, but I think if you do a "sudo apt-get remove totem" and the a "sudo apt-get install totem" all of the packages will be reinstalled for you.

---

### Post by JJFO on 2007-04-24
I tried reinstalling totem and firefox as well, Im not sure how to reinstall gstreamer, in synaptic theres a slew of gstreamer packages and Im not sure which ones to reinstall.

---

### Post by JJFO on 2007-05-04
Sorry to bump this but Im having the same problem. Anyone have a clue about whats wrong
?

---

### Post by jarvis13 on 2007-05-08
Same exact problem. Very annoying. Any fixes?

---

### Post by Sparky Jim on 2007-05-08
Hi fella, this may not be the answer your looking for, but I installed Ubuntu 7.04 today and I am a total nooby, however i had a similar issue with Firefox, and it was the same reason I dumped it under Windows. One solution would be to migrate over to Opera, a lovely free browser that I think is far better than Firefox and once you install Java etc it works fine with video etc..

I would add one note of caution..if your going to porn sites, it could equally be the low grade datastreams they use that is the problem in your case.

---

### Post by HeyItsMatt on 2007-05-08
> **Sparky Jim said:**
> Hi fella, this may not be the answer your looking for, but I installed Ubuntu 7.04 today and I am a total nooby, however i had a similar issue with Firefox, and it was the same reason I dumped it under Windows. One solution would be to migrate over to Opera, a lovely free browser that I think is far better than Firefox and once you install Java etc it works fine with video etc..

I would add one note of caution..if your going to porn sites, it could equally be the low grade datastreams they use that is the problem in your case.

I might also have to suggest Opera.  I don't have a problem with video-related crashes, but Firefox does seem really antsy to me - it will often crash if I have too many tabs open or if I am making it work extra hard loading things.  I still use Firefox simply because I keep adding bookmarks and I'm too lazy to move them over, and the crash isn't frequent enough to be a huge pain.  However, from what I've seen, Opera's actually a lot faster than Firefox.

If you don't want to lose Firefox, perhaps you can try uninstalling it and installing the version provided on the Firefox website itself?  I remember seeing some threads in the past about people having problems with Firefox that were fixed by getting the version from the site, rather than the pre-installed version in Ubuntu.  Of course you can also see if it's an embedded video problem by switching Firefoxes default video player (it's totem in Ubuntu I think, you just get rid of the totem plugins in the Firefox plugin directory and replace them with mplayer or some other plugin).

---

### Post by kc0eks on 2007-05-08
firefox seems to be very sensitive to certain sites java or scripting in general, so I would imagine its something related to the site speciffically and firefox. You can always try noscript or adblock and block out the scripts and see if that helps...
But firefox does seem to crash fairly often lately for me as well, though not on any specific sites. 

I too have considered Opera several times, but I just love my extensions too much.

---

### Post by jubxie on 2007-05-08
I'm at my wits end with firefox. It was crashing in dapper, so i installed feisty. It crashed there, so I installed xubuntu feisty. Needless to say, it is still crashing. On the latest install, I didn't add anything to firefox. No plugins, no themes, no extentions, nothing but bookmarks.  I've run memtest overnight with no errors and I even payed $90 for spinrite to test the hard drives. No problems. My system is x2 4200, 1GB, NV, bla bla.

```
Segmentation fault (core dumped)
``` is what I get and I must reboot to open firefox again. Safe mode does not work once firefox has crashed. I'm using opera now (cause I don't want to reboot), but I really like firefox better. Azureus was also crashing constantly unitl I switched to ktorrent. Could these be related? No other program seems to be an issue. Sorry for the rant.

---

### Post by greenstar on 2007-05-16
I just confirmed a similar problem with other browsers on feisty. Same problem occurs when I install & use epiphany browser from the repos.

I also tested using a site that has java, not flash and both firefox & epiphany crashed there also.


Greenstar

Edit: Just noticed that epiphany is built upon firefox... Doh!!

---

