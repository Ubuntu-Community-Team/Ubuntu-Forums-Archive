---
title: "extremely frustrated"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Loki*PI on 2008-02-26
Newbie here,  I've been working with ubuntu for about three months.  I have  18 years professional computer experience - Windows and CISCO.
You guys have done a lot of amazing work with this but it is a hair ball. 
It took 2 days to get a common sound card to work, the final tweak was to turn off something that was enabled by default.
I've spent a lot of hours trying to get DVD to work.  I've followed the guilds, tweak this and that, but cannot get DVD Video to read. The hardware works, I read other formats but not DVD Video.
Everytime I lauch Ubuntu it is something different.  Sometimes the video drivers work and sometimes they don't.
Yesterday the mouse accelerator stopped working. I go into mouse and reset it, but when I close the window it defaults back to slow.
Sometimes all the windows go gray for two or three minutes and everything is locked up, then it clears and starts working. Nothing consistent, nothing that appears to trigger it, just happens.
Sometimes individual letters in various windows or applications will gray out, just random letters not entire words.
Today I launched and the desktop went crazy, I'm assuming it was the mouse driver, but folders started opening and closing, things disappeared off the desk top, tools bars are gone. New folders where created all over the place. I had to power cycle to stop it.
Now I'm back but I don't have control of the system, the tools bars are gone. Trash will not open. Alt F2 doesn't work.  I had to launch the automatic get help on line to bring up the browser.   
I"m not much of a Windows fan, but I have to say at least it works.  
So what do I do with this thing, how do I get control of it again?
I'll bring up my XP so I can read any responses.
I like this too, I"m logged in , says so at the top of the screen, but when I try to post this it tells me I"m not logged in.

---

### Post by cozmicharlie on 2008-02-26
Sorry to hear you are having so much trouble.  Hard to know where to start. Some info would be helpful.
A brief description of the computer
What version of Linux are you running (for example Ubuntu Gutsy)
How did you install it (from the live cd or ??)
Did you install any restricted drivers?

First, since you are having so many problems, start by system>preference>appearance>visual effects and click "none".  Sometimes the visual effects don't play nice.  

To be honest - if it were me, I would start all over.  Save any critical data and do a fresh install.

---

### Post by Crafty Kisses on 2008-02-26
Yeah, what are your specs?

---

### Post by JoshuaRL on 2008-02-26
I am so sorry you have been having this much trouble.  I would say from what I've seen about 50-60% of installs have no trouble, and another 20-30% only have small issues.  But we're here to help, and we really want to get you going.

Okay, now for the problems.  For the DVD support, we can walk you through that no problem.  But first we need to fix all the weirdness you've got going on.  I seriously think this is an Xorg problem.  Xorg is an application that give you the GUI that you're used to.

cozmicharlie is right.  To better help you, could you post your computer type, what version, how you installed, and video card?

But to get you a little preliminary help, go into the Recovery Mode.  It will load a bunch of stuff while the OS loads, then drop you in a terminal as root.  Something like:
```

root@yourcomputer:~$

```
Try to put in this:
```

dpkg-reconfigure -phigh xserver-xorg

```
That will try to reconfigure Xorg for your system.

---

### Post by 3rdalbum on 2008-02-26
DVD checklist:

1. Do you have the following packages installed: libdvdcss2, libdvdnav, libdvdread, libdvdplay

2. Are you using VLC to play DVDs? The Totem media player doesn't do encrypted DVDs.

---

### Post by wolfen69 on 2008-02-26
> I've spent a lot of hours trying to get DVD to work
looking through your posts, i notice you didnt ask how to get DVD working. instead of spending "hours" on your own trying to figure it out, you couldve had the answer within 10-15 min on the forums. nuff said.

---

### Post by Loki*PI on 2008-02-26
To those actually trying to help, thank you.

To answer some questions, it is an older box. I have an ATI All-in Wonder VE video card in it which may be a lot of the problem but that said it does work.  Sound card is a Sound Blaster Audigy with SB0090 chip set - that works.  3/4 gig memory.  Intel PIII.  Sorry that's all I remember, and I cannot call up the specs.

