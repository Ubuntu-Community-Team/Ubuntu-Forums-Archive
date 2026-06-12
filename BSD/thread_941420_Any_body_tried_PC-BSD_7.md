---
title: "Any body tried PC-BSD 7?"
date: 2008-10-08
forum: BSD
---

### Post by HuBaghdadi on 2008-10-08
Hey,
Has any one tried PC-BSD 7?
I don't know but I can hardly resist it :)
It is FreeBSD 7 man !
Any stories to share?

---

### Post by cardinals_fan on 2008-10-08
I've never been a big fan of PC-BSD, and the inclusion of KDE 4 does nothing to improve this release.  At least it's based off FreeBSD 7 :)

---

### Post by hajimow on 2008-10-08
I am trying to install FreeBSD 7.0 amd64 on my new PC. I have a separate HD for that. When I put the first disc1, the booting window comes and then when I hit enter or wait for 9 seconds, it checks my resources and then hangs there. the last line that I can see is 
ehcio [ithread]
I also tried i386 version and I got the same result. any help on how I should tackle the problem?
My system is:
LITE-ON 20X DVD±R DVD Burner SATA Model iHAS220-0 
pqi TURBO 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model PQI26400 
BIOSTAR GF8200 M2+ AM2+/AM2 NVIDIA GeForce 8200 Micro ATX AMD Motherboard
SAMSUNG Spinpoint F1 HD322HJ 320GB 7200 RPM 16MB Cache SATA 3.0Gb/s Hard Drive 
Old floppy drive

---

### Post by HuBaghdadi on 2008-10-09
Would you please tell us why you are not a fan of PC-BSD ?

---

### Post by sir_cheats_a_lot on 2008-10-09
not a big fan of pc-bsd either...but im sure it's improved quite a bit since version 1.4.1 :wink:  looks like they have a very frequent release schedule too.  i got that version a little around Christmas i think.

**edit**
oh and my only real complaint was the lack of precompiled software on their site really.    has this improved any?

---

