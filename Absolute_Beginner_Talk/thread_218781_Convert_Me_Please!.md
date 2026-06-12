---
title: "Convert Me Please!"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Anthraxx on 2006-07-19
Hello all. I'm a somewhat experienced Windows user, but I *want* to be converted to Ubuntu. Could you guys help me out by showing me enough benefits to make me feel it's worthwhile spending a couple of days backing up, reformatting, configuring ect.? Some of my main concerns include:

Can I get iTunes to run, and be able to synch my iPod?
Can I get µTorrent to run, or will I need Azureus?
In either case, would I be able to have XP and Ubuntu downloading the same files, writing to the same files?
When using Firefox, what changes would I notice compared to using it under XP?
How easily could I get files between XP and Ubuntu?

P.S. I'm a gamer, but I'm totaly down with using XP for gaming, but I'd like to be able to do everything else with Ubuntu.

Thanks.

---

### Post by orb9220 on 2006-07-19
Well for the itunes to run don't think so? maybe others amorak is an great alternative for mp3 devices,and has great features like browse your collection by album playlist,lyrics,wiki lookup etc,,

Yes uTorrent or in my case I use Bitcomet thru wine which will install and run many windows app I even use dvdshrink for ripping and compressing my dvd movies.

The only way utorrent ot work on same directory like Torrents folder would 
be to have it on a partition that is fat32 then my ubuntu or xp can read and write to it.

I now only have a minimal install of xp for emergencies with wifi in case i break something in ubuntu while I learn and of course games but that is about the only reason.

Havn't booted into xp fer a couple of weeks anyway.

My layout is first hd 10gig partion for xp
    second partition  42 gig for root /
    third              1 gig for linux swap

    second hd         112GB fat32

setup works well for me.
Good luck

---

### Post by aysiu on 2006-07-19
> **Anthraxx said:**
> 
Can I get iTunes to run, and be able to synch my iPod? No iTunes. Yes, syncing the iPod. I've heard Banshee is good for this. AmaroK and Gtkpod are worth checking out, too. > Can I get µTorrent to run, or will I need Azureus? I don't know what that is, but Ubuntu comes with a Bittorrent client installed. It's not that difficult to install Azureus, though. > In either case, would I be able to have XP and Ubuntu downloading the same files, writing to the same files? Yes. I would recommend putting everything on Ext3 and using [http://www.fs-driver.org](http://www.fs-driver.org) to access those files from XP. > When using Firefox, what changes would I notice compared to using it under XP? The differences are minimal. If you want to jump to the third tab, you press Alt-3 instead of Control-3. If you want to click to highlight the address bar, you have to click twice (I prefer Control-L myself, as I find clicking inefficient), and if you accidentally drag a link, you'll see it actually drag. > How easily could I get files between XP and Ubuntu? Well, if you do what I suggested earlier, quite easily. Otherwise, you can follow this tutorial to do it the other way around: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Kobalt on 2006-07-19
Install Ubuntu, you'll get 70 virgins when you reach paradise ;)

---

### Post by FrancoNero on 2006-07-19
only 70? pah, I guess I stick with m$ then ;-)))

---

### Post by JerMe on 2006-07-19
> **Anthraxx said:**
> Hello all. I'm a somewhat experienced Windows user, but I *want* to be converted to Ubuntu. Could you guys help me out by showing me enough benefits to make me feel it's worthwhile spending a couple of days backing up, reformatting, configuring ect.? Some of my main concerns include:

Can I get iTunes to run, and be able to synch my iPod?
Can I get µTorrent to run, or will I need Azureus?
In either case, would I be able to have XP and Ubuntu downloading the same files, writing to the same files?
When using Firefox, what changes would I notice compared to using it under XP?
How easily could I get files between XP and Ubuntu?

P.S. I'm a gamer, but I'm totaly down with using XP for gaming, but I'd like to be able to do everything else with Ubuntu.

Thanks.

1. You can sync your iPod in Linux. There are a series of iPod applications that you can use in lieu of iTunes, such as GtkPod Banshee, and AmaroK.  In my experience, it's difficult to use both iTunes and GtkPod to manage a single iPod - meaning pick iTunes, or GtkPod.  Or, you can use CrossoverOffice to use the Windows version of iTunes, in Linux (for $40.)

2. uTorrent is a closed source Windows application.  IMHO it's the best torrent app out there, just not available for Linux (not yet at least.)  I'd stay away from Azureus.  There's a lot of linux torrent apps around, I personally use a commandline torrent app called rtorrent.

