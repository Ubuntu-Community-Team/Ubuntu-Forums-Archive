---
title: "Considering Ubuntu ..."
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by KentDA on 2007-07-14
Ok, I'm sure this has been brought up many a times, but ... here goes.

I'm relatively computer savvy, having worked with computers since the days of windows 286. For those not so much in the know, this was BEFORE windows 3.0

I'm looking into buying a new system.

I liked Windows XP and was considering upgrading to Vista (but the cost is outrageous and I've yet to hear anything good about it). My reasons for considering the upgrade was because I repair computers at times, and so I need to know the OS that is dominant.

So ... my question is this.

I've considered off and on over the past two years getting into Linux, ever since a friend of mine showed me that it runs about as smooth as Windows and has most of the support of Windows. Combine that with proggies like Wine and you've got a lot more windows based support for programs that don't exist on Linux natively.

The system I'm looking at is thus ...

AMD 64x2 3800+ (may go higher, but definitely going for a dual core)
1 GB Memory (not likely to start out with more, but will upgrade in time)
Geforce 7300 or better video card (again, this is the minimum level I'll get)
Current Sound Blaster Card (not sure the title off hand)
Western Digital 200+ GB HD

etc, etc. Those I felt were the vitals. I won't have anything odd like scanners or webcams, just the basics.

From the research I've already done, most of what I'd use a computer for is already natively supported by Linux. Save for a few programs like World Of WarCraft(and even that can work with some effort).

Considering for down the road upgrading to Vista as a secondary OS (IE dual boot), is Ubuntu a good choice for an OS?

I'd mainly use the computer for every day stuff: writing, listening to music, watching dvds, watching video files, peer to peer download ... think that covers what I'd use it for.

If I have to get into the nuts and bolts, I don't care, so long as I dont have to do it like on the hour or anything like that. I'm relatively computer savvy, so I'm not afraid to get in there and tweak things.

---

### Post by p_quarles on 2007-07-14
It looks like it'll mostly work. The video card should work out of the box, but you may find you'll need to install nVidia's proprietary driver for optimal performance.

The one thing that concerns me is the sound card . . . there is a "current" SoundBlaster product that is completely unsupported in Linux (they won't release the specs). So, be sure to get the product name and make sure it's not that one.

---

### Post by KentDA on 2007-07-14
Had to track down the name. The names are getting funky these days, I swear!

Sure, there is better, but its still a good sound card.

Sound Blaster Audigy SE.

Yes, there are better, but I have to keep my costs down as much as possible.

Another question, is Crossfire or SLI supported for Linux? I'm considering for down the road. And appreciated about being advised about their drivers. I've read that ATI support is ... questionable at best, that and I've had better luck with nvidia cards anyway, so ...

Also, not trying to incite a small war here or anything, but is there a major difference in terms of how well Ubuntu or other Linux versions runs on AMD or Intel? I prefer AMD, but I'm willing to look at Intel for a change. Since the costs are relatively close together in terms of general power.

---

### Post by p_quarles on 2007-07-14
Do mean the Audigy ES? I looked on the hardware support page (link below), and it looks like it works with one driver, and not with another.

If you have choices, though, I'd suggest you go with a RealTek card. They've worked fine for me without any tweaking, and the company actually releases Linux drivers, which comes in very handy if you have any problems. 

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

EDIT: On AMD vs Intel, my understanding is that they both work fine. I'd recommend against getting the 64-bit version of Ubuntu, though, just because the headaches you will encounter with it are not worth the minor performance upgrade on an already fast system (IMHO). The 32-bit OS will work fine on a 64-bit chip.

---

### Post by dorath on 2007-07-14
KentDA,

Your story sounds similar to mine. :)

The only thing you stand to loose by giving Ubuntu a shot is the time you spend setting it up and trying it out.  If you don't like it, you're not going to be out any of your hard earned cash, so why not give it a go?

Personally, I've found that aside from some games that run much better on XP, Ubuntu does everything I need (and a whole lot more).  Between these forums and a few Google searches, the learing curve hasn't been nearly what I thought it would be, and it'd be even easier if I wasn't forcing myself to learn the command line.

Best of luck to ya!

---

### Post by arvevans on 2007-07-14
KentDA

I too have an AMD 64-X2 3800 system which runs Ubuntu 7.04 Linux (No dual-boot, no MS OS).

Most of the Ubunto repository stuff will install and run with no problem.  I did find problems with some external Linux programs (Skype, Google Earth, etc.) that do run on 32-bit machines with Ubuntu, but will not install on the 64-bit X2 architecture.  There are libraries available that claim to support 32-bit on 64_X-2 systems, but the problem programs detect my 64-bit system and refuse to install.

This will undoubtedly get better as more and more X2 64-bit systems become available, but today this is bleeding-edge architecture and not all that well supported.

Now, having said that, I use Ubuntu_64 for CAD programs, Graphics work (mostly GIMP), PCB layout, and for electronics circuit simulation with quite satisfactory results.  AMD 64-bit X2 architecture with Ubuntu-64 and the available applications all do a very good job for me.  

I have been told that the 32-bit version of Ubuntu will install and run on my dual 64-bit system but I have never tried that.  Possibly you could set up a dual-boot system with 64-bit Ubuntu on one side and 32-bit Ubuntu on the other and have full benefit of both environments..?

Arv
_._

---

### Post by KentDA on 2007-07-15
Well, from what I've read in the forum, as well as some "introductory" linux books, I'm seeing that outside of a few minor areas, that getting into Ubuntu will be easy enough. Combine that with Wine or Cedega, I'll pretty much have the bases covered(more of a console gamer than a pc gamer anyway ...)

I did read up on dual boot setups, and realized that perhaps it might not be the safest bet. But, time will tell of course.

Now for a more specific question.

KDE or Gnome?

From what I've seen, Gnome looks a bit simpler to work with, but that's just from the books so ...

For someone who knows computers, but is getting his feet wet for the first time in Linux, which of the two desktops would be better to start with? I know that I can change my mind easily enough later, but I'm looking at first starting out.

Or is it mostly a matter of preference?

Also, I noticed that Ubuntu is Debian based, am I restricted from downloading Linux packages that were designed for a non-debian kernel?

Sorry for continuing to ask general questions like this, many of which probably seem stupid, but ... I want to know as much as I can before I actually sit down and put in the install disk.

The books have helped, but I've found that "users" provide far more useful information than books can ever provide.

---

### Post by p_quarles on 2007-07-15
There is a huge range of packages available directly from the Ubuntu repositories, so you can pretty easily get away with never installing anything else. That said, it is entirely possible to compile applications from source code. That's something to do after you've gotten your feet wet, though. Not really for beginners.

As for KDE vs. GNOME, I prefer the latter. If you're unsure which to choose, though, just run the live CDs for both flavors, and you'll be able to get a better sense of how they each agree with you.

---

### Post by wolfen69 on 2007-07-15
> **arvevans@earthlink.net said:**
> KentDA

I too have an AMD 64-X2 3800 system which runs Ubuntu 7.04 Linux (No dual-boot, no MS OS).

Most of the Ubunto repository stuff will install and run with no problem.  I did find problems with some external Linux programs (Skype, Google Earth, etc.) that do run on 32-bit machines with Ubuntu, but will not install on the 64-bit X2 architecture.  There are libraries available that claim to support 32-bit on 64_X-2 systems, but the problem programs detect my 64-bit system and refuse to install.

This will undoubtedly get better as more and more X2 64-bit systems become available, but today this is bleeding-edge architecture and not all that well supported.

Now, having said that, I use Ubuntu_64 for CAD programs, Graphics work (mostly GIMP), PCB layout, and for electronics circuit simulation with quite satisfactory results.  AMD 64-bit X2 architecture with Ubuntu-64 and the available applications all do a very good job for me.  

[B]I have been told that the 32-bit version of Ubuntu will install and run on my dual 64-bit system but I have never tried that.  Possibly you could set up a dual-boot system with 64-bit Ubuntu on one side and 32-bit Ubuntu on the other and have full benefit of both environments..?
[/B]
Arv
_._

99% of people with 64bit cpu's use 32bit OS. where have you been?

---

