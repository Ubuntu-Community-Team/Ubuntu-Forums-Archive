---
title: "Old Computer Advice"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2006-06-29
Hello!  I have finally found a way to use Linux on a machine before I go to college (maybe)!  I have an old Gateway computer lying around that would be perfect, assuming Linux will work on it.

Here are the specs:
1386 Mb of free space
Windows 98 currently installd (I would like to keep this for my parents)
Intell Pentium II Processor - 333 mHz
160 Mb of RAM
Gateway Multi-function keyboard
Creative Sound Blaster Audio PCI 64v
ATI 3D Rage Pro AGP 2x 

Which version of Ubuntu, if any, will run on this computer?  What special measures must I take for a smooth install/use?  Thanks! O:)

---

### Post by minden on 2006-06-29
[http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by Darklighter137 on 2006-06-29
Will this work, even given the terrible graphics card and very limited space?

---

### Post by IYY on 2006-06-29
I'd try Xubuntu, and if you find it too slow, replace the window manager with IceWM or Fluxbox.

---

### Post by princemackenzie on 2006-06-29
[QUOTE=Darklighter137]Will this work, even given the terrible graphics card and very limited space?[/QUOTE]

That's really a tiny amount of free space, 1.4 GB.  I believe Ubuntu wants a minimum of 2 GB thereabouts.

I would investigate Damn Small Linux at [http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/").  I got DSL running on a 486 with a 5 GB HD and 64 MB of ram without a problem, and it had a truly ancient video card, even worse than that ATI you have referenced.

As for ubuntu, you could try a server install and then installing fluxbox or another lightweight WM, but I have a feeling that you'd use that free space up very quickly.

---

### Post by Darklighter137 on 2006-06-29
Hmm...  Will that be possible even though I have a Winmodem?  Is my Winmodem supported?  Are the files I need to get it working something I could burn on CD and take to the computer?  If not, are the files needed for chaning the window manager something I could burn onto a disk?

---

### Post by K.Mandla on 2006-06-29
[QUOTE=Darklighter137]Will this work, even given the terrible graphics card and very limited space?[/QUOTE]
It'll work, although it might be a little sluggish. It will definitely be usable. The weakest machine I ever put Xubuntu on was a 233Mhz 128Mb 2Gb laptop. It was a bit overburdened, but I blame that on the fact that it had only 2Mb of video memory. 

If Xubuntu proves still too laggy for you, check some of the stripped-down Ubuntu versions [in the wiki]("https://help.ubuntu.com/community/Installation/LowMemorySystems"). If you're willing to build from the ground up, you can get a spunky Ubuntu system running on some very old hardware. :smile:

---

### Post by Darklighter137 on 2006-06-29
[QUOTE=princemackenzie]That's really a tiny amount of free space, 1.4 GB.  I believe Ubuntu wants a minimum of 2 GB thereabouts.

I would investigate Damn Small Linux at [http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/").  I got DSL running on a 486 with a 5 GB HD and 64 MB of ram without a problem, and it had a truly ancient video card, even worse than that ATI you have referenced.

As for ubuntu, you could try a server install and then installing fluxbox or another lightweight WM, but I have a feeling that you'd use that free space up very quickly.[/QUOTE]

Wow....  Is Damn Small any good?  I was really hoping to support Ubuntu, but I will take whatever I can get...

---

### Post by princemackenzie on 2006-06-29
[QUOTE=Darklighter137]Hmm...  Will that be possible even though I have a Winmodem?  Is my Winmodem supported?  Are the files I need to get it working something I could burn on CD and take to the computer?  If not, are the files needed for chaning the window manager something I could burn onto a disk?[/QUOTE]

It depends on the type of winmodem... such issues could be messy, as there are some old winmodems that no drivers where ever written for, I believe... so you would need to do research regarding what modem you have and if drivers were created.  If they were, it could be something that is transferred over later, in theory.

---

### Post by princemackenzie on 2006-06-29
DSL is very mature and there is a lot of documentation and success stories surrounding it on the web.  There is even a GTK enabled version out there now which is a stunning 85 MB in size.  I would really consider it if ubuntu doesn't work.

As for support for a winmodem, I don't think there is any sort of GUI in DSL for that.  I don't know how to help you there.

---

### Post by x64Jimbo on 2006-06-29
Wait, you're going to college and they're going to make you use a modem??? Colleges should be hooked up on broadband nowadays.

---

### Post by K.Mandla on 2006-06-29
[QUOTE=x64Jimbo]Wait, you're going to college and they're going to make you use a modem??? Colleges should be hooked up on broadband nowadays.[/QUOTE]
Maybe the laptop only has a modem port? If so, look for a Xircom CardBus Ethernet 10/100+ Modem 56. That's what I used with my old, old laptops and never had a problem.

[http://search.ebay.com/Xircom-CardBus-Ethernet-10-100-Modem-56_W0QQfrppZ50QQfsopZ1QQmaxrecordsreturnedZ300QQsatitleZXircomQ20CardBusQ20EthernetQ2010Q2f100Q2bQ20ModemQ2056](http://search.ebay.com/Xircom-CardBus-Ethernet-10-100-Modem-56_W0QQfrppZ50QQfsopZ1QQmaxrecordsreturnedZ300QQsatitleZXircomQ20CardBusQ20EthernetQ2010Q2f100Q2bQ20ModemQ2056)

Definitely worth $4 plus shipping.

---

### Post by Darklighter137 on 2006-06-29
lol, my college is, but my home computers aren't, hence the problem.  Thanks for  all of the suggestions.  I'm going to install either Kubuntu or Ubuntu when I get my new computer, but I am looking for a Linux fix now. =P

---

### Post by K.Mandla on 2006-06-29
[QUOTE=Darklighter137]Wow....  Is Damn Small any good?  I was really hoping to support Ubuntu, but I will take whatever I can get...[/QUOTE]
DSL is all right, but personally I like Ubuntu over DSL. I started with Ubuntu and DSL feels ... restrictive by comparison. :rolleyes:

---

### Post by princemackenzie on 2006-06-29
[QUOTE=K.Mandla]DSL is all right, but personally I like Ubuntu over DSL. I started with Ubuntu and DSL feels ... restrictive by comparison. :rolleyes:[/QUOTE]

Of course is restrictive, because its meant for restrictive systems :wink: 

A similar complaint would be saying your bicycle is restrictive because it doesn't seat 4 comfortably... it wasn't designed to, it was meant for one.  DSL was designed to give a functional desktop in a tiny package on lousy old hardware...

I have rescued a few computers with it already, and I recommend it to anyone trying to get some use out of fossilized machines.

---

### Post by minden on 2006-06-29
hmm 
you have that old computer
and your on dial up

heres my story
i was on dial up for a while
i also had an old computer
i had never had a computer that was up to date and was always using crap computers
i finally decided to build my own computer and i have DSL(as in internet)
to me
this is heaven
best $1800 i ever spent

just my 2 cents

---

### Post by blkish on 2006-06-29
[QUOTE=Darklighter137]Wow....  Is Damn Small any good?  I was really hoping to support Ubuntu, but I will take whatever I can get...[/QUOTE]

check out [ubuntulite]("http://www.ubuntulite.org")


blkish

---

### Post by minden on 2006-06-29
[QUOTE=blkish]check out [ubuntulite]("http://www.ubuntulite.org")


blkish[/QUOTE]

i couldnt find a direct link for ubuntulite but i found a torrent file
here
[http://linuxtracker.org/torrents-details.php?id=2233](http://linuxtracker.org/torrents-details.php?id=2233)

---

### Post by Pavilion on 2006-06-29
[QUOTE=princemackenzie]That's really a tiny amount of free space, 1.4 GB.  I believe Ubuntu wants a minimum of 2 GB thereabouts.

I would investigate Damn Small Linux at [http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/").  I got DSL running on a 486 with a 5 GB HD and 64 MB of ram without a problem, and it had a truly ancient video card, even worse than that ATI you have referenced.

As for ubuntu, you could try a server install and then installing fluxbox or another lightweight WM, but I have a feeling that you'd use that free space up very quickly.[/QUOTE]

YEP...I believe DAM SMALL LINUX is the way to go.:-\"

---

### Post by Pavilion on 2006-06-29
[QUOTE=K.Mandla]DSL is all right, but personally I like Ubuntu over DSL. I started with Ubuntu and DSL feels ... restrictive by comparison. :rolleyes:[/QUOTE]

No question Ubuntu is the way if you can make it work=D>

---

### Post by Pavilion on 2006-06-29
[QUOTE=princemackenzie]Of course is restrictive, because its meant for restrictive systems :wink: 

A similar complaint would be saying your bicycle is restrictive because it doesn't seat 4 comfortably... it wasn't designed to, it was meant for one.  DSL was designed to give a functional desktop in a tiny package on lousy old hardware...

I have rescued a few computers with it already, and I recommend it to anyone trying to get some use out of fossilized machines.[/QUOTE]

DSL is great for what it's designed for.  But, of course, it's not in the same league as Ubuntu:D

---

### Post by Pavilion on 2006-06-29
[QUOTE=minden]hmm 
you have that old computer
and your on dial up

heres my story
i was on dial up for a while
i also had an old computer
i had never had a computer that was up to date and was always using crap computers
i finally decided to build my own computer and i have DSL(as in internet)
to me
this is heaven
best $1800 i ever spent

just my 2 cents[/QUOTE]

Apparently this post was taken out of context.  My intent being simply to agree with Minden and his general statement: A new computer would serve a college student better.   Sorry Minden didn't mean it in the way you took it, however, I can see now how it could had been taken out of context.

---

### Post by az on 2006-06-29
[QUOTE=Darklighter137]Will this work, even given the terrible graphics card and very limited space?[/QUOTE]
The terrible graphics card has no bearing on 2D performace. It would just not do 1600x1200 resolution.  With 4 megs of video ram, you will do 1024x768 at 16-bit color, which is great. 

I think the space requirements for xubuntu are too big for your hard drive, and that's not even considering that you want to dual-boot with windows 98.

You can install aminimal system that takes up about 600 megs of space.  You would have to either use ubuntu-lite or install a base server system using the alternate cd and then just install a lean desktop.

You would enable universe and

sudo apt-get install x-window-system-core wdm icewm menu mozilla-firefox synaptic xterm

---

### Post by louieb on 2006-06-29
I have ubuntu up and running on a P1 200 mhz machine w/125 meg of memory.. Works just fine for surfing the internet, word processing and just playing around with Linux. And its more stable that the Win 98 operating system it replaced. For disk space I found and old 4 gig eide hard drive laying around. Don't know what type video card it has, the card was bought at a computer junkyard store. all I know about it is its pci and has 4meg of memory.:p    I've also had dam small installed on the same machine.
 I also have a P2 400 w/384 meg of memory. I Dual boot FC5 and win xp on that one. Installs on both machines when smooth the only problem I had was getting the P2 to dual boot but that was just a part of the learning process.
Of course both machine are noticeably slower that my pentium d 3.1 ghz. machine. but then  they are much faster that the pcs I had before that.

---

### Post by IYY on 2006-06-30
> Wow.... Is Damn Small any good? I was really hoping to support Ubuntu, but I will take whatever I can get...

It's obviously not as full-featured as Ubuntu, but it's a great distro. Also, it is Debian-based so it's very similar to Ubuntu.

---

### Post by bonzodog on 2006-07-02
I am going to say, use a Live CD. That way you won't have to bugger about with the partition with win98se on it, and you won't have to worry about HDD space.
Seems the most obvious option to me.

---

