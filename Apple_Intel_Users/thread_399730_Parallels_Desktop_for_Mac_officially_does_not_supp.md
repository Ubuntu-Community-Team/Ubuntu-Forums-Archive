---
title: "Parallels Desktop for Mac officially does not support Ubuntu 6.06 &amp; 6.10"
date: 2007-04-02
forum: Apple Intel Users
---

### Post by nanostar on 2007-04-02
why is that?
are there problems installing/running newer Ubuntu versions?

// Parallels Desktop for Mac does support as guest OS :
• Ubuntu Linux 5.04



what about using VMware Fusion beta instead?

---

### Post by Chrisj303 on 2007-04-02
I installed ubuntu 6.06 / 6.10 and the latest kubuntu with no problems whatsoever.
The real problem with linux on parallels however, is lack of native resolutions, NO seamless mouse/focus intergration and poor graphics support.
VMware fusion beta is already a better option regarding linux virtualisation on mac. When it goes gold it'll be a must-have.

chrisj303

---

### Post by nanostar on 2007-04-03
my problem is:
i "need" Ubuntu 6.10 on my MacBook  (Core 2 Duo) **RIGHT NOW**!

do you recommend installing VMware Fusion beta (rather than buying Parallels Desktop for Mac)?

---

### Post by Chrisj303 on 2007-04-03
yes.

---

### Post by eldoran on 2007-04-03
Virtualization is cool and all -- but if you really NEED Ubuntu -- why not partition your disk and run it native?   Bootcamp and reFIT make it pretty easy..   (on my mac mini anyway)

---

### Post by Chrisj303 on 2007-04-03
> **eldoran said:**
> Virtualization is cool and all -- but if you really NEED Ubuntu -- why not partition your disk and run it native?   Bootcamp and reFIT make it pretty easy..   (on my mac mini anyway)

Oh, definitely...Thats what i do (OSX/UBUNTU/XP via refit). I do use VMware Fusion beta to check out different distro's though - it's really handy, and a much better experiance than parallels.

chrisj303

---

### Post by ryckmonster on 2007-04-04
I need to give VMware fusion a try..

Have you had any experience with Q?  I think its a pretty slick virtualizer, however my Ubuntu installs always seem to take forever and I give up..

---

### Post by cyberdork33 on 2007-04-04
Q is just the GUI, the VM is Qemu.

---

### Post by neorou on 2007-04-04
I can install practically any flavor of ubuntu on my mactels. So far, the successful ones include 6.10 + (Ubuntu, Kubuntu and Xubuntu - Xubuntu being my favorite, being a minimalist and all). 

The easiest way to do this is to use the ISO image of the live cd and run it as the CD media from Parallels, instead of using one or more CD drives. I even got a 64-bit version to install on a Mac Pro. The Mac Pro is notorious to have it install only Ubuntu (i.e., not using a VM and have Ubuntu be a host OS).

I got networking for Samba to work on the Mac OS' system preferences and am sharing files via IP. Parallels does not support either file sharing OR Coherence. If  Parallels wised up and chose to support Ubuntu and Coherence is available for Ubuntu, it would open up the entire Ubuntu and Mac community to each other. 

Paralles also does not include more than 1.5 gb of memory for each virtual machine, only 620 mb of it could support Ubuntu. Increasing the memory past that limit caused Ubuntu to go into kernel panic...:confused: 

When running memory costly applications on a hosted installation of Ubuntu on the Mac, like MAT (Mass Array Tiling - for genomics), it will stop in the middle of loading its genetic libraries because it really requires 2GB of RAM. At this point, the Parallels equipped Macs become useless....

All of this is still true with build 3188 (released March 7, 2007).[http://www.parallels.com/en/download/desktop/](http://www.parallels.com/en/download/desktop/)

......

---

### Post by neorou on 2007-04-04
By the way, if it weren't for the necessity of other Mac only niceties, I would move to Ubuntu 100%. In the end, because of the people I support (who are die-hard Mac people), I can not move to Ubuntu 100%.

I've only done this at home. There IS a reason why I like being at home :) I'm even getting my wife to use it. Pretty soon my cats will use it too....:lolflag:

---

### Post by neorou on 2007-04-04
Should have consolidated all of this in one post, but I got a gazillion things running in my  head today. I apologize for that...

I think the reason why Parallels is only fully-supporting Windows is because they are getting feedback from people who want to use Windows software. I truly believe that if there is enough incentive for people to run linux apps on a mac, Parallels will respond and choose a distro. I really really hope that they choose Ubuntu. I think as far as Desktop variety distros, Ubuntu is right now a front-runner, the only reason being that it IS the easiest to setup, learn and maintain. 

I was a Fedora user for 3 years, and discovering YUM aside (like apt-get command), Fedora had little incentive for me to use it all the time. They've improved quite a lot in recent years, but Ubuntu is far more attractive in every aspect. A real good reason/example: ISO images are far easier to get, at least for us here in the western US. I timed a download of an ISO image between the 2, Ubuntu (downloaded from CSU Monterrey Bay), was about 15x faster. Also, Fedora has 7 ISO images to install vs. Ubuntu's one LIVE CD. 

Hopefully Parallels people will take that into account.

Okay, I think that's all the posting I will do for today...

---

### Post by Chrisj303 on 2007-04-04
I got a bit stinky on the parallels forums about the lack of parallels Tools - the result was worth it though as a parallels official confirmed that the Tools were going to be released in an upcoming build!

TR_606

---

### Post by neorou on 2007-04-04
Parallel tools for Ubuntu specifically or linux overall? did they comment on version numbers? does that matter?

---

### Post by cyberdork33 on 2007-04-04
They have been promising tools for linux for a long time... Meanwhile, VMWare's Fusion is only in beta and already has linux tools that work great!

---

### Post by nanostar on 2007-04-07
i do not want to give up Mac OS right now -

maybe on the long term Ubuntu could replace it but at the moment: NO!

i installed 6.06 on an old PC - my first impression:
i like Ubuntu - impressive
interface better than Windows XP

but there is many small problems...
starting with screen resolution (1024 x 768 instead of 1280 x 1024)
...

i do not want to waste much time with administration and problem solving.
my computer is a tool - not my hobby


This is why i am on the Mac.
(and i have to confess that i consider Mac OS X to be
my favourite OS)


Still i want to use Ubuntu - like the open source idea -
think i will try to install 6.10 on my MacBook using
VMware Fusion Beta 3

hope it will work

---

### Post by nanostar on 2007-04-07
does anybody know about a **roadmap for virtualbox** for mac?

---

### Post by nanostar on 2007-04-07
> **Chrisj303 said:**
> I got a bit stinky on the parallels forums about the lack of parallels Tools - the result was worth it though as a parallels official confirmed that the Tools were going to be released in an upcoming build!

TR_606


please tell Parallels that you want them to support Ubuntu
(i already did so)

[http://www.parallels.com/feedback/]("http://www.parallels.com/feedback/")

---

