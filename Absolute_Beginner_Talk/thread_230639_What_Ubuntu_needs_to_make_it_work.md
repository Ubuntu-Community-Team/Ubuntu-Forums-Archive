---
title: "What Ubuntu needs to make it work"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by mcvos on 2006-08-06
I've noticed that in Ubuntu there's a huge gap between easily used GUI stuff and the stuff that needs to be done to get things working. And this is not necessary.

Here is an example: Installing Firefox plugins 

Downloading a plugin is easy, but the plugin install script cannot be run straight away. I have to figure out where Firefox stores its downloads, go there from a shell and then run it. Why? Why not make a default app to open files with that checks if perhaps they're simple shell scripts? Why not put "open in sh" in the right mouse button menu?
(After running it from the shell this still doesn't work, but I assume that's the fault of Firefox, because Ubuntu's firefox has more problems than just this.)

This is not the only example of this. Almost every time I try to do anything, the GUI suggests it should be easy, and every time I have to go to the shell to fix it, google for solutions, and half the time I simply give up. It's almost starting to look like I'll have to give money to Microsoft if I want my PC to simply do the stuff I think it should be able to do. I really hope that won't be necessary, but Ubuntu just doesn't look quite ready for people who don't have computer maintainance as their hobby.

---

### Post by ciscosurfer on 2006-08-06
Try [Automatix]("http://getautomatix.com/") or [EasyUbuntu]("http://easyubuntu.freecontrib.org/") :-D

---

### Post by seshomaru samma on 2006-08-06
How long have you been using ubuntu?
I've been using it for less than a year and had the same feeling as you for a long time,
It's only recently that I started feeling comfertable with the terminal and discovered how powerful it is. 
Are you an experienced Windows user ? I am ,and I expected to be able to do the same things I could do on Windows in Ubuntu, What I didn't realise is that I had 3 years of Windows behind me ,so of course I could tweak it to my likings. It was not wise of me to expect the same level in a new system
btw- I know many new Windows users who have difficulties doing the simplest stuff in Windows, like installing Firefox (yes , they downloaded the exe. to temp folder and then couldn't find it...)
I don't know if your case is similar to mine , but if it is , give it some time. 
Ubuntu works. (most of the time;) )

---

### Post by mcvos on 2006-08-06
I'm comfortable with the shell (grew up with Solaris, have used various brands of linux during the last 12 years), but I'm really not that interested anymore in having to spend a day researching all kind of solutions just because I want to install something really simple. Recent years I've been working more with Windows than with linux, but I have no problem doing things from the shell. The problem is that Ubuntu seems to suggest that it has lots of useful tools for everything, when in reality those tools rarely work. Okay, often they do work, but I think a few simple improvements would really help a lot in userfriendliness.

What would be nice, for example, is a tool that automatically detects your graphics card, and installs the appropriate drivers. Instead, you have to do it by hand, and the instructions for doing so are incomplete. There's a document somewhere with very detailed and accurate instructions, but the user has to find it first. Why not write a simple tool that knows these instructions and does this for the user? When new troublesome cards are discovered, make the solution availlable through Synaptic.

Installing browser plugins should be nearly automatic, but instead, I can't get flash to work at all, even after installing the plugin both as user and as root. (Should the plugin really be in .../mozilla, and not in .../firefox, perhaps?)

And then ofcourse there's wine, which is nearly impossible to get working. But that's such a complex piece of software that I can imagine nobody in the Ubuntu community wants to burn their fingers on it.

---

### Post by Tomosaur on 2006-08-06
What you're asking for is perfectly reasonable, but what you have to understand is that this isn't (for the most part) a failing on Linux' behalf. The real problem is that a lot of the software you're talking about, codecs, plugins, whatever, are propietary and bound by licensing restrictions and all that jibber jabber. It's very difficult for a free operating system to acquire permission to use these things by default, which means it's left up to the end user to sort out. It's a sorry state of affairs, but that's just the way it is at the moment. Either the restrictions need to be loosened/removed, or new, opensource formats need to be created which can be included within the OS directly.

Scripts such as Automtix and EasyUbuntu make the transition/installation process a lot easier, but nobody knows about them until they think 'hey, I need <whatever>, how the hell do I get it', and has a look on the internet.

---

### Post by mcvos on 2006-08-06
> **ciscosurfer said:**
> Try [Automatix]("http://getautomatix.com/") or [EasyUbuntu]("http://easyubuntu.freecontrib.org/") :-D

EasyUnbuntu looks interesting (although I have finally managed to get my nVidia card working -- it won't mess with that, will it?), but Automatix doesn't tell what it actually does or installs. Does it do exactly the same things that EasyUbuntu does? Is it better? Worse? The lack of a simple features list for Automatix makes me lean more towards EasyUbuntu.

---

### Post by MarkSheely on 2006-08-06
Anything related to computing has the potential to be frustrating, no matter which OS is being used.  

Did you look at either of ciscosurfer's suggestions?  Or, instead, did you just need to get a few things off your chest?  (That's not meant as criticism - we all need to vent from time to time.)

--Mark

---

### Post by mcvos on 2006-08-06
> **Tomosaur said:**
> 
Scripts such as Automtix and EasyUbuntu make the transition/installation process a lot easier, but nobody knows about them until they think 'hey, I need <whatever>, how the hell do I get it', and has a look on the internet.

Wouldn't it make sense to include EasyUbuntu and/or Automatix directly with Ubuntu? The stuff they install doesn't have to be part of Ubuntu, but a tool that helps to install those things would help quite a lot.

---

### Post by Tomosaur on 2006-08-06
I haven't used either, but have heard great things about both (aswell as a few negatives, but nothing's perfect). From what I've heard, Automatic will allow you to choose what you want to install, but I'm not sure about how detailed the information it gives you is.

