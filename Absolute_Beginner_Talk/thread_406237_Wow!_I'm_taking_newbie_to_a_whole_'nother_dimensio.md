---
title: "Wow! I'm taking newbie to a whole 'nother dimension!"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by jimmj43 on 2007-04-10
I'm a newbie, not only to this forum, but to Linux as well. I've browsed through a number of threads and found 1 or 2 that closely relate to problems I'm encountering, but when I look for a place to contribute to the thread I find no "add a comment" or "start a new thread" buttons.
What am I missing? (Stating the obvious: 'a few brain cells', doesn't count.)

For the record, I'm trying to do a clean install of Ubuntu on a Compaq Presario, 900Mhz, 256M, 30G that I just reformatted. This is a (presumed good & tested-via-install-options) disk that was mailed to me from Ubuntu a couple of months ago.

I should add that the machine I'm dealing with has a replacement video card, installed before the reformat. 

During the normal(?) install progress screen, one element fails to get an "OK": Starting PCMCIA (<--or something very similar to that). Than a DOS-looking screen appears, quickly scrolls up too far to read it all and is partially overwritted by verbiage from another planet. It asks if I want some manner of "X" something to do something or other. 'Yes" is highlighted. If I hit 'Enter' nothing happens. If I hit -> to highlight "No" and hit 'Enter', nothing happens.

Can someone clip a leash onto this ring in my nose and lead the way, please?

Thanks.

---

### Post by halitech on 2007-04-10
far as PCMCIA failing, no big deal unless you have a laptop then it could be a problem.

Are you installing from the LiveCD? Personally I've never had much luck with installing from there, great for trying but not so good for installing (YMMV) so if you are sure y ou want Ubuntu, grab a copy of the Alt Install CD, download and burn that and it will just install with no fancy graphics

---

### Post by kevmartin on 2007-04-10
I won't try to help on the actual issue - no idea here I'm afraid - I'm a newbie too.  But on the 'how to reply' point, you should see a 'Post Reply' button directly above the name of the previous posters, as well as directly below it, but after the content of the post, kind of like this:

"Post Reply"

7 Minutes Ago
jimmj43
First Cup of Ubuntu
----------------------------------------------------------------
Post contents here ... Post contents here ... Post contents here ... Post contents here ... Post contents here ... Post contents here ... Post contents here ... Post contents here ... Post contents here ... Post contents here ... Post contents here ... Post contents here ... Post contents here ... Post contents here ... Post contents here ... Post contents here ... Post contents here ... 
----------------------------------------------------------------
"Post Reply"


Hope that helps :-)

---

### Post by Iceni on 2007-04-10
> **jimmj43 said:**
> I'm a newbie, not only to this forum, but to Linux as well. I've browsed through a number of threads and found 1 or 2 that closely relate to problems I'm encountering, but when I look for a place to contribute to the thread I find no "add a comment" or "start a new thread" buttons.
What am I missing? (Stating the obvious: 'a few brain cells', doesn't count.)

For the record, I'm trying to do a clean install of Ubunto on a Compaq Presario, 900Mhz, 256M, 30G that I just reformatted. This is a (presumed good & tested-via-install-options) disk that was mailed to me from Ubuntu a couple of months ago.

I should add that the machine I'm dealing with has a replacement video card, installed before the reformat. 

During the normal(?) install progress screen, one element fails to get an "OK": Starting PCMCIA (<--or something very similar to that). Than a DOS-looking screen appears, quickly scrolls up too far to read it all and is partially overwritted by verbiage from another planet. It asks if I want some manner of "X" something to do something or other. 'Yes" is highlighted. If I hit 'Enter' nothing happens. If I hit -> to highlight "No" and hit 'Enter', nothing happens.

Can someone clip a leash onto this ring in my nose and lead the way, please?

Thanks.

As far as I understand you are still in the "dos-looking window" when it asks you about X. Just type y (for yes) or n (for no) and then press enter :)

X is - easy (and partially uncorrectly) said - your "linux windows"  - the window interface you probably want to use.

---

### Post by halitech on 2007-04-10
I think the problem Iceni, is that no matter what he does, it doesn't respond so to tell him to select yes or no, really doesn't help much

---

### Post by dstew on 2007-04-10
I have an old Presario, and every time it boots it puts up the Starting PCMCIA message, which always fails, because it has no PCMCIA slot. It just goes on booting after the "failure" and it works fine. I don't know why the installer put in the PCMCIA module, but it doesn't ever cause any problems. Just try to skip the error or ignore it.

---

### Post by jimmj43 on 2007-04-11
Halitech is correct. When faced with that display with the "Yes" already highlighted, hitting 'Enter' accomplishes nothing. Likewise, if I --> to highlight the "No" option and hit 'Enter', nothing happens.

This is a desktop system. For the record, I can load a D/L'd & burned copy of Linux Puppy and go merrily surfing my brains out - running from the disk. I haven't, nor do I have any INTENTIONS of INSTALLING Puppy, even though it is pretty nifty.

During install how does one go about "skipping" or "ignoring" the error in order to continue?

Sidenote question: When I got the hand-me-down Compaq I installed W98se, followed by, among other things, [BelarcAdvisor]("http://www.belarc.com/free_download.html") so I could print out a hard copy of all the hardware & software the machine has. However, since reformatting, Belarc is toast and I have no clue what video card I plugged in (after the reformat). It ***seems*** to be a continuing theme with Ubuntu that video cards and their drivers can be problematic. Should I focus attention on that issue? Am I gonna hafta re-install W98se so I can reinstall Belarc just to find out what I have in the way of a video card before I can progress?

