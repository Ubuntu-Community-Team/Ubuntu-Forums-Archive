---
title: "Are there any Upgrading Guidelines?"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by Jucato on 2006-01-26
Are there any guidelines when you upgrade packages/programs, like which should you upgrade/install first?

This problem of mine came from an experience I had last week. After reinstalling Kubuntu, I did these things, in chronological order:

1. updated kernel from 386 to 686 (running on AMD Sempron)
2. updated NVIDIA to latest kernel (7667 to 8178 )
3. updated KDE to 3.5
4. ran Automatix (firefox 1.5, multimedia codecs, java)

Then I tried to install the latest version of GIMP (2.2.10, the repos only have 2.2.8 ). I took some packages from the Debian site, and in the process upgraded some of the libraries (notably libxrender1 and libcairo). The problem now came when I realized that I needed to compile something and needed kdelibs4-dev, w/c depended on libxrender-dev, w/c in turn depended on an older version of libxrender1. Now I can't compile anything, so I will probably need to reinstall (again), unless I can find some other workaround.

So my question is this: Is there a proper order of installing/upgrading packages (like kdebase, kde-dev, etc) so that dependency problems like this won't happen?

... or probably I should have just sticked to GIMP 2.2.8... :(

---

### Post by gerbman on 2006-01-27
[QUOTE=Fenyx]Are there any guidelines when you upgrade packages/programs, like which should you upgrade/install first?

This problem of mine came from an experience I had last week. After reinstalling Kubuntu, I did these things, in chronological order:

1. updated kernel from 386 to 686 (running on AMD Sempron)
2. updated NVIDIA to latest kernel (7667 to 8178 )
3. updated KDE to 3.5
4. ran Automatix (firefox 1.5, multimedia codecs, java)

Then I tried to install the latest version of GIMP (2.2.10, the repos only have 2.2.8 ). I took some packages from the Debian site, and in the process upgraded some of the libraries (notably libxrender1 and libcairo). The problem now came when I realized that I needed to compile something and needed kdelibs4-dev, w/c depended on libxrender-dev, w/c in turn depended on an older version of libxrender1. Now I can't compile anything, so I will probably need to reinstall (again), unless I can find some other workaround.

So my question is this: Is there a proper order of installing/upgrading packages (like kdebase, kde-dev, etc) so that dependency problems like this won't happen?

... or probably I should have just sticked to GIMP 2.2.8... :([/QUOTE]

The best thing to do is probably install everything using Synaptic.  It should take care of all the dependencies and ensure you're good to go.  Does it give you an error when you try to do ```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by byen on 2006-01-27
sorry this is not an answer to your question but a suggestion. Instead of the 686 kernel...why not use k7 kernel which runs best with all athlon processors. I have an AMD athon xp and it helped speed my pc a little. Incase you are interested here is a [how-to]("http://www.ubuntuforums.org/showthread.php?t=85917") that works!
goodluck.

---

### Post by Jucato on 2006-01-27
gerbman: yeah I installed/upgrade everything through synaptic/adept, except for the GIMP 2.2.10, since it wasn't in the repositories (Debian Unstable and Testing has it). 

What I was looking for was if there is an order/sequence to be followed when upgrading/installing stuff like "install kde-base before upgrading to this version", or like "don't install GIMP 2.2.10 unless you have installed anything that depends on an older version of libxrender1..." Oh, well, that teaches me no to always install the latest...  :(

byen: during my first installation, I upgraded to k7. But KControl and "uname -m" always says that my machine is i686 so I thought I might have done something wrong. Maybe when I reinstall next week I'll go to k7 again. 

Kinda off-topic: is there a way to downgrade a certain library, like libxrender1. It's the only thing stopping me from installing kdelibs4-dev...

---

### Post by az on 2006-01-27
You are going to have to downgrade those packages by hand.  That will remove the packages on which they depend. 

Never mix debian and ubuntu repositories.  Stick with your distro's repo and use backports.  Never mix Ubuntu and debian repos.

Never mix debian and Ubuntu repos.

It's one or the other - not a mix.

---

### Post by bscbrit on 2006-01-27
Azz has provided the best advice - and in case he forgot to mention it, never mix ubuntu and Debian repos :p  There are quite a few problems on this forum that are caused by similar attempts to install the very latest software by finding a 'testing' or 'unstable' version.  They are what it says on the wrapper - testing or unstable and, unless you relish the challenge, are probably not worth the effort it takes to keep them running.  (I expect someone will come straight back at that comment and tell me how version 99.9.9 of whizzprogram works perfectly in their own setup! Please don't - it isn't relevant to this forum in my opinion).

Stick with the standard repos, perhaps add the backports and your system will just keep on going.  

You must also ask yourself 'what additional feature or bugfix in Gimp was provided by the latest version and was it worth the effort?'

---

### Post by Jucato on 2006-01-27
[QUOTE=bscbrit]You must also ask yourself 'what additional feature or bugfix in Gimp was provided by the latest version and was it worth the effort?'[/QUOTE]

After the hell that I've been through re-installing... not that much... :(
I tried to downgrade those libraries by reinstalling the ones that our found in our own Ubuntu Packages Website (Imagine that! I've been searching the net for "older" versions, only to find them in our own backyard). However, it broke 65 basic packages along the way, including kate, adept, and kdm. Left with a black and white console and little knowledge of restoring, I decided to reinstall. Thank goodness I chose to put my /home in another partition the first time I installed! (Thank you Linux, for teaching me the ways of the wise!!)

Long story short, I learned my lesson. Never mix Debian and Ubuntu repos. Oh, did I also forget to mention that I learned not to mix Debian and Ubuntu repos. I don't know if I'm alone in this, but because Ubuntu is Debian-based (on the testing or unstable branch?), I thought that packages from one would work on the other... I presumed that since they were all *.deb, it would work... A presumption I paid with 4 hours of reinstallation (still ongoing. installation finished, just updating KDE).

Well, in some cases, upgrades are worth it, like upgrades to KDE 3.5, or amaroK 1.3.8... other than that, I'll be waiting for Dapper to come...

Thanks for your answers. They were really helpful. :D

---

### Post by bscbrit on 2006-01-27
Fenyx, I'm pleased that you have resolved your problem.

I'm sure that many non-Ubuntu .deb packages will work with no problem in Ubuntu - its just that the programs that the users of this forum choose don't! ;)   However, as an 'average' user I have not found the need for any specific program that does not exist in the usual repos.  I write programs using c++, I run 2 servers, I repair (windows) computers and I do all the usual office type of tasks.  Everything that I need is available and seems to work without problem.  But perhaps I'm just not an adventurous user......

---

### Post by bscbrit on 2006-01-27
Fenyx, One more tip that I have found useful.  I also made the mistake of trying to install software the 'hard' way and, like you and many others, found it caused me lots of problems.

Firstly, write what you have learned in your computer notebook - you do keep one next to your computer, don't you?  Make notes of everything that you do, what works and what doesn't.  Then, when things break or you have to rebuild, you can do so with the minimum of hassle without trying to 're-learn' all those good experiences.  :D 

If you are particularly stubborn (like me!) write in big letters on a poster that you place just above the monitor "DO NOT INSTALL NON-UBUNTU SOFTWARE".  It doesn't stop me from doing anything stupid but it gives me something to smile at when I do! :p

---

### Post by Jucato on 2006-01-27
yeah, I'm too adventurous... or to idealistic. I'm trying to get into Computer Graphics and stuff so I decided to give the latest GIMP a try. But like I said, not worth all that hassle. I was also in the process of customizing my setup when all these problems occured. But take note that GIMP 2.2.10 is the real culprit. Here are the packages that are not in repos but w/c I found necessary for my own use:

1. Yakuake - a very nice Terminal emulator. But if you want a run down version, Tilda is in the repos.
2. Bittorrent 4.2.2 - waaay better than the one in the repos, waaaay lighter than Azureus. I'm still going to try out BitTornado, but it just looks a bit  too umm.. ugly...
3. Java (JRE 1.5) - only 1.4 is in the repos, but this is easily solved by Automatix
4. Firefox 1.5 - again solved by Automatix
5. KSplash Moodin Engine
6. Real Player 10 -  I don't know if any of the other multimedia players could play .rmv's. Haven't tried out MPlayer yet

Most of these are really non-essential... but nice! :D

---