3. You can write to your NTFS formatted Windows partition with something called NTFS-3G.  It's still considered beta, but lots of people are using it (myself included).  Conversely, when you're booted in Windows, there is a driver called EXT2IFS ([http://www.fs-driver.org](http://www.fs-driver.org)) which will let you write to your Linux partitions from Windows.

4.  Firefox in Linux?  Instead of Tools > Preferences, you click Edit > Preferences.  ;)

5.  To share files between Linux and Windows... see #3.  OR, you can format a partition as FAT.  Linux can read and write to FAT partitions without special drivers.


Why Linux?  For starters, no more WGA crap.  Anti-virus and software firewall protection isn't as essential as it is in Windows.  Software is free - as in freedom, and in most cases, free as in beer (no $$$).  A lot of the native linux software is better than their Windows counterparts.  If you need those Windows programs, you can most likely run them under Wine ("Wine is Not an Emulator").

Why Ubuntu?  This distribution of Linux is EXTREMELY easy to use.  Pop the Ubuntu CD in, answer a few questions, and you're done.  The CD in most cases will autodect all your hardware, and when you reboot a few minutes later, you'll have a working system.  Then you pay a visit to ubuntuguide.org, the Ubuntu Wiki, or here on the forums to get everything else you need.  A good starting place would be EasyUbuntu.

There are tons of reasons to switch over from XP, or at least to dual-boot and spend most of your computing time in Linux.  I dual-boot Windows and Linux (Ubuntu, Kubuntu, Gentoo), but spend maybe 80%-90% in Linux.

Switch over, you know you want to. ;)

---

### Post by adam.tropics on 2006-07-19
Getting Ubuntu/Linux up and running, and finishining up with an OS that does what you want, how you want it done, can be hugely satisfying, and with Ubuntu, relitively painless. 

Kobalt: those 70 virgins....can we order those with the shipit cds!!

---

### Post by x64Jimbo on 2006-07-19
I've switched to using Linux for all but a couple games. I still keep my Windows partition around so that I can play C&C, but that's about it, and I think my new video card may enable me to play it through Wine anyway. ;)
I really highly recommend Kubuntu for ex-windows users. I find it more similar to Windows and a lot less of a transition that Gnome is, but that's my opinion. 
I recommend taking a look at superkaramba. It's a great widget app that will put all kinds of cool widgets on your desktop like a weather monitor and system monitor, among others. (K)ubuntu is the best Linux distro I've tried to date, and I've tried quite a few of them.

---

### Post by kigina on 2006-07-19
hmm

---

### Post by Kobalt on 2006-07-19
> **adam.tropics said:**
> 
Kobalt: those 70 virgins....can we order those with the shipit cds!!

I'll email Mark S. about that ;)
I can almost picture the "Edgy-virgin delivery thread" in october !

---

### Post by x64Jimbo on 2006-07-19
> **kigina said:**
> [*deleted*](*deleted*)
I know you're just kidding and everything, but religion and the Internet don't mix. Even joking about it is a pretty surefire way to start a flame war.

---

### Post by richbarna on 2006-07-19
Hi, I use ktorrent for torrents and once it is up and running it's ok. Azureas ran slow for me. Also, I have heard that uTorrent runs under Wine (let's you run "some" windows programs).
For sharing files between windows and linux, a FAT32 "storage" partition is probably the best option.

Good luck.

---

### Post by kigina on 2006-07-19
> **x64Jimbo said:**
> I know you're just kidding and everything, but religion and the Internet don't mix. Even joking about it is a pretty surefire way to start a flame war.

im an atheist so i would just sit back and watch

---

### Post by Anthraxx on 2006-07-19
Wow, thats a lot of info. If where I was when I started this topic, and installing Ubuntu is 100, then right now I'm 60. Two more things came up, though:

With that Ext2 program, could my unenlightend (XP using) friends be able to access files on an Ext2 partition across a LAN?

With Firefox, I was more wondering if Flash & streming videos would work properly, as I heard they could be troublesome.

Also, what kind of low to mid level music/video transcoding software is availible on Ubuntu, or can be WINE'd?

---

### Post by richbarna on 2006-07-19
> Wow, thats a lot of info. If where I was when I started this topic, and installing Ubuntu is 100, then right now I'm 60. Two more things came up, though:

With that Ext2 program, could my unenlightend (XP using) friends be able to access files on an Ext2 partition across a LAN? **No need, you can share files from Linux to Windows with Samba**

>  With Firefox, I was more wondering if Flash & streming videos would work properly, as I heard they could be troublesome. **Yes you can use them, as long as the website hasn't upgraded to Flash 8,9 (should be available for linux 2007) Take a look at [Automatix]("http://ubuntuforums.org/showthread.php?t=190025")**

