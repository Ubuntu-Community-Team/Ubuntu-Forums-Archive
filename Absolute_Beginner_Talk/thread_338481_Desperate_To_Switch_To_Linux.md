---
title: "Desperate To Switch To Linux"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Leonaken on 2007-01-14
Whether this is a rant or a desperate plea for help is in the eye of the reader here. I've wanted to switch over to Linux for some time now but have had several things holding me back. Now I'm pretty [desperate](http://www.heise.de/tp/r4/artikel/5/5263/1.html), not that I have anything to hide.

Despite my strong will to ditch proprietary source and go open, there are things I feel I can't live without that I know Linux can offer but isn't keen on giving to me right off the bat.


**Dual-Monitor Support**

Two heads are better than one, to beat a dead cliche'd horse. I have two monitors and I've grown to feel debilitated without an extended desktop. The X Window system supports this, yet it requires all this scripting hoohah that I don't feel like delving into. I just want to be able to quickly get it set up and throw Thunderbird above me and work Firefox on my main monitor without acquiring a headache with messing in .conf files.

Well...if there's a simple cut and paste solution, I'd be happy to hear it.


**Meager Sound Support**

I can overlook the fact that Ubuntu doesn't come with MP3 support built in. I can find the codec, no problem. What every Linux distro I've tried so far (including Ubuntu, Fedora, and SuSE) has in common is a problem dealing with multiple applications playing sound. If I have XMMS playing music and I decide to watch a YouTube video, I'll be watching that video without sound because Linux doesn't handle sound like Windows can. Is this a limitation of Linux or do I need to flip a buried switch?


**Learning Curve**

When using Linux, it's guaranteed I'll come into situations where I have to mess with file permissions, which is fine if I knew the terminal commands by heart. I never used a Unix operating system before I tried Linux, and I have barely learned anything in the command line besides *sudo apt-get install porn*.


**My Demands**

I want to switch to Linux. I'm almost desperate, even. The sad truth is that either it's not ready for my kind of use or I'm not ready or it. But as far as ease-of-use, it does have some areas that need brush-up. For some things, I find myself puzzled at why I need to use a command line when Windows makes it so easy in a GUI. In some cases, I'm forgiving, but in some cases (such as the multi-head support) I wonder why the heck I have to go through this kind of trouble to get things working the way I want them.

I want to switch and be able to brag to my friends that I'm a Linux user, but Linux is impeding my ability to switch. Please help me make the switch!

---

### Post by cilynx on 2007-01-14
**Dual-Monitor:**  

This is outside of my scope, but I know people using Xinerama with very few problems.

**Sound Support:**

This isn't Linux, but rather your sound card's limitation.  A "real" sound card can be "opened" more than once, thus allowing multiple sounds to be played at once.  "Bargain" sound cards and some built-ins save some hardware cost by only allowing a single opening.  Linux gets around this through the use of "sound servers" such as ARTS (default in KDE) and ESD (default for Enlightenment) which combine all of the sounds that your system can make into a single stream with is sent to your card using a single "open".  Windows runs a sound server as well.  This is why it appears that your card works better under Windows.  Look at your audio preferences and you'll find things about sound servers.

**Learning Curve:**

File permissions can be accessed in the GUI by right clicking and selecting Properties.  There is a permissions tab.  This is about security.  If you want a Linux system that is wide open, look into Damn Insecure Linux.  (I'm not kidding.  It exists.)

**Demands:**

Your demands are about the same as what everyone else wants.  They want an easy to use operating system with perfect hardware support and they don't want to pay for it.  The problem is that the hardware vendors like money and that's the language that Microsoft speaks.  Big corporations are willing to throw money into multi-head.  Your average hack doesn't even care about it.  It just makes sense that a pretty system for multi-head hasn't been developed by the hacks.  As the old saying goes: if you want it and it isn't currently available, you write it.  That's why you've got the source.

Welcome to the community.

---

### Post by riven0 on 2007-01-14
Well, first, the majority of things can be done without the terminal, but it's true that if you want something like dual-monitor support, you're probably have to dwelve a little into it. I'm sure there is a tutorial around here, and I'm going to try to find it in a moment. 

But one thing you have to realize is that there* is* a learning curve, and that isn't something you can escape. If you're just one of those people who just go on the net, check your mail and write up a few word documents, then the learning curve will practically be nothing. Otherwise, be prepared to forget everything you were taught about Windows and learn the Linux way of doing things, because, believe me, it's much different... though I find it much superior. :) 

Give me a minute, I'll be back...

---

### Post by moshuptrail on 2007-01-14
If the primary reason you have for using Linux is:

> I want to switch and be able to brag to my friends that I'm a Linux user.

then you will find it very difficult indeed.

The fact is, you will need to learn the command line.  There are still too many things that require you to use the command line.  It will take 6 months before you begin to feel really comfortable, and even then you'll still find things that puzzle you.

My suggestion to you would be this:  Set yourself up a dual-boot system so you can continue to use Windows while you learn Linux.  That's what I did, and after about 3 months I erased XP completely from my laptop.  I still dual boot my desktop because there are still times when things just can't be done in Linux because a vendor doesn't provide Linux support.

Start with specific posts here, and there are lots of folks who are more than happy to help you along the learning curve.

---

### Post by transactionlogfiller on 2007-01-14
**Dual-Monitor Support**

Depends on what graphics card you have. Requires the command line but could be as easy as a one-liner. There is an excellent how to on here somewhere.


**Learning Curve**

That's what this forum is for :) There are loads  of things I can never remember how to do but I can remember how to find the instructions.

---

### Post by annda on 2007-01-14
> 
**My Demands**

I want to switch to Linux. I'm almost desperate, even. The sad truth is that either it's not ready for my kind of use or I'm not ready or it. 

as much as i like to convince people to switch, it's obviously not for everyone.  if you follow e.g. the open source hardware debate, there are good reasons why Linux will not take care of all your hardware - and it's called closed source drivers. if you say Linux is not ready for you, what you mean is that the producer of your hardware is not ready.

if you are desperate, make sure you get compatible hardware and this will surely spare you a lot of command-line related headache.

you can satisfy all your needs as a computer user by buying the right hardware from the right companies.

---

### Post by adewale on 2007-01-14
i didn't know there was a sound problem cause i open kaffeine and play music at the same time play hangaroo and both produce sound. i've never encountered a sound problem but whatever your problem might be, i have confidence in this forum's ability to solve them

---

### Post by MasterOfDisaster on 2007-01-14
About the dual monitors, the guide depends on what video card you have:
NVidia (binary driver): [http://www.ubuntuforums.org/showthread.php?t=301946&highlight=twinview](http://www.ubuntuforums.org/showthread.php?t=301946&highlight=twinview)
ATI (binary driver): [http://www.ubuntuforums.org/showthread.php?p=1773544](http://www.ubuntuforums.org/showthread.php?p=1773544)
ATI (open-soucre 'radeon' driver): [http://www.ubuntuforums.org/showthread.php?p=1773710](http://www.ubuntuforums.org/showthread.php?p=1773710)
Any card with working drivers: [http://www.ubuntuforums.org/showthread.php?p=1773624](http://www.ubuntuforums.org/showthread.php?p=1773624)

Of these four options, xinerama should only be used as a last resort, as it is the most complicated to set up, and only allows 3D rendering on one monitor.  For more in-depth information about the different options, take a look at this comprehensive post:
[http://www.ubuntuforums.org/showthread.php?t=221174&highlight=mergedfb](http://www.ubuntuforums.org/showthread.php?t=221174&highlight=mergedfb)

About the sound problems, there are two main sound implementations in Linux.  There is OSS, which does not support sound mixing (only one program gets sound), and ALSA, which does support sound mixing.  To check if ALSA supports your card, look here:
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)
It does, try to enabling the sound mixer by going System --> Preferences --> Sound Preferences.  Go to the Sounds tab, and click the check box labeled 'Enable software sound mixing'.  Hopefully that will work.

Anyways, good luck with learning the command line, it takes a bit getting used to.

Cheers

---

### Post by daka on 2007-01-14
I agree with all the good advice above.  It has taken me a few years to make the switch and lots of "learning curve"... I have tried Mandriva, Suse, Fedora, Ubuntu, Knoppix, Kubuntu, and about seven or eight other distros.

One distro, in my opinion is easier than all of the rest, especially for a newbie.  I discovered it last week, installed it, and I am extremely happy with it.  It is fairly new and it is called Linux Mint.  It is simply a Ubuntu distro that has much of the "proprietary" software included, like MP3 and DVD multimedia capabilities.  It makes many other things easier.  

I was wondering why there weren't any brave rebel-types in the Linux world to test the metal of the proprietary legal types who have threatened nasty actions against everyone who uses "their" closed source software.  The "Mint" distro was made in Ireland which explains the bravery and rebelliousness of the originators.  They are fortunately taking on the Tekno-Imperialists who do bear some resemblances to the British imperialistic arrogance (past, of course!).

The Linux Mint Distro can be found at:

[http://lt.k1011.nutime.de/](http://lt.k1011.nutime.de/)  ---- a German server  (probably to confuse the lawyers)

The Linux Mint Forum can be found at:  

[http://lt.k1011.nutime.de/forum/index.php](http://lt.k1011.nutime.de/forum/index.php)

The forum is excellent.  The distro as I said is basically Ubuntu.... with much more

(Mint uses all the Ubuntu repositories)

Good luck 

Daka

---

### Post by riven0 on 2007-01-14
Awww! MasterOfDisaster got to the guides before me. Oh, well...:) In either case, it does depend on your graphics card. 

And I agree with moshuptrail that if your just switching to Linux to brag to your friends about your elite skills, you're going to run into a lot of trouble. 
But I don't agree that it'll take you 6 months to get comfortable with Linux. That could be a general rule, but I was comfortable enough with Linux by the end of my first month that I permenantly deleted Windows. So it really all depends on how enthused you are to learn something new.

Good luck! :KS

---

### Post by cilynx on 2007-01-14
MoD, your OSS vs ALSA statement isn't entirely correct.  You can software mix using OSS, it's just via Sound Servers as opposed to built into the system.  If you have a real sound card, e.g. a SoundBlaster Live! (circa 1999 or newer), OSS can and does very easily open the card over and over and you can play as many concurrent sounds as you like.  (Actually, I believe the SBLive is limited to 64 opens at a time or some such, but I don't think I could deal with that many sounds at once anyway)

---

### Post by louieb on 2007-01-14
> **Leonaken said:**
> 
I want to switch to Linux.... Windows makes it so easy in a GUI...  multi-head support...have to go through this kind of trouble to get things working the way I want them.... Linux is impeding my ability to switch. 
This probably belongs in the cafe. I loaded Linux for the first time last April just for the heck of it. I have found it to be fast and reliable for the things I want it to do. The link you gave as a reason to switch, well that not new if the US government want to snoop around on your computer not much you can do. 
Anyway back to Linux, sure its behind MS in the GUI application area. If GUI applications and not having a government hook in it are the most important things a computer has to provide for you then you may want to look at a MAC. 

When I start a software project I tell the buyer there are 3 things he can choose from: good (thought testing) , fast (ASAP), and cheep (low cost).
Then I tell him he gets to pick 2.
The reason I now run Linux is I was trying to get IIS (the web server that comes with Windows) to serve up PHP pages. What a pain! I found it was easier to  run Apache under XP and serve my PHP pages that way. It just seemed natural to run the server under Linux.
Linux is what it is. And its not impeding you from using it. It can't

---

### Post by Sef on 2007-01-14
> The reason I now run Linux is I was trying to get IIS (the web server that comes with Windows) to serve up PHP pages. What a pain! I found it was easier to run Apache under XP and serve my PHP pages that way.

Which is why Linux has about 2/3 of the web server market and Microsoft has about 20%.  Now for the web server virus market, Microsoft has that all wrapped up; Linux just can't compete there.  :p

---

### Post by Leonaken on 2007-01-14
Thanks for the help, everyone. Working to get my dual-head working, and I´&#314;l work on the sound issues.

Didn´t mean to come off as a 15 year old looking for street cred by using *Teh Lunix*. ](*,)

---

### Post by rabid9797 on 2007-01-14
> **moshuptrail said:**
> 

nice avatar;) 


but on subject:

switching from windows to linux can be a very hard change for some people. its a whole new expierence, where things aren't put before you with one click answers and fixes. unfortunatley, thats part of having linux, but if your going to switch your going to have to realize your going to need to learn a whole new way of dealing witih computers.

i remember when i first really started getting into linux, i had just had a fatal boot error with windows and no longer had a way to access windows, so i was thrust into the only other working OS on my computer, which was ubuntu. its frustrating at first, and its a little hard to figure it out, but you get the hang of it and eventually see that its not some in unconquerable monster but just a diamond in the ruff. 

just keep at it and you'll eventually get over the roadblocks 8)

now, fortunatley for you, there is an entire community of ubuntu users at your disposable to help you with all your problems. :D 

IRT: dual monitors

that was one of my biggest concers when i started using ubuntu(two identical screens just isn't the same is it?)

so try this thread:
[http://ubuntuforums.org/showthread.php?t=221174&](http://ubuntuforums.org/showthread.php?t=221174&)

---

### Post by riven0 on 2007-01-14
> **Leonaken said:**
> Thanks for the help, everyone. Working to get my dual-head working, and I´&#314;l work on the sound issues.

Didn´t mean to come off as a 15 year old looking for street cred by using *Teh Lunix*. ](*,)

Not a problem. We just wanted to make sure you knew what you were getting into. :) 

As for your sound problems, try posting the error message your getting. Perhaps one of us can help you out...

---