### Post by HuBaghdadi on 2008-10-09
Why?
I realy like it (I didn't try it yet :))
But it is based upon FreeBSD 7, it should be solid as a rock.

---

### Post by kk0sse54 on 2008-10-09
> I realy like it (I didn't try it yet )
How do you formulate an opinion of something you've never tried?
PC-BSD is just a large plate of bloat with a small selection of PBI's

---

### Post by cardinals_fan on 2008-10-09
> **HuBaghdadi said:**
> Would you please tell us why you are not a fan of PC-BSD ?
I think that PBIs are a stupid concept.  DesktopBSD provides a pure FreeBSD system with GUI tools and a KDE desktop.  PC-BSD adapts FreeBSD in their own way, and I don't like it.

---

### Post by Antman on 2008-10-10
> **C!oud said:**
> How do you formulate an opinion of something you've never tried?
PC-BSD is just a large plate of bloat with a small selection of PBI's
+1

For me, their use of KDE4 really put a damper on my interest. But, on the plus side, the RC detected my Intel 3945 wireless card without an issue. I tried the final on my desktop hoping to use it full time, but it just didn't go well.

If DesktopBSD ever releases another version... ](*,) I'll try it.

---

### Post by HuBaghdadi on 2008-10-12
> **C!oud said:**
> How do you formulate an opinion of something you've never tried?
PC-BSD is just a large plate of bloat with a small selection of PBI's
I like it because it is based on FreeBSD 7 (I like this OS so much)...
> PC-BSD is just a large plate of bloat with a small selection of PBI's
Isn't Ubuntu just a large plate of bloat with a small selection of DEB's?
Just curious...

---

### Post by sir_cheats_a_lot on 2008-10-12
actually no.  ubuntu has one of the biggest software repositories of all linux distributions(assuming you enabled the multiverse, and universe sections as well).   PC-BSD literally only had 50 apps total on their PBI section the last i saw it.

---

### Post by HuBaghdadi on 2008-10-12
Please correct my if I'm wrong:
PC-BSD has a tool that is similiar to Synaptic for installing software.
Any FreeBSD package should be downloaded via this tool.
(AFAIK, FreeBSD has more thant 20.000 package in their repository)

---

### Post by techmarks on 2008-10-12
It's just regular FreeBSD so all the packages for FreeBSD will work with PCBSD.

I tried it, it's nice,

The installation is very polished and easy.

But why did they have to pick KDE for the desktop?

At least if they offered a choice at the installation.

---

### Post by HuBaghdadi on 2008-10-12
Any FreeBSD package is installable via PC-BSD packaging tool, right?

---

### Post by techmarks on 2008-10-12
> **HuBaghdadi said:**
> Any FreeBSD package is installable via PC-BSD packaging tool, right?

I'm not sure what you mean.

You can install the PCBSD way, the PBI's (not so much software).

The traditional way (the only one I used since it's what I'm accustomed to on FreeBSD) which is the packages (easy binary install) and ports (you have to compile them).

I don't think you can use PBI's on FreeBSD yet, but any FreeBSD package or port can be installed on PCBSD.

---

### Post by HuBaghdadi on 2008-10-12
My original thouhgt of PC-BSD that it has a software manager like Synaptic.
And via this tool, any FreeBSD package should be downloadable.
For any FreeBSD package to work with PC-BSD software manager, it should be packaged as PBI, right?

---

### Post by cardinals_fan on 2008-10-12
> **HuBaghdadi said:**
> 
Isn't Ubuntu just a large plate of bloat with a small selection of DEB's?
Just curious...
The selection of debs isn't small, but I do consider Ubuntu horribly bloated.
> **HuBaghdadi said:**
> My original thouhgt of PC-BSD that it has a software manager like Synaptic.
And via this tool, any FreeBSD package should be downloadable.
For any FreeBSD package to work with PC-BSD software manager, it should be packaged as PBI, right?
That would be DesktopBSD.  PC-BSD does allow installation from Ports, but they prefer that you use their silly PBIs.  DesktopBSD, on the other hand, provides a relatively pure FreeBSD preconfigured for the user.  Their current stable release is based off FreeBSD 6.x, but they have a snapshot available for FreeBSD 7.

---

### Post by sir_cheats_a_lot on 2008-10-12
> but I do consider Ubuntu horribly bloated.

      odd.. I've never noticed bloat on Ubuntu.. Kubuntu sure, they have that annoying little auto-updater on Kubuntu that runs in the background which is kinda cruel to us dial-up users.  there really needs to be an option to turn that off :mad:. end up going into sysguard and killing apt so i can actually get to where i need to go online.  I left windows to get away from that kinda crap, after all most of us are capable of getting the updates ourselves. 

     anyhow i believe PC-BSD was originally aimed at migrating windows users.  this is likely why they are using KDE, to give the new users a more windows-like feel.  didn't see any package manager like program on my version. though i would imagine there is one in current versions.  was just an icon that pointed to their PBI download site.  

    I will give them their due credit though. From my experience with the version i have, it runs stable and it runs well on 512mb of ram, probably would run decent enough on 256 mb of ram.  and it was pretty easy to use(at least up to the point i played with it).  i think the version i have was based on freeBSD 5 if that makes a whole lot of difference, :lolflag:.

---

### Post by cardinals_fan on 2008-10-12
> **sir_cheats_a_lot said:**
> odd.. I've never noticed bloat on Ubuntu.. Kubuntu sure, they have that annoying little auto-updater on Kubuntu that runs in the background which is kinda cruel to us dial-up users.  there really needs to be an option to turn that off :mad:. end up going into sysguard and killing apt so i can actually get to where i need to go online.  I left windows to get away from that kinda crap, after all most of us are capable of getting the updates ourselves. 

GNOME itself qualifies as bloat in my book.

---

### Post by sir_cheats_a_lot on 2008-10-12
> **cardinals_fan said:**
> GNOME itself qualifies as bloat in my book.

install fluxbox (or any one of the other window managers for that matter), and remove gnome then.  It's not like you are forced to use gnome on ubuntu.  :rolleyes:


 at anyrate this is off topic; i believe we missed that poor soul asking for help on page 1 ;)

---