EDIT: I doubt they would ever include a 3rd party script with the distrobutions. Complex scripts which call other programs may not work on many people's computers depending on their setup. I think I read that someone working on a program similar to Automatix / EasyUbuntu to include with the distro, but they won't include a script the devs didn't write.

---

### Post by deepank on 2006-08-06
I think that there is a need to bring various customized editions of ubuntu into market which include softwares such as media players, codecs, google earth, c compilers and various other softwares avialable in Automatix. even if it takes 2 cds I would not mind. Moreover what ubuntu needs is an easy installation guide. I had a tough time figuring out how to install ubuntu.

---

### Post by MarkSheely on 2006-08-06
To include either along with the default Ubuntu install isn't possible due to various legal/practical issues.  I agree, however, that more could be done to let new users know that these resources are available.  

Having said that, if a new user comes to the forum with a question about installing a flash plug-in, goes to the "how-to" section, and does about 2 minutes of looking around, they'll have a hard time missing Automatix and EasyUbuntu.

--Mark

---

### Post by mcvos on 2006-08-06
> **MarkSheely said:**
> Anything related to computing has the potential to be frustrating, no matter which OS is being used.

I'm aware of that, and I know that in the long run, Windows will cause me more frustration (because it already has). It was just that all the positive news about Ubuntu gave the impression, and certainly the hope, that linux would be almost as easy as Windows to get working on the desktop.

> 
Did you look at either of ciscosurfer's suggestions?

I just did. They look very useful, but it's not quite clear what Automatix does, and if I should use it in addition to - or instead of - EasyUbuntu. If at all.

> 
Or, instead, did you just need to get a few things off your chest?  (That's not meant as criticism - we all need to vent from time to time.)


Venting is certainly a big part of it. But it's also that I can see how everything could have been made just that little bit easier, to rival with the superficial easiness of Windows. (The problems of Windows, on the other hand, go much deeper and are much more fundamental; I don't see those getting solved anytime soon. Hence my choice for linux.)

---

### Post by Tomosaur on 2006-08-06
That's just the thing though, they CAN'T really be made much easier. It's illegal. It's a common misconception that a new linux install is 'broken' or whatever. It's not. The law is broken.

---

### Post by mcvos on 2006-08-06
But you *can* get proprietary drivers through Synaptic/apt, so if that's legal, the law isn't entirely broken. Proprietary stuff can be installed by open software. So the Ubuntu devs could probably also add the functionality of EasyUbuntu or Automatix to Ubuntu, as long as they do show all the EULAs that come with the proprietary stuff.

---

### Post by kpurcell on 2006-08-06
The issue here is GUI v. Terminal.  Windows has successfully shaken off the command line and is not almost totally GUI.  Linux is the uderpinnings of Ubuntu and is (I believe) primary a command line OS with Ubuntu's versions of either Gnome or KDE or whatever on top of it to make it useful to more people.  Unless you just want to do what is already in the installation, then you have to get under the hood in Ubuntu whereas in Windows you don't have to get  under the hood as much since more peoople are coding gui interface to solve problems.

I have made an attempt at getting Ubuntu usuable three different times now.  The first time I could not get it to install due to problems with ATI.  The next time I got it installed and got it doing the fun stuff I enjoy in my free time but my work stuff simply would not work.  I have three Windows programs that won't install under wine or crossover office.  So I gave up.  Then I learned that VMWare is free and I tried getting it going and now I've got Windows on VMWare running those three programs and for the first time, I am able to do the work I do on Linux with an assist from VMWare.