>  Also, what kind of low to mid level music/video transcoding software is availible on Ubuntu, or can be WINE'd? [B]Not sure on this one, take a look here :- 
[/B][http://www.linuxrsp.ru/win-lin-soft/table-eng.html#41](http://www.linuxrsp.ru/win-lin-soft/table-eng.html#41)

---

### Post by darkowl on 2006-07-19
1 advice !
Delete your windows partition and enjoy with ubuntu ! :cool:

---

### Post by Sonic Alpha on 2006-07-19
[This site]("http://www.getgnulinux.org/"), has some valid arguments.

Personally, I have a dual boot system (XP and Ubuntu).  However, I'm finding I spend more and more time in Ubuntu than Windows.  It's probably best to start this way, just incase anything goes wrong and you need to get back online to ask for help :)

Download the Desktop CD, run it live, and try Ubuntu for yourself :)

---

### Post by Anthraxx on 2006-07-19
A guy I talked to, family friend, said that the iTune's performance in Crossover Office sucked, but then again he hates the penguin.

How do the Linux music players compare to iTunes in the music management/organisation department? I realy like the control iTunes gives.

---

### Post by Brunellus on 2006-07-19
AmaroK is generally thought to be the rival (and, by some, the better) music indexing/organizing app for Linux.  

I happen to like Rhythmbox.  

That said, I've never run iTunes, ever (surprised?)

As someone else noted, it's probably better for you to start off dual-booting, but having Ubuntu boot as the 'default' operating system.  My main computer at home dual-boots Windows XP and Ubuntu, but I haven't booted into WinXP in at least eight months.

---

### Post by aysiu on 2006-07-19
I'd go one step further on that even--start off with just the live (Desktop) CD before installing any kind of dual-boot. Play around with the live CD for a week or two.

---

### Post by Brunellus on 2006-07-19
> **aysiu said:**
> I'd go one step further on that even--start off with just the live (Desktop) CD before installing any kind of dual-boot. Play around with the live CD for a week or two.
Good advice if you really just want to look at the interface.  But be aware that the installed system is still better...especially when you get around to adding support for non-Free codecs (mpeg, for instance) and other non-Free goodies (flashplayer, java)

---

### Post by Kobalt on 2006-07-19
I have an iPod, which I use with gtkpod, and it's been really easier to get to work than with windoze... And to play music I really like Rythmbox. I've tried amaroK : I liked it but what I like about rythmbox is it's good graphical integration with my desktop, and it's speed and efficiency. 
Follow aysiu good advice (as you may always do) : start with a LiveCD first... 

Cheers !

---

### Post by avtolle on 2006-07-19
I strongly second Aysiu's recommendation. That is what I did w/Mac OS9, and after getting comfortable w/Breezy, totally went to Ubuntu Linux.

---

### Post by Anthraxx on 2006-07-19
I got the Live CD, have been playing with it, suitibly impressed, but it seems too limited when you can't access any of the files on my HDD, so I'm gonna go for the install. Now here's the part where I sound like a total noob. I do want to get into the whole command liney, script writey thing that Linux has, making the OS what I want, ect. but not until I'm sure I'm going to stay with Linux, and when I'm used to it, more migrated ect.

---

### Post by aysiu on 2006-07-19
You can access the files on you hard drive with the live CD. You may need to learn a command or two--no biggie.

Most likely this will get your hard drive mounted: ```
sudo mkdir /windows
sudo mount -t ntfs /dev/hda1 /windows -o nls=utf8,umask=0222
```

---

### Post by Anthraxx on 2006-07-20
Well as per your advice, I've been playing 'round with the live CD, but can't connect to the 'net. I started a thread for it [here]("http://www.ubuntuforums.org/showthread.php?t=218796").

I think I'll wait 'till I can at least connect to the 'net before I install it.

P.S. That was an oh-so-subtle hint to help me if you are so inclined. Thanks.

---

### Post by Frank Golden on 2006-07-20
> **Kobalt said:**
> Install Ubuntu, you'll get 70 virgins when you reach paradise ;)Is that virgins or Virginians.?

---

### Post by JerMe on 2006-07-20
> **Anthraxx said:**
> Well as per your advice, I've been playing 'round with the live CD, but can't connect to the 'net. I started a thread for it [here]("http://www.ubuntuforums.org/showthread.php?t=218796").

I think I'll wait 'till I can at least connect to the 'net before I install it.

P.S. That was an oh-so-subtle hint to help me if you are so inclined. Thanks.

Applications > Accessories > Terminal

What's the output of [FONT="Courier New"]**lspci**[/FONT]?

---

### Post by 3rdalbum on 2006-07-20
Agreed with above poster. Any Flash 8 or Flash 9 content that you can't run natively on Linux can be run through Firefox on WINE.

And DEFINATELY dual-boot, even if it's only to symlink the Windows DLLs into your WINE folder. :-)