### Post by Chame_Wizard on 2008-10-13
i want to try t out(you need 3 ISO Cd's for install ?):lolflag:

---

### Post by cammin on 2008-10-13
You only need the first one, the others are just extra packages.

---

### Post by kk0sse54 on 2008-10-13
The FreeBSD repo is *not* available through PBI's although you can install them through ports. PC-BSD generally discourages that because it's deemed too advanced although imo if you're going to be learning and installing via ports you might as well install FreeBSD instead of PC-BSD. My only problem with FreeBSD is the lack of video drivers for my card and the time it takes to install updates (of course there are more than one way but through portmanager it takes days :mad:)

---

### Post by kaffeboy on 2008-10-20
Well, I must say I have tasted the PC-BSD 7 flavor and I must say...IT NEEDS A LOT OF WORK. 

I kinda thought I would like it at first, since it supported Atheros AR5007 Wifi card (which my laptop carries and Ubuntu has failed to support out of the box). I was very happy, until KDE 4 started crashing. No webcam support and the fact that I couldn't enable desktop effects either and their small selection of PBIs. 

Yes, you can install other FreeBSD PBIs, but the whole point of their system is their list of already compiled versions specifically for PC-BSD 7. Which is a pretty small list, by the way. 

What I really praise is how it looks SUPERFICIALLY. It's something I would buy if I saw it on TV on a high end notebook or desktop. It looks prettyful, but like that saying goes..."not everything that shines is made of diamonds". My guess is PC-BSD will be ready in about a year or so, when stable versions are out and there is enough support for devices such as webcams and such.

---

### Post by Antman on 2008-10-20
[PC-BSD 7.0.1 update available]("http://forums.pcbsd.org/viewtopic.php?f=14&t=12542")
I'm hoping this takes care of the *bugginess* I experienced in the 7.0 version. Downloading now to try on my test laptop.

---

### Post by Justin Case on 2008-10-21
> **HuBaghdadi said:**
> Hey,
Has any one tried PC-BSD 7?
I don't know but I can hardly resist it :)
It is FreeBSD 7 man !
Any stories to share?


Yes I have tried it.  I was running Edison Edition and it ran great.  Thought I would download and install 7.0.1 Fibonacci.  I downloaded the i386 iso, and after 2 attempts to get it to install it finally did. I barely found my way around the new KDE desktop, when the screen went black. I lost my patience with it and threw DaVinci on.  Next I thought maybe I would try 7.0.1 on my amd64 machine.  I downloaded the 1.6 gb iso and tried the install.  It wouldn't detect my mouse from the back usb.  It worked in the front though.  Nice. Then the installer just hung
I rebooted and tried 3 more times, installer hung every time.  I tried 1 last time and made it further into the set up, when I noticed the graphical installer page was mis sized. It was too big, and I could'b see the NEXT button to proceed, nor could I see all my options.  
In the trash all the 7.0.1 discs went. So I threw Debian Lenny on the amd64 machine and the install was never easier.

I don't want to screw around with an install.  If they can't make it install trouble free, I don't want it. BSD's Edison and DaVinci run well on my i386 machine, but not 7.0.1 Fibonacci.  Fibonacci sucks as far as I am concerned.  

And PBIs are a great idea.  Who ever said they are stupid is wrong.  They work like Aptitude or Synaptic but better.  You get lazy using the PBI installer though. I do wish they had more programs available in the PBI directory. But PBI is as good as any software installer could ever be. 

So my experience with 7.0 was not a good one. I'm gonna stay with the older release for a while.  It works for me.

---

### Post by Justin Case on 2008-10-21
> **hajimow said:**
> I am trying to install FreeBSD 7.0 amd64 on my new PC. I have a separate HD for that. When I put the first disc1, the booting window comes and then when I hit enter or wait for 9 seconds, it checks my resources and then hangs there. the last line that I can see is 
ehcio [ithread]
I also tried i386 version and I got the same result. any help on how I should tackle the problem?
My system is:
LITE-ON 20X DVD±R DVD Burner SATA Model iHAS220-0 
pqi TURBO 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model PQI26400 
BIOSTAR GF8200 M2+ AM2+/AM2 NVIDIA GeForce 8200 Micro ATX AMD Motherboard
SAMSUNG Spinpoint F1 HD322HJ 320GB 7200 RPM 16MB Cache SATA 3.0Gb/s Hard Drive 
Old floppy drive



Biostar dude??  Anyway, 7.0 seems to be buggy. I don't like the new version of kde. Geez, I don't like KDE at all.  Try an older version.  I have had good luck with Edison Edition and DaVinci.

---

### Post by Antman on 2008-10-21
Just tried the 7.01 version and **don't **like it at all. The desktop and apps are slow and it won't detect any of usb flash sticks. On the plus side, my intel 3945 wifi worked.

---

### Post by kk0sse54 on 2008-10-21
> **Justin Case said:**
> Biostar dude??  Anyway, 7.0 seems to be buggy. I don't like the new version of kde. Geez, I don't like KDE at all.  Try an older version.  I have had good luck with Edison Edition and DaVinci.

I think he's talking about FreeBSD mate in which I would say is anything but buggy ;)

---

### Post by angryfirelord on 2008-10-22
I tried PC-BSD 7 and it corrupted my Vista partition. :) KDE4 is still NOT ready for mainstream usage yet and the fonts looked very jagged on my monitor. Needless to say, I re-installed Vista and just used regular FreeBSD with an XFCE desktop environment. Now I'm much happier.

---

### Post by Antman on 2008-10-22
Well, since PC-BSD7.01 was a big disappointment on my hardware, I'm hoping that **DesktopBSD** will prove to be better.
They have continued with the snapshot builds of the new version (based on FreeBSD 7.1-PRERELEASE):popcorn:

---

### Post by kk0sse54 on 2008-10-22
> **angryfirelord said:**
> I tried PC-BSD 7 and it corrupted my Vista partition. :) KDE4 is still NOT ready for mainstream usage yet and the fonts looked very jagged on my monitor. Needless to say, I re-installed Vista and just used regular FreeBSD with an XFCE desktop environment. Now I'm much happier.

+1 I first tried KDE4 in Slackware and then recently tried it again in FreeBSD and it's buggy and slow as all get out

