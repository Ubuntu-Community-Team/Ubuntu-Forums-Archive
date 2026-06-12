---
title: "Virtual Ubuntu"
date: 2009-05-28
forum: Apple Hardware Users
---

### Post by pmaciver on 2009-05-28
I was just thinking of this and wanted to see if anyone else was doing/thinking of doing this.

instead of trying to geting all the quirks working on a native install of ubuntu on a macbook, install it on something like vmware or virtualbox and manage it full time through that.

Anyone with any opinions on this please let me know, advantages/disadvantages and anything else you might think.

---

### Post by xuCGC002 on 2009-05-28
This may seem like a good idea. The only problem I can think of is noticeably slow performance and resources being used a little more than functionally proper for the host OS. But this has been done, many times before. I use Windows within a virtual machine, and I've used liveCDs (Including Ubuntu) and installations of Linux through VirtualBox, and they work pretty good. Just make sure you have good enough resources, or I'll be quite sluggish.

---

### Post by motsteve on 2009-05-30
I have an iMac 20 inch (2.16GHz iMac5,1) with 3G ram and the latest Leopard (can't keep up with the rev's :-) ) and have installed almost every Linux 32&64 bit i386 distro that you can imagine on it.  I also have a 2.56GHz i586 machine with Ubuntu 9.04 on it. I don't have any bench marks, but I spend enough time banging on the keyboard to know that my iMac running Ubuntu 9.04 using VMWare Fusion (latest rev) is snapper than Ubuntu on my Windoz machine.  The only draw back is that VMware has crappy support for Linux on any machine and you can't get the VMware tools to work reliably on any distro.  I would instead recommend using Refix and dual booting Ubuntu if you have an iMac with an Intel processor (not a G5 ppc).  

BTW, I also have a G4 DA running Ubuntu 9.04PPC on it and it is pretty good, but forget support for Flash, etc.  

I hope this was informative.

---

### Post by pmaciver on 2009-05-30
Thanks for the information. 

My thing is that I would love to just use ubuntu exclusively on this macbook that I have, I even backed up everything, wiped the machine and did just that using refit. 

But there are 2 issues that made me go back to mac os, even though I think it is a less capable os than ubuntu in my opinion seeing that I am a developer, and those things are

1. Sound is not great, even after compiling the patched alsa source code

2. Battery life is about half of that on Mac os.

What gets me is that there is a wiki with all the tweeks that you can do to get ubuntu working fully under mac, I don't see why they just don't apply all these tweeks and create an installable image for us to use. That way the people in the know can just point to 1 file and say "use this" and that would be it, and then just detail all the changes that were made in the image for those that were interested.

At the moment all the info seems to be splintered all over the place and even the wikis that cover the different models and versions of ubuntu don't cover everything fully.

I have a macbook 5,1 and I just want ubuntu running on there and not have to spend hours looking for the information that I need to get it running properly.

Mac os for me just does not work, no package management, limited customisation, just one way to do things (this might be why some like it, not me). I just feel to restricted with mac os. They say you don't miss what you never had, well with ubuntu I had freedom, and now I don't have it I really do miss it. The mactel guys have done a great job so far, just need a final push.

---

### Post by Richardcavell on 2009-05-30
My two cents, for the record:

1.  Virtualization just isn't like the real thing.  Firstly, you are splitting your resources (particularly memory) between two operating systems.  Neither will work as well in this situation.  You should use it just to determine whether the guest OS is compatible and whether you like it.  Once you're happy with it, give it its own partition and install it properly.

2.  The ubuntu installer should definitely pay more attention to Mac-specific needs.  If I knew anything about how to program it, I'd do it myself.  Mac OS X will always be streets ahead of Ubuntu in certain areas for that reason - it's tuned for Mac.

3.  You're right, sound is pretty ordinary on Linux.

Richard

---

### Post by motsteve on 2009-05-30
There's scads of ways to customize the Mac, but they are all in utilities out on the web on Versiontracker, etc.  Yes Linux is customizable, but really it is not for anyone that isn't a geek.  I'm a pseudo-geek and like to tinker, but the thing I like best about Linux other than it is basically Unix with X windows, is the fact that most, if not all the software I want to use is free and constantly being improved via the OpenSource community.  

BTW, I've been using a Mac since day zero being #4 to take delivery in Broward county of a 128K Mac on February 16, 1984 and have had Macs all the time since.  I've used MacOS, Linux, Unix and Windoz for both work (electical engineering and manufacturing) and home.  I love my Mac (BSDUnix), Linux and will tolerate Windoz, but only XP or 2000.  Even MS die hards hate VISTA.  :-)

Just Another Geek.

---

### Post by cyberdork33 on 2009-05-30
> **pmaciver said:**
>  What gets me is that there is a wiki with all the tweeks that you can do to get ubuntu working fully under mac, I don't see why they just don't apply all these tweeks and create an installable image for us to use. That way the people in the know can just point to 1 file and say "use this" and that would be it, and then just detail all the changes that were made in the image for those that were interested.
Since it is so easy, you go ahead an start implementing all the fixes that are out there for every mac and make a new ubuntu-based distro... Then when everything changes in the next ubuntu release you can do it all over again (after all the needed tweaks are 'found' first). 

Point is, it is ALOT of work, and Macs are just one small portion of ALL the problems Ubuntu has with hardware. Go look through the bug reports on launchpad and you will see that there are a lot of things that can be fixed.

Finding and documenting the 'tweaks' (workarounds, broken drivers, fixes) and filing bugs about them is how Ubuntu gets fixed.... it takes a little time is all.

> **pmaciver said:**
>  At the moment all the info seems to be splintered all over the place and even the wikis that cover the different models and versions of ubuntu don't cover everything fully.

I have a macbook 5,1 and I just want ubuntu running on there and not have to spend hours looking for the information that I need to get it running properly.They are community wikis. If something is missing, edit the page and add a note about it. If you find a (better) fix, add it to the wiki.

> **pmaciver said:**
> The mactel guys have done a great job so far, just need a final push.Wait, YOU are the mactel guys. The people that make the wiki pages, the people that find the bugs, the people that make fixes are just the users... If someone needs a push, start by pushing yourself.

---