AmaroK is known as the best music organiser in Linux. Most people would say that it's better than iTunes for that kind of thing. It's a bit heavy, but I assume you've got a recent machine for the gaming so it shouldn't matter. AmaroK is a KDE program, which means that when you download it, it will also download and install parts of the K Desktop Environment. This isn't a problem.

If your needs are more modest, you could use the included Rhythmbox program, or use a beta Linux version of Songbird, or try Exaile (which I like!).

As you've probably already heard, when you want to install programs on Ubuntu, you go to the Synaptic program, which downloads and installs everything you need for that program automatically, while you get on with work (or play :-)

---

### Post by Kobalt on 2006-07-20
> **Frank Golden said:**
> Is that virgins or Virginians.?

Virgins :) You would have to explain me the benefit of receiving 70 inhabitants of Virginia :rolleyes:

---

### Post by crystal on 2006-07-20
> You would have to explain me the benefit of receiving 70 inhabitants of Virginia
Revenue from taxes :)

---

### Post by adam.tropics on 2006-07-20
> **Kobalt said:**
> Virgins :) You would have to explain me the benefit of receiving 70 inhabitants of Virginia :rolleyes:

Off topic, sorry......Cheap tobacco:twisted: (plus apparently, Virginia has 'tax holidays'.....lucky lucky people!

---

### Post by Kobalt on 2006-07-20
lol

---

### Post by FuzZy2006 on 2006-07-20
Wow, you really want to convert this guy. Well, Ubuntu is better than windows at internet, media, and all the stuff, but it doesn't play all the windows games -- there are really great native linux games (nexuiz, legends, planeshift and many others) -- anyway, even with cedega and wine you won't be able to play all the windows games on windows so my advice is to keep windows installed as long as you are a gamer or maybe, one day, all the windows games will be playable on linux :mrgreen:

---

### Post by Anthraxx on 2006-07-20
[QUOTE=Terminal]0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I /O Controller (rev 04)

0000:00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL PCI Express Roo t Port (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High De finition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P CI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P CI Express Port 2 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P CI Express Port 3 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P CI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface  Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family ) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Contr oller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]
0000:01:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PC IE)] Secondary
0000:06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 V E (LOM) Ethernet Controller (rev 01)
[/QUOTE]
This is what I get when I type lspci into the Terminal.

---

### Post by dimatrod on 2006-07-22
I've found that the best way to convert from an OS to another is doing it the hard way.  Forget there's dual boot.  I have gone through it 3 times though, but this last time I seriously proposed to myself I would NOT turn back to windows, and I haven't, and now I'm rather impressed what I'm doing in Linux that I couldn't do in XP after 15 years of xpirience and only 2 months in Linux.

I've also found the need for WINE almost nil.  You can find everything you can for windows for linux.  Of course, there's no uTorrent, but rTorrent and Transmission are both quite nice, and you can create torrents with the plethora of torrent makers out there (I particularly fancy this CLI one named createtorrent).  I also would recommend you do not do automatix the first time.  I find another good thing (which might be also bad) is to try to do something aiming really high, say Xgl/Compiz (eye-candy), and if you break it, then get a laptop or something and start figuring out how to fix it.  After breaking it various times, and fixing them, you will become really expirienced in linux quite fast.  Believe me, I didn't listen to my Linux-geek friend the first time that this was the best way, nor the second, but when I figured things by myself, I felt right at home while using linux.

---

### Post by Anthraxx on 2006-08-11
I'm still having major trouble connecting to the 'net. I followed [ these ]("http://www.ubuntuforums.org/showpost.php?p=1286987&postcount=1") instructions, but I can't reboot on the live CD and the stuff about commenting out /etc/dhcp3/dhclient-script didn't seem to match up with what was actualy there.](*,)

---

### Post by JerMe on 2006-08-12
> **dimatrod said:**
> You can find everything you can for windows for linux.  Of course, there's no uTorrent...

Whaddya mean there's no uTorrent?
[http://www.ubuntuforums.org/showthread.php?t=191161](http://www.ubuntuforums.org/showthread.php?t=191161)

Native linux uTorrent, no.  Wine'd out uTorrent, yes. ;)

---

### Post by powder on 2006-08-12
> **JerMe said:**
> Whaddya mean there's no uTorrent?
[http://www.ubuntuforums.org/showthread.php?t=191161](http://www.ubuntuforums.org/showthread.php?t=191161)

Native linux uTorrent, no.  Wine'd out uTorrent, yes. ;)

Alcoholic! :twisted:

---

### Post by JerMe on 2006-08-12
I only do the Wine when I need the occasional linux ISO... I will say that I'm hooked on Linux. :)

---

