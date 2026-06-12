---
title: "New to Ubuntu, 3 yrs with Fedora, should I change?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by oldwierdal on 2007-01-23
I began this journey in the fall of 2003.  Completely self-taught on computers, I migrated through the several gestations of MS, finally got pissed off enough to try something else.  My first exposure to Unix was through my work, so I tried RedHat 9.  Fun!  I migrated through the several gestations of Fedora, currently using FC5.  I attempted a few times to install Debian, first Woody, then Sarge, but the installer couldn't seem to correctly identify/configure even the simples things as my built-in video card, S3 Savage, or my mouse, or even my built-in ethernet card, Realtech.  But RedHat and Fedora installer, Anaconda, never missed, correctly configuring even my old Canon MultiPass C5500 printer, as well as the simple stuff that Debian couldn't figure out without a lot of work on my part.  Not worth it, I thought!
I still wanted to explore other distributions, and would re-try from time to time.  I just installed Ubuntu 6.10, and also installed Gentoo.  Partly because my Linux experience has been entirely rpm based, and partly because Fedora just works, I've found it slow going to change distributions.  But, I still need, for my own satisfaction, to try some others if for no other reason than just to see and try other stuff that's out there.
This installer/liveCD from Ubuntu had me up and running in short order.  I still prefer the Mozilla Suite for browser/mail, so I downloaded and installed from *.tar.gz the latest Seamonkey-mozilla, and then I blew Firefox away.
I have Win4LinPro installed on FC5 for the two remaining tasks I have to do for my work that MUST be run on Windows.  To really give Ubuntu a fair try, I'll need to get Win4LinPro installed on it.  Also, I have the other things which seem to go better on Windows, Quicken, etc., running just fine with Wine, so, I'll want to get wine installed and working on Ubuntu.
I searched for wine on apt/synaptic, but apparently it isn't available as a package.  So, I'll have to download and install it from Winehq in a tar-ball.
Are there any tips I should know about in making this change?  Any help would be appreciated.  Also, any honest experiencial feedback comparing the two ..... strengths, weaknesses, et. al.
Thanks,

---

### Post by 23meg on 2007-01-23
> 
I searched for wine on apt/synaptic, but apparently it isn't available as a package. So, I'll have to download and install it from Winehq in a tar-ball.It is available, but in the Universe repository. [Make sure it's enabled]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html"). More about the components of Ubuntu [here]("http://www.ubuntu.com/ubuntu/components").

---

### Post by hyper_ch on 2007-01-23
If you want a current package for wine, go to the winehq [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) and add the according repositories to your sources.list (it can be found /etc/apt/sources.list ).
Just add the correct repository there, do a

sudo apt-get update

and then a

sudo apt-get install wine

:)

As you are already familiar with linux this shouldn't be a challenge for you :)

---

### Post by lyceum on 2007-01-23
I think that the apt-get, add remove ect that Debian/Ubuntu uses is better than Yum, that Fedora uses. Otherwize I can't see a really big dfference. Also, for any easier way to use MS stuff on Linux/Gnu machines, try codeweavers

[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

---

### Post by TheWizzard on 2007-01-23
> **lyceum said:**
> I think that the apt-get, add remove ect that Debian/Ubuntu uses is better than Yum, that Fedora uses. 

this used to be the situation years ago. yum improved a lot and is not worse than apt-get. 
make sure you get yourself familiar with the package manager. and read [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

i migrated from fedora to ubuntu when dapper was released. ubuntu seems more polished and was better in recognising my hardware. 

make sure you check: 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lyceum on 2007-01-23
> **TheWizzard said:**
> this used to be the situation years ago. yum improved a lot and is not worse than apt-get. 
make sure you get yourself familiar with the package manager. and read [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

i migrated from fedora to ubuntu when dapper was released. ubuntu seems more polished and was better in recognising my hardware. 

make sure you check: 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Mine was a personal oppinion, not a technical one, I guess I should have said that. I tried Fedora 6 a few weeks ago. Maybe I am jsut use to what I use? Thanks for the info though.

---

### Post by oldwierdal on 2007-01-23
My thanks to you both, 23Meg and sjau, for the tips.  Please accept my appologies for not doing more reading before posting.  I admit I got a bit lazy....... sorry!
Actually, I never did like yum as a package manager.  First, it was really slow, in my opinion, and it seemed to be error prone, leaving multiple versions of things, and breaking others.  It is much faster now, but still prone to errors, I think.  There are some who swear by it.  Others, like me, who switched to apt/synaptic and swear by that just as fervently.  To each his own.  I'll stick with apt/synaptic whether I continue with FC or stay with Ubuntu.
As for using Crossover vs Win4LinPro, I've already purchased a license for Win4LinPro, and I really like it.  I don't think I'll be spending any more cash for the privelege of using Windows.  As soon as I find alternatives for the two remaining tasks, Windows will become free electrons floating about the atmosphere.
Just as with anything else new, learning how to use the 'deb' methods will just be a matter of doing it.  Although I'm good enough with Linux of any flavor to get myself in trouble quite easily, and I'm sure the trend will continue with the 'deb' methods, I've learned how to find and fix most of my blunders, and most of the time, not cause myself more problems.
So far, if you can call not quite 12 hours 'so far', Ubuntu seems to be just as straight-forward as anything FC puts out.  I'm not really dissatisfied with FC.  Rather, I think that they've pushed the release cycle way too aggresively, and release versions with too many flaws, and wait for users to find and fix them.  Just my opinion, of course.
Anyway, thanks for the feedback, all.

---

### Post by hyper_ch on 2007-01-24
For running Win-stuff you could always consider using vmware... that's what I do...

---

