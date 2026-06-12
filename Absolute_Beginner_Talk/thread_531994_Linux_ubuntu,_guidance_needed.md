---
title: "Linux ubuntu, guidance needed"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by thedonfather on 2007-08-22
Seeing windows vista come out, and having the more reliable xp already installed on my pc, i tried to take the reliability of xp and add the eye candy of vista to it using windowsx transformation pack. Although it is a great pack, it slows my system down too much (in my opinion) on startup anyway, i like my computer to load fast. So now i am looking at a reformat, as well as linux dual booting.

Linux Ubuntu took my eye, but  i have a few questions to ask before i decide to delve into Ubuntu.

I want to reformat my xp windows to begin with. So do i reformat windows xp first? and then install ubuntu on top? This seems most logical, but i don't want to be messing with my system till i know what i'm doing! 

This post seems a bit messy, so heres what i want to know:

1. Ubuntu, i realise just from searching forums, that it is extremely customizable, handles resources better etc etc, but as an OS is it reliable? Does it crash often etc? (Just want some reassurance, being a noob to the linux world)

2. I would like advice, step by step how to reformat my existing windows xp, and then how to instal ubuntu on top, how to partition etc, seems very confusing.

3. Before i touch my system what apps, i should install, from what i know so far ubuntu comes empty out of the box, and you need to install things like automatix? Can, the more experienced user post a list of must have apps, that make ubuntu 'complete' so to speak, as far as usability is concerned.

I currently run a Shuttle system with a nvidia geforce 7900 gt card, i forget what cpu, but the top single core amd. Basically a gaming system. But i'm aware that linux is not a gaming os, but thats why i wish to dual boot.

Anyways all the above infos, would be great if anyone could help me out. Looking forward to joining linux.

---

### Post by tyggna1 on 2007-08-22
Here's my best answer:

It doesn't matter when you reformat XP.  Using the Ubuntu GNOME partition manager that comes with the OS, you can resize your XP partition.  Just make sure you run a chkdsk /f
```

click on run
type in cmd
type: chkdsk /f
press y when prompted, and reboot

```
 before you resize it (and reboot into windows two times after it, just to be safe).  That'll make sure your files are handled correctly when it's resized.
The install will let you make the partitions yourself, and it's all very easy--especially if you already have experience of reformating partitions in windows.  

The only time Ubuntu has ever crashed or worked in any way that was less than reliable was if I manually changed something that was crucial.  As this is sometimes needed to get full functionality, just make sure you know what you're doing before you do it and you'll never experience any crashes.

Also, to debunk a myth:  the Ubuntu OS and essential packages is less than 200mb, so it comes preloaded with about 500mb of software--which includes firefox and open office.  I, personally, found [this article]("http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html") extremely helpful in regards to setting up software and other essential functions of my OS.  


As for usability--that varies depending on the user.  I like to write and record music, so RoseGarden and a low-latency kernel is a must for me--but would be unnecessary for someone who just wanted to listed to MP3s.  However, if you're really concerned about the "completeness" of it, I would look into the Ultimate Ubuntu--as it comes preloaded with a ton of freeware.

If you do the chkdsk /f in windows first, then the Ubuntu Feisty Fawn install wizard should be able to explain things well enough and guide you through the reformating/resizing process.

Post again if you have any more questions.

Just to give you a heads up:  You're lucky.  NVIDIA cards work wonderfully in Ubuntu--and you'll get eye candy from a program, called beryl, that will make Vista look like pre-school.
Also, it's easier to install applications and software in Ubuntu than in windows.  You just go to add/remove on the applications menu, and it'll give you a list of every available application.  Just check the box next to it and click apply and it'll download what it needs, install it, and put a link to it in the applications menu.
At first, Ubuntu just feels like a regular OS, but if you take the time to learn it, and to read in the forums, you'll find yourself more and more pleased with it everyday.

---

### Post by PartisanEntity on 2007-08-22
> **thedonfather said:**
> I want to reformat my xp windows to begin with. So do i reformat windows xp first? and then install ubuntu on top?

Do you mean reinstall XP? If that's the case, then yes, reinstall XP first and then install Ubuntu.

> **thedonfather said:**
> 1. Ubuntu, i realise just from searching forums, that it is extremely customizable, handles resources better etc etc, but as an OS is it reliable? Does it crash often etc? (Just want some reassurance, being a noob to the linux world)

Yes Ubuntu is extremely stable. I think in my 1 year experience with Ubuntu it has only crashed on me once, and to be accurate it was not the operating system that crashed, but some application which caused the desktop environment to lock up.