I'm at the long end of a slow link.  I downloaded at a friends, last Sept,  and put the download on CD.  Then installed it and upgraded by download.  It is Ubuntu Gutsy, with all the latest updates as of yesterday.

Tried the dpkg-reconfigure -phigh xserver-xorg in recovery but it didn't do anything. 

Alt F2 doesn't work.  I don't know how to get to a terminal or anything else.  I have desktop but cannot get to anything.  I never enabled visual effects, they were at default.   

No restricted drivers that I know of, but a lot of stuff installs and I don't really know what they all are.  I just go with the suggestions and auto updates. 

The last thing I was doing was working with the "Complete Streaming, Multimedia & Video How-to".  That was a couple days ago, and the system was stable.  Then I did some updates yesterday; auto updates.  Today it went south.

Seems like I'm looking at a rebuild.

---

### Post by JoshuaRL on 2008-02-26
Are you running the 32bit or 64bit version of Ubuntu?

---

### Post by Loki*PI on 2008-02-26
32 bit

---

### Post by xeth_delta on 2008-02-26
First of all welcome to the forums! I am sure a lot of people will be glad to help you. Just ask for help whenever you need it.

I understand that for a beginner to Linux it might be sometimes a bit difficult and the amount of information overwhelming, but please don't be discouraged. With time one learns. :) 

If you don't have any important information on your linux partition I would recommend you to start from a clean slate and then solve the problems you are facing one by one. Bring them here a the forums and we will see what they are about.

As previous users suggested, specs on the computer would be rather useful to help you. When you will have access to the terminal type:
```
sudo lshw
```
and post the output here. Please do use the CODE tags (you can place them with the help of the # button in the posting page.

Good luck!

---

### Post by JoshuaRL on 2008-02-26
Did you have errors or problems working through the Multimedia thread?  Do you remember where you were?

You could always try:
```

sudo dpkg --configure -a 
sudo apt-get install -f

```

---

### Post by asmoore82 on 2008-02-26
> **Loki*PI said:**
> Newbie here,  I've been working with ubuntu for about three months.
I have  18 years professional computer experience - Windows and CISCO.
You guys have done a lot of amazing work with this but it is a hair ball.

"Power Users" from the windows world are typically the worst off when coming to Linux.
Indeed, old habits die hard and "Tried and True," "Time-Tested" windows habits
are of no use in the Linux Realm. A Wise Man once said:
[COLOR="Red"]Windows teaches you about Windows; Linux teaches you about COMPUTERS![/COLOR]

> **Loki*PI said:**
> It took 2 days to get a common sound card to work,
the final tweak was to turn off something that was enabled by default.
This is the only part of your post that surprises me. The only think that springs to mind
is that support for ISA sound cards may have started dropping off the map.
And on second thought, if that "tweak" was disabling `esd` "software sound mixing,"
that's actually a fairly common problem for low end sound cards.

> **Loki*PI said:**
> I've spent a lot of hours trying to get DVD to work. I've followed the guilds, tweak this and that,
but cannot get DVD Video to read. The hardware works, I read other formats but not DVD Video.
This, unfortunately, is just a cold, hard fact of life for Free Software and its Users.
You require the package "libdvdcss2" which cannot be provided through official channels, despite
Fair Use Doctrine and COMMON SENSE that says you have a right to watch DVDs you have purchased.

> **Loki*PI said:**
> Everytime I lauch Ubuntu it is something different. ...
The rest of your difficulties are related to Compiz-Fusion "Desktop Effects" which is *beta* software.
The decision to include them as part of the Ubuntu distribution was not made lightly**;
but in your case I would definitely disable them:
Open "System -> Preferences -> Appearance"
Click the last Tab, "Visual Effects"
and choose the Top Option, **"None"**.

the "command" to turn off desktop effects on the fly is:
```
metacity --replace &
``` which, actually, simply runs the "eye candy"-less *window manager*, **`metacity`**.

[COLOR="Blue"]The pressing question[/COLOR] that I have for you at this time is
Have you used any 3rd Party "helper" Apps on your Ubuntu System such as Automatix or Envy??

While Envy seems to serve its purpose and work well, you should be aware that its usage
constitutes you effectively seizing control of *and taking responsibility for* your graphics drivers.
The standard Updates system will not be able to service them for you and future updates
to the Linux kernel or Xorg will cause *you* to have to fix these drivers again,
either manually or by re-running Envy.

[COLOR="Red"]Furthermore[/COLOR], Automatix is actively dangerous to your system and should never be used!

**You may wonder why compiz made it in since it seems to cause you so many problems;
the answer is that for users with a modern nVidia video card and a decent CPU,
compiz-fusion "Just Works" near flawlessly which leads to all of those jaw dropping
videos all over YouTube about it. You may think that a simple change in video card
could not make a huge difference in *stability* for compiz. But I got to see it for
myself in quite an Eye-Opening way: I *cloned* my ubuntu installation from
a laptop with Intel GMA to a desktop *with a slower CPU and 1/4 the RAM* but nVidia graphics.
I witnessed first hand as the exact same software that dissapointed on the laptop
soared to the highest heights on the desktop.

---

### Post by xeth_delta on 2008-02-26
asmoore82, nice post! I have a question, though. What where the problems you were having on your Intel GMA based laptop, other than probably some speed and lack of shaders. Compiz works actually quite well on my laptop (GMA 950 @ 1280x800). I ask because some other users have had issues with intel cards and compiz.

---

### Post by Loki*PI on 2008-02-26
Thank you asmore82 and everyone else.  

The Window comments, though understandable, are unhelpful and quite unneeded.  

As to the problem I think at this point the best solution recommended was a rebuild.  I'll get a better video card and then rebuild the system.  This venture into Ubuntu was for educational purposes so I guess I'm getting educated.

Thank you all for your help.  I'll be back around in a few days.

---

### Post by Jerry N on 2008-02-26
If you still have problems the next time you install Ubuntu you might try installing LinuxMint 4 - it might provide more compatible drivers.  

I have enough computer to use the Compiz thing.  I tried it, played with it, saw the "gee whiz" things.  Then I disabled it and never turned it on again.

Jerry

---

### Post by xeth_delta on 2008-02-26
> **Loki*PI said:**
> Thank you asmore82 and everyone else.  

The Window comments, though understandable, are unhelpful and quite unneeded.  

As to the problem I think at this point the best solution recommended was a rebuild.  I'll get a better video card and then rebuild the system.  This venture into Ubuntu was for educational purposes so I guess I'm getting educated.

Thank you all for your help.  I'll be back around in a few days.

Indeed, one can learn a lot tinkering with a Linux installation. :)
I just read in a previous post of yours that your computer has an old ATi. As far as I know, the proprietary ati drivers for older cards in linux is not exactly great. There is an open source driver in X11 that works quite well for some cards. It seems that it is not the case with your card model.