---

### Post by ahmatti on 2008-12-03
For me PCBSD is just a convinient way to install FreeBSD with hardware autodetection, Flash and Java... The installation worked fine on my Acer laptop, no 3D with mobility radeon though. I don't like KDE4 either so I installed Gnome from ports instead. And I use ports for installing all my software...

---

### Post by Izek on 2008-12-11
> **HuBaghdadi said:**
> Isn't Ubuntu just a large plate of bloat with a small selection of DEB's?
Just curious...

That's why there's an alternate CD.

---

### Post by scottuss on 2008-12-14
I really wanted to try out BSD, so I downloaded PC-BSD and FreeBSD. Well what can I say, neither liked my external CD Drive and so would not boot on my EEE. (I checked over at the FreeBSD forums, they didn't think it was strange that a standard IDE CD ROM drive would fail to be detected...) Ah well.

So I tried PC-BSD on my main system, my PC is a good spec yet I aborted the install about 25 minutes in, it was only 19% done. It was still going, I'm sure it would have succeeded but when I can install any Linux distro or even (gasp) Windows in about 15 minutes total I'm not impressed.

Also I don't like KDE. I'm not having a go at the BSDs but they're not for me.

---

### Post by kk0sse54 on 2008-12-14
> **scottuss said:**
> I really wanted to try out BSD, so I downloaded PC-BSD and FreeBSD. Well what can I say, neither liked my external CD Drive and so would not boot on my EEE. (I checked over at the FreeBSD forums, they didn't think it was strange that a standard IDE CD ROM drive would fail to be detected...) Ah well.

So I tried PC-BSD on my main system, my PC is a good spec yet I aborted the install about 25 minutes in, it was only 19% done. It was still going, I'm sure it would have succeeded but when I can install any Linux distro or even (gasp) Windows in about 15 minutes total I'm not impressed.

Also I don't like KDE. I'm not having a go at the BSDs but they're not for me.

lol Windows does not take 15 minutes to install, however NetBSD does ;). Even most linux distro do not install within fifteen minutes (personal experiences vary but Ubuntu has never been that fast for me). As for KDE that's only default on *BSDs such as PC-BSD and DesktopBSD but for others FreeBSD, NetBSD, OpenBSD, and DragonflyBSD GUI is not included in the installation and you can add gnome or xfce afterwords.

 As for your problem with your CD drive I'm not suprised since one of the major drawbacks that I have found with the BSD OSs is that they are often behind their linux counterparts in terms of Hardware support.

---

### Post by scottuss on 2008-12-15
> **C!oud said:**
> lol Windows does not take 15 minutes to install, however NetBSD does ;). Even most linux distro do not install within fifteen minutes (personal experiences vary but Ubuntu has never been that fast for me). As for KDE that's only default on *BSDs such as PC-BSD and DesktopBSD but for others FreeBSD, NetBSD, OpenBSD, and DragonflyBSD GUI is not included in the installation and you can add gnome or xfce afterwords.

 As for your problem with your CD drive I'm not suprised since one of the major drawbacks that I have found with the BSD OSs is that they are often behind their linux counterparts in terms of Hardware support.

Actually I can install Windows in 15 minutes on my main PC, and Ubuntu installs in less actually. 

Also after looking at the FreeBSD Gnome pages on their website it seems a lot of things haven't been ported yet (NetworkManager being one of them) 

I wont ever use Windows on a machine of my own ever again and I can safely say my machines will be Linux based for quite some time until BSD gets it's act sorted out for desktop use. (It's awesome for servers, my friend uses it and highly recommends it.)

P.S I appreciate that BSD is sometimes a bit behind with hardware support but come on, a standard CD drive?

---

### Post by cardinals_fan on 2008-12-15
> **C!oud said:**
> lol Windows does not take 15 minutes to install, however NetBSD does ;). Even most linux distro do not install within fifteen minutes (personal experiences vary but Ubuntu has never been that fast for me). As for KDE that's only default on *BSDs such as PC-BSD and DesktopBSD but for others FreeBSD, NetBSD, OpenBSD, and DragonflyBSD GUI is not included in the installation and you can add gnome or xfce afterwords.

 As for your problem with your CD drive I'm not suprised since one of the major drawbacks that I have found with the BSD OSs is that they are often behind their linux counterparts in terms of Hardware support.
What?!  I've never seen a NetBSD install take more than 7 minutes... :confused:

---

### Post by kk0sse54 on 2008-12-15
> **cardinals_fan said:**
> What?!  I've never seen a NetBSD install take more than 7 minutes... :confused:

I was referencing to the original statement of installing Windows and Ubuntu in 15 minutes. For me it's all relative, I pop in the CD, start the installation, then go walk the dog around the block and when I'm back it's done. Doesn't get much better than that :)

---