> **thedonfather said:**
> 2. I would like advice, step by step how to reformat my existing windows xp, and then how to instal ubuntu on top, how to partition etc, seems very confusing.

There are many tutorials on how to do this on both Google and here on the forum, a quick search will turn up many results, sorry I don't have time to search for you right now.

> **thedonfather said:**
> 3. Before i touch my system what apps, i should install, from what i know so far ubuntu comes empty out of the box, and you need to install things like automatix? Can, the more experienced user post a list of must have apps, that make ubuntu 'complete' so to speak, as far as usability is concerned.

Ubuntu comes pretty complete for most of the basic uses. It comes with a web browser, chat software, office applications, some basic games and much more. IMO Automatix is not really needed, but that will depend on your opinion.

> **thedonfather said:**
> I currently run a Shuttle system with a nvidia geforce 7900 gt card, i forget what cpu, but the top single core amd. Basically a gaming system. But i'm aware that linux is not a gaming os, but thats why i wish to dual boot.

Many people dual boot in order to be able to play games using Windows. I have kept a Windows partition in order to be able to use Photoshop.

---

### Post by thedonfather on 2007-08-22
Hey thanks, bit confused with this chkdsk thingy, but i'm sure when i actually come to the install, it will all become clear. Just wanted to be clear on everything. Ok, i'm gonna go ahead and try it out. I'll be back, if i have any problems, especially with all this commandline thingies. Thanks for the help, fantastic community.

---

### Post by StooJ on 2007-08-22
If you do decide to install Ubuntu, I would set up your hard drive partitions first, before you install XP *or* create a partition during the XP installation and leave enough unpartitioned space for your Ubuntu installation.

Since you're reinstalling the whole thing anyway, this is preferable to resizing partitions.

You could do this with the Windows XP CD and then the Ubuntu CD afterwards, or use GParted.

When I am setting up a new dual boot, I install windows first and create a partition for XP (usually about 10gb, because I install programmes on a seperate partition, but you'll need something bigger (20-40gb depending on the size of your harddrive and the number of games you own ;) )

Once Windows has finished installing, I reboot into [GParted]("http://gparted.sourceforge.net/") and set up my Ubuntu partitions. There will be lots of recommendations on the forums about how to partition your hard drive, but [psychocats.net]("http://psychocats.net/ubuntu/partitioning") has an excellent guide on how to plan them. The whole website is an ideal introduction to setting up and using Ubuntu.

I think Ubuntu likes about 10GBs for the root partition (this is the operating system), but someone else will know better than I do. I always give it a healthy bit extra.

Remember you will need a swop partition as well. Look at your ram, multiply the ram by two and you have a good size for your swop partition.

---

### Post by hyper_ch on 2007-08-22
> **thedonfather said:**
> 
1. Ubuntu, i realise just from searching forums, that it is extremely customizable, handles resources better etc etc, but as an OS is it reliable? Does it crash often etc? (Just want some reassurance, being a noob to the linux world)

Well, if we all would say linux is less stable and less reliable, would you install it? You think we would admit if that was true?

> **thedonfather said:**
> 
2. I would like advice, step by step how to reformat my existing windows xp, and then how to instal ubuntu on top, how to partition etc, seems very confusing.

Have a look here: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
And here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
That will answer a lot of questions!

> **thedonfather said:**
> 
3. Before i touch my system what apps, i should install, from what i know so far ubuntu comes empty out of the box, and you need to install things like automatix? Can, the more experienced user post a list of must have apps, that make ubuntu 'complete' so to speak, as far as usability is concerned.

Ubuntu comes with a wealth of software after you installed it. Then you have the repositories where you have thousands of applications at your disposal.... I would advice against the use of Automatix. In the beginning it may easy a few things but it's not really needed and it's not officially supported and an analsys on it did discover a few things that made the the analyst wonder...

---

### Post by tyggna1 on 2007-08-22
Explanation of the chkdsk thingie:

The windows partition often has errors on it.  If it has errors on it, the Ubuntu install shouldn't work (and if it does, then you'll could have more serious issues later).  chkdsk /f is the method of fixing those errors so your Ubuntu install doesn't mess up anything on windows.

---

### Post by tyggna1 on 2007-08-22
> **StooJ said:**
> 
I think Ubuntu likes about 10GBs for the root partition (this is the operating system), but someone else will know better than I do. I always give it a healthy bit extra.


I've been able to get Ubuntu to run on as little as 2GB.  I will note, however, that once you get down to less than 10mb of freespace, it won't let you log on in the graphical user interface.  The size entirely depends on how many applications/pictures/mp3s/ect. you want to put on--but, yeah, 10 gigs is a really good recommendation.

---

