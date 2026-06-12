---
title: "Total Noob, need help please"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by gordoha on 2007-03-04
I am a total linux Noob.  I have traditionally been ok with XP.  But, I refuse to switch to vista.  So, on this older laptop of mine I figured I'd install linux, and I'd have two years or so to get to know it before my other computers get old and I have to drop Microsoft entirely.

OK, so, I choose ubuntu because it is a big supported package that claims to be user friendly and is totally free.

Install, etc. went fine.

Here are my problems so far:

The Openoffice doesn't come with draw or math.  I go to open office website to download, and it turns out that I have no idea how to install them.  Of course, with windows I would download to my desktop and double click the icon.  Presto!

Here is has some crazy code line.  And here's the thing, I wouldnt even know where to go to put that line of code in.

So first, it is really that hard?  2.  My advice... Linux will never gain ground if you can't just click on the icon to install something.

2nd problem.  I grab some mp3's from my email.  I click on them.. whoa.. turns out that the music player doesn't know how to play mp3's and I need to install something or other.

First, who in their right mind would write a music player that can't play mp3's?  2nd, how would I even go about installing whatever it is I need for it to play mp3's, going back to my first point, its not like I can apparently just download a patch and click on it.

Or, should I ditch the music player that comes with ubuntu and get a new one?  If so, same install problems.


Last point:  Ultimately what will allow me to dump microsoft is the ability to use the programs that I want in linux.  Hoepfully that will improve over time.  Now, however, I run some expensive programs (and example will be Crystal Ball be DecisionEngineering) that is essentially an excel add-in.

Is there a good windows emulator?  I have seen people mention wine, but also seen people claim that it is a bear to get working properly.

Thanks so much for your help!

Thanks

---

### Post by annda on 2007-03-04
clicking works in ubuntu too :-)

if you want to install things but are afraid of commands, synaptic is great (system > administration)

go to settings > repositories and check all the software sources you see.

reload (there is a button)

search for whatever you want, click to mark it for installation and hit apply.

even easier:

in your applications menu you have an add/remove option. go there, choose "all available applications" and again you can search or browse.

---

### Post by toasterofirony on 2007-03-04
You can play mp3s in Linux ;)

You just need to install the codec [a like so]("https://help.ubuntu.com/community/RestrictedFormats")

Oh, and for installing by a click, you can if you have the installer (.deb) on your computer. Infact, it's easier than with Windows. You find this as your play with Ubuntu more :)

---

### Post by Kobalt on 2007-03-04
> **gordoha said:**
> First, who in their right mind would write a music player that can't play mp3's?
People caring about legality maybe... 
All the answers to your other questions are there : [http://help.ubuntu.com](http://help.ubuntu.com)

---

### Post by gordoha on 2007-03-04
Got it.  Thanks to both of you who replied.  Still, one has to wonder about the thought process on not putting support for mp3's in the main downloand.

I mean really, whose genius idea was that?

---

### Post by toasterofirony on 2007-03-04
It's a legal issue, I believe. Not a sudden moment of idiocy on the part of Canonical :P

---

### Post by Kobalt on 2007-03-04
> This is mainly a philosophical decision on the part of Ubuntu's founder Mark Shuttleworth to provide not only a cost-free operating system but an open source one as well (no proprietary software). Using Ubuntu didn't stop me from using proprietary software (yes, I still use MP3 and Flash), but it did make me more aware of what software is proprietary and what is open.
From [Aysiu's website]("http://www.psychocats.net/essays/linuxdesktopmyth").

---

### Post by Daveski on 2007-03-04
> **gordoha said:**
> Still, one has to wonder about the thought process on not putting support for mp3's in the main downloand.

I mean really, whose genius idea was that?

You MUST have heard that MS got burned for $1.5b for including MP3 codecs. MP3 is a patented technology - Ubuntu is completely free, and that means totally legal for you use as you like and to distribute to who you like. You are free to install MP3 codecs, but this is your decision, not 'Ubunutus'.

---

### Post by Nythain on 2007-03-04
Sure linux isnt as point and click friendly as windows... but it also doesnt crash as much as windows or cost as much as windows.

First you should probably do is familiarize yourself with repositories and how your new ubuntu system (or any debian based system pretty much) utilizes then in the /etc/apt/sources.list file

Linux has a few variations of the good ol binary exe file... .deb files and .rpms depending on distro

Then again, one of the great things about linux, is my box is completely different then your box, and by manually compiling software through the cli (command line interface otherwise known as terminal) my linux installation and all my software know this fact.

Mp3's have a non open issue as explained above, so its not a default standard in the wonderfull world of open source free linux... but it is possible. Its not so much designing a player that doesnt play mp3s its a matter of wether or not your system has the codecs so the player even knows what an mp3 is... almost every media player can and will play mp3's as long as it knows it can

so to sum up
Aptitude Repositories and Deb packages will make installing things just as easy if not easier than windows

You need to install mp3 codecs to play mp3s

and configure/compile of software rocks cause i can tell it how to compile it so its more specific to my system

---

### Post by gordoha on 2007-03-04
OK, I have it working.  Thanks so much everyone for your help.  And the speed with which you helped is amazing!!!

Does anyone have any opinion on windows emulator type stuff?

Thanks!

---

### Post by dcraven on 2007-03-04
> **gordoha said:**
> Got it.  Thanks to both of you who replied.  Still, one has to wonder about the thought process on not putting support for mp3's in the main downloand.

I mean really, whose genius idea was that?

It is illegal to do so. Remember, for many of the things you find annoying in comparison to the platform you are used to, there are worthy explanations for that you don't know about or understand just yet. Things like mp3 licensing is already taken care of in the realm of pay software. Things work a little differently here.

Please be patient before judging the new software you use. Sure, it has it's problems, but don't jump to Windows-based conclusions either.

Cheers,
~djc

---

### Post by rocknrolf77 on 2007-03-04
Have a look at [www.ubuntuguide.org](www.ubuntuguide.org) for starters. It can answer many of your questions. If your'e wondering about something, just ask. Lot's of good info and help here at the forums. :)

---

### Post by annda on 2007-03-04
as to win emulators: wine is free and easy to use but not always good with complex programs. crossover office is supposed to be great but commercial. you can try vmware to run a virtual windows machine.

those are just ideas to get you started searching for info. i have no experience whatsoever - still have a win partition for my online tax management.

---