Please keep us updated.

---

### Post by asmoore82 on 2008-02-27
> **xeth_delta said:**
> asmoore82, nice post! I have a question, though. What where the problems you were having on your Intel GMA based laptop, other than probably some speed and lack of shaders. Compiz works actually quite well on my laptop (GMA 950 @ 1280x800). I ask because some other users have had issues with intel cards and compiz.

I'm not on that laptop right now, but I think it's 965GM;
It's known buggy and actually blacklisted by compiz but
I forced it to try to run anyway ;).

---

### Post by asmoore82 on 2008-02-27
> **Loki*PI said:**
> Thank you asmore82 and everyone else.  

The Window comments, though understandable, are unhelpful and quite unneeded.

No offence intended; there's nothing wrong with being fluent in both systems,
as long as you keep them totally separate. 

For example, a big "No-No" that is prevalent in Windows is the illusion of "owning"
the entire hard drive. So many "power users" feel that even in Linux they should be
able to place files anywhere for any reason especially becase it is **their** computer
but that's really just a case of being childish. I've recently figured out a great way to
explain the Linux way: What if a person whom you've never met was given the task
of backing up all of Your data from Your Linux system and for some arbitrary, external
reason that's not important, they have to do it blindfolded at light speed and never look
back. Any admin in this made-up senario would copy your home folder and nothing else!
That's why all of YOUR data should be in YOUR home folder.

[COLOR="Green"]Sorry for another tangent;[/COLOR] Welcome to GNU/Linux.

---

