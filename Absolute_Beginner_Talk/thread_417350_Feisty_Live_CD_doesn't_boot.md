---
title: "Feisty Live CD doesn't boot"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Kamigawa on 2007-04-21
Hi!
I used the 6.1 (was this the Feisty Beta?) Live CD for some days now, to test he OS prior to install it really. Today I loaded 7.04 (Feisty) and burned it. When I reboot my PC it loads the main menu, where I can choose the option "Start or Install Ubuntu". If I klick this the Loading Kernel window will appear, proceed to 100% and then will stop. Nothing more is gonna happen. I just can see the Microsoft Windows like Loading Kernel window with a 100% progress bar and that's it. Wit 6.1 I had no problems. There Ubuntu would've started now, but not with 7.04.
Could it be that an other kernel is used, that doesn't support my hardware?
And am I able to fix this?
Thanks in advance!

PS: I'm very sure that the CD itself is not the reason, because I downloaded Ubuntu three times from different mirrors and burned it low-speed.

---

### Post by oilchangeguy on 2007-04-21
if there's no special reason why you need to upgrade, then don't. if 6.10 was working fine why change? look at all of the posts in the last few days from people having trouble with 7.04. i'm going to stay with 6.06lts until the next lts version comes out in 2009.

---

### Post by Kamigawa on 2007-04-21
I also thought of this possibility. And I think that I'll really use 6.1 instead of 7.04.
Do you think that the next LTS version won't have problems like this? I thought that LTS Versions just have Long-Term support, but not that they are "better" or let's say "more stable" than non LTS versions.

---

### Post by bobplano on 2007-04-21
well they are supported longer so they end up becoming more stable. also there are not so much cutting edge features so people who want a stable system for something like servers or just want stability instead of upgrading 2 times a year can use them and have a stable system

---

### Post by oilchangeguy on 2007-04-21
i'm sure others will disagree with me. however lts versions are what you want to use. they should have the least amount of problems, compaired to the non lts versions.

---

### Post by Kamigawa on 2007-04-21
I recognized that the version that worked properly for me isn't a LTS version.
It's, like I said, the 7.04 Beta, but I haven't got problems with it and it's the only version with which I can connect to a WPA2 encrypted WLAN (for sure it's also possible with other versions, but not approximately as easy as with this one).
Do you think I can use this non LTS version unworried or would you advise me to use 6.06?
And if you say 6.06, can you say me how to connect to a WPA2 WLAN?

---

### Post by medad on 2007-04-21
I'm just surprised that 7.04 didn't load correctly for you.  I had dapper on my primary computer until the feisty beta came out.  Dapper was really stable and if you want stability then it is definitely for you.  I moved on to Feisty and so far it has done pretty well.  I have it loaded on two different systems currently.

---

### Post by Zillion on 2007-04-21
Try adding IRQPOLL, on bootmenu press E and behind the 1st long line add IRQPOLL. I needed to do that too, after that it booted fine.

---

### Post by bobplano on 2007-04-21
ubuntu edgy 6.10 has been out for a while but it will still be supported for about a year more so it should be stable. the point with the Lts version was they were made to be more stable than most regular computer users need, but they are perfect for servers.

---

### Post by Kamigawa on 2007-04-21
@Zillion: I have to say that I'm still a Noob and don't know if I've done it right. In the main menu I pressed F6 (Other Boot Options). There was a line wit "[...]splash quiet -- " and I wrote "[...]splash quiet -- IRQPOLL", but it didn't changed something. When the Kernel Loading progress bar reaches the 100% the CD will stop spinning and nothing more will happen.

At least the 7.04 Beta works fine *g*

---

### Post by Zillion on 2007-04-21
Hmm that worked for me... I only know if u remove SPLASH u can see on what it hangs. Good luck!

---

### Post by Kamigawa on 2007-04-22
When I remove the splash it's all the same, because I don't reach the splash screen at all.
Also if I boot in save graphics mode it isn't working.

---

### Post by soul_motor on 2007-04-22
I was having a similar problem with mine.  I'd hit start or install, kernel loaded, then the lines started and then hung at random spots, mostly telling me to die.  I went into windows for other reasons, then I hit restart.  It's working better now, it's running through the lines as I write (i'm on my laptop).  Quick question for everyone, how many lines are there to run before Ubuntu even pops up?  It's been like an hour and it's on line 4407.xxxxxx...  Thanks in advance.

---

### Post by zorkerz on 2007-04-22
IF you want to verify that your feisty cd is uncorrupted first md5sum the iso. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Then when you boot the cd there is an option to check the cd.  If both of these test pass then you should have a good cd and be able to look somewhere else for the problem.  

I am having a similar but probably unrelated problem with the feisty live cd. The cd boots fine i even suspect gnome loads fine (i hear the startup sounds). However, i get a blank screen. 

Good luck

---

