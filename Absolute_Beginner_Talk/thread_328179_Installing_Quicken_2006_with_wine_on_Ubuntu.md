---
title: "Installing Quicken 2006 with wine on Ubuntu"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by M8M on 2006-12-30
Hi guys and gals,

For starters, I'm an absolute beginner. I've taught myself ALOT of stuff about installing in the last few weeks, but to be honest I can follow instructions more than actually understand what I'm doing. (I'm a bit of a slow learner...)

I REALLY need to install Quicken into my Ubuntu, b/c I just lost all of the last year's transactions (not good) in WIndows and since I'm going to have to start over, I might as well, start in Ubuntu. I already tried the Linux options for money management, but none do what I need them to do. The closest one is Money Dance, but it doesn't allow me to see upcoming transactions on a calendar like Quicken does. This is critical to me. 

Since I already have wine on my ubuntu for another program and I have a few more that I want to transfer over using wine as well, I might as well add Quicken and end my search for now. SO:

I need some help as I try to install Quicken with wine, it starts ok but then I get the following error:

An error (-5006: 0x8000fff) has occured while running the setup.

Then it shuts down. Can someone give me in lay man's terms the step by step instructions to fixing this? Pretty please?

M8M

---

### Post by shanepardue on 2006-12-30
I don't think quicken 2006 works with wine. you may want to google crossover office for such a task. it's easy to use and the beta is free for at least 60 days to see if it works.

---

### Post by M8M on 2006-12-30
Don´t ask me how, but I did get it installed. It just needs to be tweaked as there are some little flickerings that I´ve read about elsewhere. If I coudl just find where......

---

### Post by shanepardue on 2006-12-30
Well, cool! Unfortunately I don't know those special tweaks, but if you haven't already..check out [www.winehq.com](www.winehq.com)

---

### Post by rbhigday on 2007-01-05
I am attempting to install the home and business version and was wondering if you installation required a gecko browser installation and how you got that to work if it did?

I also have the flickering that you do as well :)

---

### Post by M8M on 2007-01-05
Yes, mine requires the installation of gecko and I too have not figured that out yet (mostly b/c I haven´t worked on it in a few days). I a little frustrated with having tried to load the Christian environlment and now I can´t use Firefox. Mozzilla web browser works for surfing the net, but it doesn´t recognize things like PDF files or know what program to use to access them. I´m REALLY busy trying to get school going for my kids again, and don´t have anymroe time to spend on the computer. I´m just waiting for Jereme to get back from vacation and ask him to custom set up everything for me, b/c I don´t have anymore time to waste trying to figure this all out. If I  learn something, I´ll post.

M8M

---

### Post by M8M on 2007-01-05
Oh, I forgot, I´ve been told that installing the gecko thingy must be IN WINE, not in unbuntu. (I don´t know if that helps you or not).

To turn off the flickering thing, you must go to winecfg (in terminal) then go to graphics and unclick something that has to do with allowing windows to manage windows. The only problem with that is that when you do so it automatically opens in full screen and one cannot click on the mini gecko window that supoosedly is behind the Quicken screen and you need to accept the download to install gecko......

I hope that helps. That´s where I stopped....

M8M

---

### Post by scohar70 on 2007-05-08
I have installed Quicken 2006 with Crossover, and it appears to work... to a point.  The tool comes up nicely, and for the first 90 seconds, I can navigate around my quicken data, but then, Quicken throws up a popup which appears to be one of those "Welcome to Quicken Tool Tip" type popups, and that popup hangs Quicken.  Anybody know what this is, and how to disable it?

Thanks,
Scott

---

### Post by Das Goat on 2007-05-12
Well, that is more than i have been able to do. Can you post the EXACT steps to took to get Quicken 2006 to work?

---

### Post by scohar70 on 2007-05-13
> **Das Goat said:**
> Well, that is more than i have been able to do. Can you post the EXACT steps to took to get Quicken 2006 to work?

Here's exactly what I've done:

[LIST=1]
[*]I installed Crossover 6.0.1 from their website installation instructions.  ([http://codeweavers.com](http://codeweavers.com))
[*]I then installed using the "Quicken" (not Quicken 2007) option in Crossover, using my Quicken 2006 Premier CD.  This went into a "Win98" bottle.
[*]Then, I installed IE 6 (from Crossover menu).  I verified that IE works.  (I hate having it on my Linux system, but Quicken needs it. 
[*]Finally, just to be safe, but it doesn't seem to help, I installed Flash and Shockwave from the Crossover menu.
[/LIST]

So, it still doesn't work for me.  I mean the QUICKEN application totally works:  I can even download my latest data, save files, print, change settings, etc., but the first instant I enter the check register, the "Welcome to Quicken" dialog pops up.  In debugging this on my Windows machine, it looks like this is a Shockwave application (ashxxxx process names in windows).  But this dialog box crashes Quicken and the process has to be killed.

So, for now, I am running Quicken on my last remaining Windows machine.  I sure am close to getting it working on Ubuntu; I hate to give up after getting so close.

---

### Post by joe056 on 2007-05-21
Hi schohar - 

Your bug is not unique.  The exact same thing happens to me.  Installation ran fine.  IE6 works fine.   Quicken 2006 opens up fine, but as soon as the check register opens, the program hangs for about a minute, and then closes itself without any error message.

As far as details that I used to get quicken to "work" in the first place:

1) Install Automatix with the appropriate .deb package from [www.getautomatix.com](www.getautomatix.com)
2) Install Crossover Office Standard Demo from Automatix program.
3) Insert Quicken 2006 CD and open Crossover's "Install Windows Programs" program.
4) Install Quicken 2006 using the onscreen instructions into the Windows 98 bottle.  Make sure to be patient, because it's slow.
5) Eagerly await the imminent crash we've discussed.

---

### Post by noMScraig on 2007-05-21
You might consider moving to the online edition and using the ie program to access with active x controls.  I switched my quickbooks and it is working great.

MIght not be the best work-around but it might work.

-c

---

### Post by Das Goat on 2007-06-12
The online edition huh? I am a little dubious putting all that information on line like that.

---

### Post by scohar70 on 2007-06-12
For what it's worth, I had a little more success with Quicken 2007 Premier than I did with Quicken 2006.  

All of that is documented on the CodeWeavers forum here:

[http://www.codeweavers.com/compatibility/browse/name/?app_id=2634;forum=1;msg=5622](http://www.codeweavers.com/compatibility/browse/name/?app_id=2634;forum=1;msg=5622)

But the short of it is that I can get the basic functionality of Quicken working in 2007, with all the fonts and things working properly, but the stupid IE won't talk to the stupid Quicken, and so I can't do online updates, which is a deal breaker for me.

So, for the time being, I'm still Quickening on the old XP machine I have.  :-(

---

### Post by Das Goat on 2007-06-24
Hi folks,

Ok, I am sure this is not the answer you all were hoping for, but it is an answer!

Go to this thread: [http://ubuntuforums.org/showthread.php?t=340113&page=13](http://ubuntuforums.org/showthread.php?t=340113&page=13)

Follow the instructions. 

I currently have a native Ubuntu system, with Windows XP running in a virtual Box, and in the virtual box, Quicken runs FLAWLESSLY. I updated on line, backed up my files. Everything!

:popcorn:

---