---

### Post by MarkSheely on 2006-08-06
Unfortunately, the legal issues aren't quite as simple as that. 

You asked if you should use Easyubuntu and/or use Automatix.  You certainly don't need to use them both.  Which you should use is more a matter of what you want installed on your computer.  Take a  quick look through both threads - you'll see what each has to offer.  Post back here if you have any more questions - I'll be watching this thread for another hour or so.

Good luck,
Mark

---

### Post by Tomosaur on 2006-08-06
Yes, propietary stuff can be installed by open software, but it can't be included with an open distrobution, or open source software in general. EasyUbuntu and Automatix aren't breaking the law because they're playing by the big boys' rules. Synaptic can install propietary stuff, this is very true, and it's a shame that Ubuntu doesn't provide some method of installing the 'common' software/drivers post-install, but Ubuntu and linux in general is based on choice and freedom. If the devs created some pre-installed program which said 'you can install these drivers to do this', what about all the alternative, open source formats which are striving to provide an alternative format or even clone of a particular product? Shuttleworth wants Ubuntu to remain free, in all senses of the word, and part of this is the avoidance of pushing the end user into using a closed format to do something when there are 'more free' alternatives and replacements elsewhere.

---

### Post by mcvos on 2006-08-06
> **kpurcell said:**
> The issue here is GUI v. Terminal.  Windows has successfully shaken off the command line and is not almost totally GUI.  Linux is the uderpinnings of Ubuntu and is (I believe) primary a command line OS with Ubuntu's versions of either Gnome or KDE or whatever on top of it to make it useful to more people.

I don't think that distinction is really all that fundamental. The shell is not the OS. In Windows, you can still do a lot of things from the command line (and I do that a lot at work). At the same time, nothing in linux technically prevents you from making an exact clone of Windows' Explorer WM (in case you were crazy and really wanted to do that).

The main difference is in culture, and in the fact that the unix shell is really powerful whereas the dos shell sucks. But in the end, the shell just translates commands into system calls. A purely graphical shell can do that too.

---

### Post by mcvos on 2006-08-06
> **Tomosaur said:**
> Synaptic can install propietary stuff, this is very true, and it's a shame that Ubuntu doesn't provide some method of installing the 'common' software/drivers post-install, but Ubuntu and linux in general is based on choice and freedom. If the devs created some pre-installed program which said 'you can install these drivers to do this', what about all the alternative, open source formats which are striving to provide an alternative format or even clone of a particular product? Shuttleworth wants Ubuntu to remain free, in all senses of the word, and part of this is the avoidance of pushing the end user into using a closed format to do something when there are 'more free' alternatives and replacements elsewhere.

I agree completely with the value of open formats, but as a user, I just want stuff to work.

I consider the greatest success of OSS not GPL software like linux, which has still only a tiny percentage of its market, but Apache, which dominates its market, and uses a much more pragmatic Apache License. Not sure if there is a causal connection there, but I can imagine there is; Apache License makes it easier to combine OSS with proprietary software, which makes it easier to use OSS, which means more people will use OSS. And that is what we want. Or I, at least.

---

### Post by MarkSheely on 2006-08-06
...I don't think I understand.  It is pretty easy to use the proprietary codecs you said you wanted to - use EasyUbuntu or Automatix.  Both are about as easy as easy gets.  

If what you want is a distribution that comes with all of this proprietary stuff pre-intalled for the user, then try Linspire, or something like it.  

You see, there already are linux distributions that have the combination of proprietary software and open source software you seem to be after.  None of those distributions are anywhere near as popular as Ubuntu.  This fact may counter your claim that an integration of proprietary and open source software is necessary to advance the usage of open source software.  

--Mark

---

### Post by robins_web on 2006-08-06
Interesting discussion. Most of the points I've read could just as easily apply to FreeBSD or PC-BSD, which I recently tried. I had so many problems with them I went back to Ubuntu, which installed with no problems on my laptop.

There are several issues at work here. One is proprietary software and hardware, which love to lock you into their worlds. Another is the usual learning curve associated with any new OS. Yet another is the fact that there really is no simple way to find answers about GNU/Linux--regardless of flavor.

For example, it took me 4 hours and visits to about 15 web sites before I was able to undo the mistakes I made to my USB flash memory yesterday. Part of *that* problem is similar to looking up a problem in the index of a computer manual: I know what *I* would call this problem, but what would the guy who wrote the index call it?