As a newbie I can't reject out of hand the notion that an online D/L "alternative" disk might behave better than one produced by the guys who are responsible for creating the OS, but I only need to think for a moment about Gates and it kinda-sorta makes sense (in a demented kind of way).

That said, the [factory] disk that I have indicated while it's loading that it is V2.6.16, while the disk itself is imprinted with 6.06LTS. I ALSO have a disk I D/L'd & burned that is (I think) a version of Feisty which gives me exactly the same results! 

At present there's a screen that says:

Failed to start your X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? "Yes"(highlighted), "No".

If I hit the "y" key, nothing happens.
If I hit the --> key, "No" becomes highlighted, and if I then hit 'Enter', nothing happens.
If, when the "Yes" is highlighted I hit 'Enter', I get ....... ACK!!

Something entirely foriegn!!

And NEW!

I get:

X window system version 7.1.1
Release date 12 May 2006
X protocol version 11, revision 0, Release 7.1.1
Build operating system: Linux 2.6.15.7 i686
Current operating system: Linux ubuntu 2.6.17-10 generic #2 SMP Fri Oct 13 18:35:45 UTC 2006 SMP
Build date: 07 july 2006
     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure you have the latest        
     version.
Module loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) Informational, (WW) Warning, (EE) Error, (NI) Not implemented, ( ??) Unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 11 02:50:51 2007
(==) using config file: "/etc/x11/xorg.conf"

And at the bottom center of this BRAND NEW PAGE is the word, "OK".

1st I'll hit the "o" key, with ZERO expectation of anything happening. Assuming I'm correct, I'll then pounce on the 'Enter' key.

hmmmm.......

As predicted, hitting the "o' key got me nothing.
However, hitting 'Enter' got me a couple more lines of text:

(EE) s3(0): Ramdac probe failed
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error


?? Huh? I don't own a server and wouldn't know one if it was gnawing on my ankle!

I should add that the ^foregoing^ happened with the D/L'd disk I burned myself. Whatizzit anyway? Edgy? Feisty? Google?

Gonna try it again and select the "no" option if ^that^ window comes up again. One o' you guys got a light?

Egad! Don't tell me I need a boot floppy!

OK, I --> and highlighted "No", then hit 'Enter' and was presented with:

The X server is now disabled. Restart GDM when it is configured correctly.
                                       OK

umm.... What's a GDM? And how does one go about correctly configuring one? 

Just hitting 'Enter' got me a blank/black screen with nothing but a blinking cursor at the top left.

It's after 3AM(central)  here, so I'll ask a final question: Is there a better time of day to get fairly quick responses to inquiries? If so, what's the window? 

Thanks.

---

### Post by tommcd on 2007-04-11
When the grub menu comes up choose "recovery mode". This will give you a terminal. If ubuntu is the only OS, and you don't see the grub menu hit esc to see it.
Then run <sudo dpkg-reconfigure xserver-xorg> (without the <>, of course).
Answer defaults to all if you don't know them. This will get your GUI up and running.

---

### Post by igknighted on 2007-04-11
Ok, the "X server" is just a fancy name for the framework that all the GUI components run on.  If the X server (or X or X.org) don't load, all you get is "dos" (shell).  As for how to fix it, try typing this command after you get dropped to the shell:
```
sudo dpkg-reconfigure xserver-xorg
```
It will as you a bunch of questions, try accepting all the defaults and seeing if that works.  After it is done, type this command:
```
startx
```
and hopefully the GUI loads.  If it errors out again, try the first command again, but choose "vesa" as the driver, and pick defaults for the rest (just keep hitting enter basically).  Then try startx again and see if it works.

Hopefully this will work.  It is also possible that you are getting this error due to a bad burn, so if this doesn't work I'd check the md5sums and burn again at a slow speed (like 4x).

Other odds and ends:
GDM=Gnome Display Manager... for now lets just call it the login screen, though it does more
X server=Program that handles all windows and other GUIs
Best time to post=WHENEVER!!  Lol, actually, it seems the busiest times are evening and mid day (many seem to post from work)... times are EDT, so you'd be one hour off me.

---

### Post by cantormath on 2007-04-11
great title......:lolflag:

---

### Post by jimmj43 on 2007-04-11
After almost 6 hrs of sleep and 1st cup of coffee, I'm ready to bash in my head some more.

I tried igknighted's instructions and made some progress - I think. It was late and my eyes were nearly crossed when I ran the reconfigure thingy - for the third time running! I didn't realize where the end was so just kept going again and again. Gah! 

Anyway, I managed to get the 1st command line running:
sudo dpkg-reconfigure xserver-xorg

But when I typed: startx, and hit 'Enter'.........nothing.

THEN it became a question of "vesa" as a driver. hmmmmm..........
I'd remembered seeing "vesa" as an option for some manner of graphics/video (I think) option-select screen, so I went back through and when I got to the screen shifted from the default over to "vesa" and continued. To no avail.

I even tried to insert "vesa" into ^that^ command line in place of the 2 other 4-character strings: "dpkg" changed to "vesa", and "xorg" changed to "vesa".
No joy.

I have another request: Assume I'm the dumbass I am. To me, a "grub" is a particularly effective live bait used for catching bluegills, and a shell is what an egg comes in.

One more possibly useful chunk of info: The video card is a Diamond Stealth 64. I did some searching trying to find drivers for it. I learned that there are LOTS of folks who DON'T LIKE Diamond products A LOT!! The absence for a source of drivers is high on their list of dislikes.
Wunnerful!

Now I'm wondering if I should put this on a back burner until Feisty hits the ethers.

Thanks guys.

---

