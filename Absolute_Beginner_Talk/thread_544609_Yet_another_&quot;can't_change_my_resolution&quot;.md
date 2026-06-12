---
title: "Yet another &quot;can't change my resolution&quot; thread"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by SWEn0thing on 2007-09-06
**Edit: Wow... this post got pretty long. Anyway, the point of it for those who can't be arsed to read the whole thing: I can't change my resolution to 1280x800, and I've tried loads of things. I'm attaching my (default) xorg.conf file (changed the file extension to txt so I could attach it), and I'd be eternally grateful if anyone would edit it to suit my needs and upload it. System specs and other info below.**

I know, I know, this must've been done to death. I've read thread after thread, tried time after time but I still can't set the screen resolution to 1280x800. In some cases I simply didn't understand what to do, in other cases I did, but to no avail: either it didn't change anything, or the xserver couldn't boot.

Okay, first some hardware specs. It's a IBM ThinkPad laptop with a Intel Core Duo T2300 CPU and a ATi Mobility X1400 graphics card. The screen is, I don't know, maybe 15 inches or something like that? Anyway, the native resolution is 1280x800. 

This is what I've tried: run the xserver xorg configuration from the terminal, edited the xorg.conf file manually, for example: added the resolutions to all the "Modes" lines in Section "Screen", added some kind of resolution thing to Section "Monitor", made some kind of generated Modes line for Section "Monitor" and all possible combinations of those. Either I'm doing it wrong, or I can't simply do it.

So... I'm totally new to Linux and don't really have any idea what I'm doing. So now I'm back to default, and I'm attaching the default xorg.conf file (changed the file extension to txt so I could attach it). What I'd really appreciate is if someone would edit this in the correct way and upload it for me to download. Please no "Well, you could add this line there and there", I really don't wanna fail this time. ;-)

Thanks!

---

### Post by jingo811 on 2007-09-06
I'm bad at Xorg editing but pretty good at generalizing so check out Chapter 6 in my notes and see if that will work for you
[http://virtualseafarer.com/renaissance/allsparks/chapter6.html#ch6](http://virtualseafarer.com/renaissance/allsparks/chapter6.html#ch6)

---

### Post by SWEn0thing on 2007-09-06
> **jingo811 said:**
> I'm bad at Xorg editing but pretty good at generalizing so check out Chapter 6 in my notes and see if that will work for you
[http://virtualseafarer.com/renaissance/allsparks/chapter6.html#ch6](http://virtualseafarer.com/renaissance/allsparks/chapter6.html#ch6)

I've tried that before (but without the -phigh, any difference?), but I have a couple of questions. First of, there are two parts in that configurator where you can choose your resolution. First of, where you choose your prefered resolution (I think?) where there's loads of options, even more unusual ones like 1280x768, and then there's the part where you choose a maximum resolution. I think mine was set to 1024x768,  but there were no 1280x800 option. Why, and what should I set it to?

---

### Post by mpower on 2007-09-06
I'm having the same problem....been through the whole process but still only get the 3 options for resolution - 1024 x 768 being the max. Even though on the xorg.conf file it lists the 1440 x 900 that I've entered.

---

### Post by SWEn0thing on 2007-09-06
Oh, now I'm feeling kind of embarrassed. It was way easier than I thought. When I ran sudo dpkg-reconfigure -phigh xserver-xorg, I just highlighted the resolution (1280x800) and pressed enter to accept the choice. Didn't understand that you had to mark it with the spacebar to choose it. :) Then I just restarted the xserver and chose 1280x800 in Screen Resolution under System--->Preferences.

Tack för hjälpen, jingo!

---

### Post by mpower on 2007-09-06
Well....I've done the whole damn thing again AND edited the refresh rates and STILL get sod all.

I think maybe I'll dig out the XP disk I still have somewhere. Anything's got to be better than going through this amount of trouble to get the bloody resolution right.

---

### Post by SWEn0thing on 2007-09-06
> **mpower said:**
> Well....I've done the whole damn thing again AND edited the refresh rates and STILL get sod all.

I think maybe I'll dig out the XP disk I still have somewhere. Anything's got to be better than going through this amount of trouble to get the bloody resolution right.

Yeah. I still have no idea why they have to make it so complicated. Ubuntu is marketed as a user-friendly OS, right? One might think that it has to be possible to change the resolution without editing system files manually or running weird terminal commands. 

Well, it's free so fair enough. After all, it seems like a great OS after all the configuration. :)

---

### Post by rustybronco on 2007-09-06
I don't use or haven't used your version of an ati card BUT with my old radeon 7000ve  I set the driver to "ati" then in a terminal
```
 sudo gtf 1280 800 60 
``` 
```
 cut-n-paste the output of what you get into /ect/X11/xorg.conf at the end of the monitor section > save and exit  
``` 
Restart (ctrl+alt+backspace)

BEFORE YOU DO THIS READ UP TO SEE IF IT WILL WORK FOR YOUR CARD! (search)
or just go ahead and try to crash X, then sudo dpkg-reconfigure...

By the way everyone complained (almost)  about how hard it is to set up an ati card with 3d effects and I did it on a widescreen monitor with the ati drivers supplied in 7.04 I guess it's what you consider hard.
I consider it learning...

---

### Post by jingo811 on 2007-09-07
> Well....I've done the whole damn thing again AND edited the refresh rates and STILL get sod all.

I think maybe I'll dig out the XP disk I still have somewhere. Anything's got to be better than going through this amount of trouble to get the bloody resolution right.

You mean you followed the whole damn thing from my link or else where?
[http://virtualseafarer.com/renaissance/allsparks/chapter6.html#ch6](http://virtualseafarer.com/renaissance/allsparks/chapter6.html#ch6)

---