For the record, I have had no problems working with either of my laptops and using my HP all-in-one scanner/copier/printer, my Canon digital camera, or my I/OMagic DVD writer. Maybe I'm just lucky, yah?

---

### Post by mcvos on 2006-08-06
> **MarkSheely said:**
> You see, there already are linux distributions that have the combination of proprietary software and open source software you seem to be after.  None of those distributions are anywhere near as popular as Ubuntu.  This fact may counter your claim that an integration of proprietary and open source software is necessary to advance the usage of open source software.

It's not absolutely *necessary*; the first thing that matters is simply quality, ofcourse. And general ease of use (and Ubuntu seems to have plenty of both). But at some point, strict seperation of OSS and proprietary can become an obstacle (for example, I'm not allowed to use GPL stuff in my software at work, because then our own stuff has to become GPL instead of Apache), and I prefer to have as few obstacles as possible. That's why I like open source, but that's also why I prefer a pragmatic approach to open source.

---

### Post by ciscosurfer on 2006-08-06
[This is a good starting point for 3rd Party endeavors for Ubuntu]("http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=46")

Everyone here is making decent points.  We all want things to work "out of the bag."  And ironically, this is one the beauties of Linux and OSS in general -- you can find just what you want if you do a little research (programs all bundled together, free software working in conjunction with their proprietary counterparts, etc.)

There is a learning curve with any OS you install (remember when you first started using Windows?)  And so this includes our bloated friends in Redmond (let's face it though, there are some things that do *just work *on Windows, and that we need to use for work, etc.)

One of the major hangups with Linux in general is the learning curve for desktop users, but I believe distros like Ubuntu, et al, do a fantistic job of cutting this curve in half by providing amazing documentation, support, and an overall feeling of "we actually do care about your experience."

I'm not saying Ubuntu is perfect.  But is anything?  What Ubuntu successfully accomplishes is making it easier for someone new to open-source get their feet wet with a fantastic smattering of GUI's to get the job done, while still allowing those of us with many years of command line experience continue to use its advanced features.

In time, things will change.  They always do.  But for right now, to get your machine happy, we resort to scripts, programs, and projects to complete our overall experience.  If you want to get your box running quickly just the way you like it, both EasyUbuntu and Automatix provide what you need.  Automatix is more robust, offering many more programs to be installed.  EasyUbuntu is just that: easy, and only offers a small fraction of the things Automatix will install for you, but nonetheless, gets the job done. ;)  

The idea is this: you can install all of these programs yourself (spending time, etc.) that these scripts afford you.  Or you can let them do the work for you, drastically cutting the time to install and allowing you to be more productive, faster.  And yes, the proprietary vs OSS debate will continue, but until there is a general consensus on how to deal with these obstables effectively (which I believe there is, but...), we will need to continue to read-up on our favorite drivers, etc., in order to get things all in line. :grin:

---

### Post by MarkSheely on 2006-08-06
> **mcvos said:**
> It's not absolutely *necessary*; the first thing that matters is simply quality, ofcourse. And general ease of use (and Ubuntu seems to have plenty of both). But at some point, strict seperation of OSS and proprietary can become an obstacle (for example, I'm not allowed to use GPL stuff in my software at work, because then our own stuff has to become GPL instead of Apache), and I prefer to have as few obstacles as possible. That's why I like open source, but that's also why I prefer a pragmatic approach to open source.


--I understand better where you're coming from now.

I hope that you choose to stick with Ubuntu.  If there's anything we can do to help you fashion Ubuntu to fit your needs, let us know.

--Mark

---

### Post by The Other Dude on 2006-08-06
Well, what I want Ubuntu for is to use broadband, or more likely the fiber optic Verizon is installing out in the street.  Right now I'm in dial-up mode, my modem needs some detection string whazoo and the documentation for this is gibberish.  But I'm OK with gibberish up to a point, so I save these little .txt files to my floppy - and Ubuntu won't recognize them...so how am I suppose to get anywhere with this?  Print all this crap out I guess.
Can't get to the Windows partition either, same kind of headaches.  The installation dual boot works fine though.
Why doesn't the Wiki just explain right off the bat why MP3s won't work?  That ain't breakin' the law.  
I've been with XP for 5 years and have NEVER entered anything shellish, I've almost forgotten what terminals look like.  Yuk!

---

### Post by Ozitraveller on 2006-08-06
This should give you some idea of where edgy is moving to:

