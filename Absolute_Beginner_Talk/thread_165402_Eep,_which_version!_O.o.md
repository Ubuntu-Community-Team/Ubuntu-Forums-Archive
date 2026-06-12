---
title: "Eep, which version!? O.o"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by Ningyo on 2006-04-24
I know this is probably a stupid n00b question, so pleae bear with.  I'm new to this entire Linux thing, and am now downloading all the programs that I'll need once I install Ubuntu.

Which version of Ubuntu is currently out?

I was trying to download Audacity for Ubuntu (yay for Librivox!), but it asked if I was using Warty, Hoary, Breezy, or Dapper, and I have no clue which one I'm supossed to get.  

I just downloaded the ISO for Ubuntu yesterday, so it should be the newest version.

So which version of Audacity am I supossed to download? :confused:

---

### Post by mostwanted on 2006-04-24
Just install audacity from Ubuntu's server. It doesn't matter which version of Ubuntu you use because it'll only have versions that are compatible with your OS. See this link for an explanation on how to install:

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by Rinzwind on 2006-04-24
and just to answer your question:

Goto System and the About Ubuntu. It's state what version you downloaded.

Mostlikely it's Breezy (since that's the most uptodate and officially released version).
Dapper Drake comes in month 06.

audacity is inside 'universe'. If you are totally new you might want to add that (and 'mutiverse') to your repository (unless you allready did that).
It's got more software but software that's not officially supported and/or maintained by Ubuntu (staff etc).

---

### Post by gr0kzer0 on 2006-04-24
I understand what you're doing, downloading all the programs you think you'll need before you install. But as a newbie, you'll be far better off if you install first, then get whatever you want/need from the repositories. That way you'll have no installation problems or dependency issues - 2 things that you're almost sure to experience by installing software from other sites. You do _not_ want to end up in a dependency hell!

---

### Post by Ningyo on 2006-04-24
What repositories?

Dependency issues?

I have no clue what you people are talking about. :sad:

:confused:

---

### Post by Rinzwind on 2006-04-24
repositories: that's a place on the web where ALL the ubuntu software is stored.

Go into Synaptic (-> system, administration, synaptic package manager).
Inside Synaptic you go to Settings, Repositories.

Here you can see which ones are accesible. Ubuntu comes with only the ones that Ubuntu maintaince. You can tick the box on the left to be able to open that repository.



If you open your terminal (command line; goto applications,accesories  and start "terminal" ) and type in:

**sudo gedit /etc/apt/sources.list**

you get a text-file with names of the repositories.

Here is a run-down on what to do with this file to get more software:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

And I apologize for using words you didn't understand.
Is this more clear?

---

### Post by Rinzwind on 2006-04-24
Dependecy issues:

If you install a program that you downloaded yourself you need to make sure all the things that program uses are installed.

Linux works some what like this.

I code something. And inside that program I use a library (lib).
When I let you download my software you only get my software and do NOT download that library. This works this way so that you do not end up with 10000x the same librabry for 10000 programs. So you can have several programs that use that one library. 

So if you install my software I should tell you that my program depends(!) on a library and if you install that upfront you can't use it. 

Is this easy enough to follow? If not say so!!

---

### Post by Ningyo on 2006-04-24
Yes, Rinzwind, that was MUCH clearer, thank you.

Which will make getting the software I need much easier.  Man, that's a LOT better than windows! :mrgreen:

---

### Post by Rinzwind on 2006-04-24
No problem.

Oh and I started with Ubuntu Dapper last weekend (tho I have to admit I have some prior Linux experience) and I am a newbie too when it comes to Linux. 


Linux is not harder to cope with than Windows. 
It's just understanding all the messages :) These forums never have let me down yet :)

---

### Post by Rinzwind on 2006-04-24
And do open up multiverse and universe repositories.
There's alot of cool software in there.
And amongst it is audacity so it's installed within a few seconds if you add those 2 repo's ;) 

Oh and what version do you have? Found that out yet?

---

### Post by gr0kzer0 on 2006-04-24
When I started on Ubuntu, a month or so ago, it's my first taste of Linux. And I didn't have internet access, couldn't get my modem to work with Ubuntu at first. So I was getting programs from [http://packages.ubuntu.com](http://packages.ubuntu.com) and some other sites, as .debs or even .tar.gz packages. Doing it that way means I didn't automatically get all the programs' dependencies at the same time. The packages.ubuntu site does list required progs for you, but other people's sites don't. And I ended up in a right mess on a couple of occasions, cos I neededthis dependency, then that dependency, and often it was easier not to bother installing something new at all!

Now though, I just go to Synaptic and choose a package, knowing that all the required dependencies will be installed for me too. It's a _hellishly_ simple system. Linux really has got this installation system worked out with Synaptic

---

### Post by Ningyo on 2006-04-24
As long as my Linksys wireless card is able to work, I should be able to get all of my programs, then.

Errr... are Linksys wireless cards supported?  The only good internet I'll be able to access back home is at the local library (free T1 wireless internet).

---