easyubuntu automatix PLF ubuntu-guide: Common Customizations 
[http://ubuntuforums.org/showthread.php?t=206535&highlight=automatrix](http://ubuntuforums.org/showthread.php?t=206535&highlight=automatrix)


CommonCustomizations
[https://wiki.ubuntu.com/CommonCustomizations](https://wiki.ubuntu.com/CommonCustomizations)

Suggestions for Edgy Eft (or maybe Edgy+1)
[http://ubuntuforums.org/showthread.php?t=183958&highlight=automatrix](http://ubuntuforums.org/showthread.php?t=183958&highlight=automatrix)

IdeaPool
[https://wiki.ubuntu.com/IdeaPool](https://wiki.ubuntu.com/IdeaPool)

---

### Post by ciscosurfer on 2006-08-06
> **The Other Dude said:**
> Well, what I want Ubuntu for is to use broadband, or more likely the fiber optic Verizon is installing out in the street...More than likely, the broadband you'll use will be fiber, a SONET (Synchronous Optical Network) ring perhaps.> Right now I'm in dial-up mode, my modem needs some detection string whazoo and the documentation for this is gibberish...The days of dial-up are quickly coming to an end.  Time to upgrade to this century (no insult intended).> ...so I save these little .txt files to my floppy...Who still uses floppies?  They hold a pointless amount a data and quite frankly are obsolete (again, no insult intended)

---

### Post by The Other Dude on 2006-08-06
Verizon's service is called Fios.  It'll be a tad cheaper than broadband around here.
I don't mind the digs about floppies or dialups, they both suck but it's simpler to use the flop than burn a CD-RW over and over.  Well, maybe not, I don't know, the flop works and I figured since I'm just copying little text files what could go wrong?
What indeed!  Is this another proprietary issue?  I'd forgotten that MP3 was proprietary.
I used broadband with XP for a while - quite the hoard of spyware/viruses descended on me, all that Service Pack update update update crap.  Unix being basically immune to viruses and the like is a definite attraction, if I ever get it working!
And why won't Firefox extensions install automatically, like the first fellow wondered?  That another Microhard license at work?

---

### Post by mcvos on 2006-08-07
> **ciscosurfer said:**
> If you want to get your box running quickly just the way you like it, both EasyUbuntu and Automatix provide what you need.  Automatix is more robust, offering many more programs to be installed.  EasyUbuntu is just that: easy, and only offers a small fraction of the things Automatix will install for you, but nonetheless, gets the job done. ;)  


This is really useful information. I had no idea exactly what it was that Automatix installed, but this sounds like Automatix is probably the better option for me.

Thanks.

---

### Post by mcvos on 2006-08-07
> **MarkSheely said:**
> --I understand better where you're coming from now.

Yeah, I may not be the average newbie here. I've used Slackware 2.1 12 years ago (or thereabouts) and have used many other linux distros, but I never got any of them working quite to my taste. I have really enjoyed SunOS and Solaris over the years. In more recent years, I've also been a stupid windows user who didn't know anything about his OS, so I'm combining some very different views. But now I'm an application programmer and really don't feel like worrying too much about the configuration of the underlying infrastructure. That's an admin's job, and I'm not an admin.

> 
I hope that you choose to stick with Ubuntu.  If there's anything we can do to help you fashion Ubuntu to fit your needs, let us know.

I will. Thanks. Who knows, I might even decide to add my own two bits to the Ubuntu community. Don't count on it, though. I'm already in an Apache community, and I also like to spend some time away from my computer every now and then.

---

### Post by mcvos on 2006-08-07
> **The Other Dude said:**
> I don't mind the digs about floppies or dialups, they both suck but it's simpler to use the flop than burn a CD-RW over and over.

A floppy is certainly easier than a CD-RW, but nowadays, USB sticks are the method of choice for this kind of thing.

> Well, maybe not, I don't know, the flop works and I figured since I'm just copying little text files what could go wrong?

No idea. There is a small difference between how Windows treats text files and how unix/linux treats them: Windows uses two characters to signify the end of a line, whereas unix/linux uses only one. The second character usually shows up as a ^M.

---

### Post by ciscosurfer on 2006-08-07
> **mcvos said:**
> This is really useful information. I had no idea exactly what it was that Automatix installed, but this sounds like Automatix is probably the better option for me.

Thanks.

You can find a [changelog for the (X)Ubuntu Automatix here]("http://getautomatix.com/wiki/index.php?title=Automatix_for_%28X%29Ubuntu#Changelog") and a list of programs Automatix installs at [this page]("http://getautomatix.com/wiki/index.php?title=Software_and_Tweaks").  And you can find out how to remove these programs [here]("http://getautomatix.com/wiki/index.php?title=Uninstalling_Software").

If you'd like to know what EasyUbuntu installs, [check here]("http://easyubuntu.freecontrib.org/overview.html").

---

