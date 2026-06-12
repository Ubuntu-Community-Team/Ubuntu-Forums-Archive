---
title: "Questions - Need help to migrate to Ubuntu 6.10 from Windows XP Pro"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by kenthomson799 on 2006-10-29
[FONT="Times New Roman"][SIZE="3"]Namaste,

              I heard that ubuntu forums are really newbie friendly so here i shall try to explain my questions in-detail in hope of getting some really good in-depth answers.
             I am a 'power' Windows User, who is at the computer for almost 10HRS a day. That means i can format my Windows machine, take care of the 'services', know basic Java Programming, etc, etc. I never tried Linux. But since last month i tried 'embedded DSL in qemu', Knoppix live CD, and now i am planning to migrate to Ubuntu 6.10. Here are my questions:

Do note that currently i only have windows XP Pro installed on C: drive, no other OS whatsoever.

Question-1(Q1)
This is my HDD. Total = 40GB, (PATA-7200rpm)
C: drive 10GB NTFS (running Windows XP Pro, recently formatted)
D: drive 30GB NTFS (My Data, Windows Programs, Movies)

So naturally i dont have any seperate partition for ubuntu. i know that it "shrinks" the windows partition to make room for itself. But, i want to take care of my disks myself. So i want to before-hand partition my HDD, through Windows before booting into Ubuntu. I would like to have
C: Drive NTFS for Widows (10GB as it is)
D: Drive (any file system) for Linux + Windows Programs (28-30GB, depending upon the last swap partition).
E: Drive, for swap (i have 512MB (main) 400Mhz RAM, and 128MB Dedicated GPU RAM on a nvidia 5200 FX). How much space should i allocate to swap?

Is there a way to shrink my current partitions through Windows and make them ready for Linux, or using some freeware, without loosing the current data on them?

Now my question is, what file system should i use for D: drive. I know that Linux reads a whole bunch of filesystems. But i dont know what are the advantages of one filesystem (maybe ext3) over say something else (like vfat). What i want is easy management, so a partition which windows can read would be fine, but not necessary, (becuase on D drive there are going to be Windows Programs + Movies + Data + ofcourse, Linux). You may suggest a filesystem for Linux which gives the most "performance". ( i mean theoretically vfat or NTFS should be OK for Linux, but which filesystem gives the "best" performance, and being compatible with a Windows OS, would be a nice touch but NOT a necessity.)

Q-2) I run a wonderful program called "FreeRAM XP Pro". Which frees my RAM from time to time. As i am a heavy multi-tasker, my RAM gets bloated. So how would i run something like this on Ubuntu to free my RAM? Moreover i use 'msconfig' in windows to control the Windows Services, and the Programs that automatically start at Startup. All this is done to achieve maximum performace from my machine. How would i control the programs that start at startup automatically and the "services" that run in background in Ubuntu 6.10? Is there something like a GUI "Task Manager" in Ubuntu?

Q-3) I am going to do a fresh install of Ubuntu 6.10 on my AMD Athlon 2600 XP+ with a nvidia FX 5200-Graphics Card. Some users have problems installing Ubuntu 6.10 with nvidia cards. So should i install ubuntu on my machine? Will there by any problems? And what is the 'right' method to do it?

Q-4) Moreover as i am a Power Windows user, so  i would also like to be a Power Linux user, can you point me to some 'free' guide(s) on the net about using Linux completely from the shell or the command line? It should be concise yet in-depth, and ofcourse newbie friendly otherwise i shall get lost within the commands.

Q-5) Moreover i downloaded the Desktop-i386-Ubuntu 6.10 ISO. Can i install it somehow without burning a disk? I would have to take my HDD to a friend's place for burning a CD, as i dont have a CD-Writer. Could you suggest some other way except Shipit? ;-)

Someone told me you can "netboot" without the needing of a CD. But that was it. I dont know what netboot is. Moreover i am having a stand-alone HomePC which is directly connected to the Internet using ADSL PPPOE. I dont have any other computer. Do you still think netboot is possible. If yes, please outline the steps for me, and i would be highly grateful.

Q-6) I want to have all those 3D Desktop effects + wobbly and transperent windows on Ubuntu. But are they incompatible with some programs? Are they experimental or full-fledged and ready to be used by the end user? Moreover what is beryl? or XGL? Can i turn them-off, if they start behaving irresponsibly and return to the normal Ubuntu Look easily?

Q-7) I heard people saying Automatix is bad? Is it safe to use on Ubuntu 6.10 or does it "hurt" Ubuntu more that it does good?

Q-8) Moreover i use the following programs on my Windows machine, are there equivalent "other" progams that i could use on Linux as replacements? If no, how 'bad' are the Linux programs as compared to their professional counterparts? And as a last resort, Is Wine or Some Windows emulator practical or effecient? or simply more of a pain?
List of Programs i use on Windows of whom i need replacement for Linux:
3DS MAX 9.0
CorelDraw 13
Photoshop CS2
Winamp (for listening to shoutcast and AOL (wtih XM) radio)
Avast antivirus
Zone Alarm Firewall

Q-9) Can i run Google Desktop on Linux?
I run an offline Program for Dictionary work called WordWeb. I need these dictionary programs to be absolutely fast and responsive, so connecting to internet to retrieve definitions is not an option. Can i run a good freeware Like WordWeb (see [www.wordweb.info](www.wordweb.info))which gives Synonyms, definitions, usage, root, etc on Linux?

That is all, thank you for taking the time to go through my queries. I could really appreciate some detailed answers, and you may as well suggest some Links on the web to which i can refer to, for my questions.

Thank you for your time and effort,
Namaste,
Ken[/SIZE][/FONT]

-----------------
UPDATE OCTOBER 31
-----------------

ok, so...i am having a nvidia fx 5200 128MB, graphics card, with a VGA output to which my current CRT is connected. I dont have any other output on my graphics card, but i do have the (defualt output) of the motherboard (which is currently empty), Now my question is. Can i make two monitors work like this: One on the Graphic cards VGA, and the other on the Motherboards VGA?

If no, this is the second option. I have a REALLY REALLY OLD PCI graphics card, which has a VGA output. Is it possible to insert that ancient PCI card on my motherboard, and than have one monitor plugged into the Graphic card's VGA, and the other one in the *ancient* PCI's VGA output?"
----------------------------------------
END OF ORIGINAL QUESTION
-----------------------------------------

At this point can you answer this question:
1)Will one monitor on Motherboard's VGA and one on Graphic card's VGA would work?
OR
will one monitor on the (ancient) PCI card's VGA, and the other one on Graphic card's VGA would work?

I am a little reluctant to use the PCI card, becuase it is really old, I found it in the attic. It is manufactured by some company called "Ali-cat". And i dont even know whether it works or not.

Thank you for your time,
Namaste,
Ken

---

### Post by tortus on 2006-10-29
Since no one else has bitten, I figured I'll take a stab at your questions. I'm ripe new to Ubuntu, and haven't really used linux in about 3 years, but it was my sole operating system for many years, and I've used many distributions.

There are many partition manager programs out there, the most well known for Windows is probably Partition Magic. It is not free. But Ubuntu's installer -- like most linux installers -- includes a full fledged partition program, and you can always boot into your computer with a live cd or something and use fdisk if you want to be real hardcore about it.

If you want a filesystem that both Linux and Windows can use, ehhhhh ... unless some big changes have happened here recently, this won't really work. You can use FAT in Linux, but it's missing a lot of features that a modern filesystem should have that you'd really, really want in Linux, such as file permissions. You can use ext3 (the main filesystem of linux) in Windows with a driver or at the very least a program that gives you basic access to an ext3 partition, but again not really ideally. If you really want a partition both OSes can see, I'd recommend making a small "sharing" partition that's just a few gigs or so. The sole intent to "drop off" files from one OS to the other.

Stuff on the web for becoming a "Linux power user"? Yeesh, there is more information out there then you'll ever know what to do with. Try the Linux documentation project

[http://www.tldp.org/](http://www.tldp.org/)

As a great starting point. For command line stuff, try reading some of their guides

[http://www.tldp.org/guides.html](http://www.tldp.org/guides.html)

Such as 
Introduction to Linux - A Hands on Guide
GNU/Linux Command-Line Tools Summary
Bash Guide for Beginners

btw, bash is a shell, the linux/unix equivalent of cmd.exe and command.exe in Windows. There are other shells as well, but bash is the most popular in the linux world.


Linux equivalents to your programs, let's see...

Photoshop CS2 -- you will probably hate it at first, but the Gimp is all you've really got. It has no CMYK support, but then if you are a print based graphic designer then linux is NOT the OS for you, at all :) It's a decent photoshop clone. Once you get used to the interface you find it's all pretty much there: layers, channels, powerful selection capabilities, support for just about all image formats, rgb and indexed color, you name it.


Winamp (for listening to shoutcast and AOL (wtih XM) radio) -- XMMS handles shoutcast just fine and is a great program, very winamp like. AOL with XM? Not so sure about that...

Avast antivirus -- you don't need antivirus, you really don't. Windows is the only OS where this crud is standard fare.

Zone Alarm Firewall -- built right into the kernel, and many many frontends and packages for setting it up and configuring it exist. The nice thing here is the linux firewall is not obtrusive and annoying like typical software Windows firewalls are.

---

### Post by Tom Brokaw on 2006-10-29
I'm newer to Linux than Tortus, but I went through some of the same things as you when I installed Dapper, so I'll try to help too.
> **kenthomson799 said:**
> [FONT="Times New Roman"][SIZE="3"]Namaste,

              I heard that ubuntu forums are really newbie friendly so here i shall try to explain my questions in-detail in hope of getting some really good in-depth answers.
             I am a 'power' Windows User, who is at the computer for almost 10HRS a day. That means i can format my Windows machine, take care of the 'services', know basic Java Programming, etc, etc. I never tried Linux. But since last month i tried 'embedded DSL in qemu', Knoppix live CD, and now i am planning to migrate to Ubuntu 6.10. Here are my questions:

Do note that currently i only have windows XP Pro installed on C: drive, no other OS whatsoever.

Question-1(Q1)
This is my HDD. Total = 40GB, (PATA-7200rpm)
C: drive 10GB NTFS (running Windows XP Pro, recently formatted)
D: drive 30GB NTFS (My Data, Windows Programs, Movies)

So naturally i dont have any seperate partition for ubuntu. i know that it "shrinks" the windows partition to make room for itself. But, i want to take care of my disks myself. So i want to before-hand partition my HDD, through Windows before booting into Ubuntu. I would like to have
C: Drive NTFS for Widows (10GB as it is)
D: Drive (any file system) for Linux + Windows Programs (28-30GB, depending upon the last swap partition).
E: Drive, for swap (i have 512MB (main) 400Mhz RAM, and 128MB Dedicated GPU RAM on a nvidia 5200 FX). How much space should i allocate to swap?
For the swap file, I believe at least 256, and 512 MB is recommended IIRC.
> Is there a way to shrink my current partitions through Windows and make them ready for Linux, or using some freeware, without loosing the current data on them?
As Tortus said, Partition Magic is probably your best bet.  However, I wouldn't shrink your XP partition beyond what it already is.  Since XP gets fragmented, more free space is better.  
> Now my question is, what file system should i use for D: drive. I know that Linux reads a whole bunch of filesystems. But i dont know what are the advantages of one filesystem (maybe ext3) over say something else (like vfat). What i want is easy management, so a partition which windows can read would be fine, but not necessary, (becuase on D drive there are going to be Windows Programs + Movies + Data + ofcourse, Linux). You may suggest a filesystem for Linux which gives the most "performance". ( i mean theoretically vfat or NTFS should be OK for Linux, but which filesystem gives the "best" performance, and being compatible with a Windows OS, would be a nice touch but NOT a necessity.)
I don't know which one gives the best performance.  ext2/3 doesn't get fragmented nearly as easily as NTFS does.  FAT32 can be read by both OSes, I think.  I used the ext2IFS driver with my dual-boot machine for a while.  I did have a problem, but I'm 99% sure it was because of my IDE controller card issues with drive size. (I have 6 IDE drives total, necessitating a card.)
> Q-2) I run a wonderful program called "FreeRAM XP Pro". Which frees my RAM from time to time. As i am a heavy multi-tasker, my RAM gets bloated. So how would i run something like this on Ubuntu to free my RAM? Moreover i use 'msconfig' in windows to control the Windows Services, and the Programs that automatically start at Startup. All this is done to achieve maximum performace from my machine. How would i control the programs that start at startup automatically and the "services" that run in background in Ubuntu 6.10? Is there something like a GUI "Task Manager" in Ubuntu?
There is a startup menu, I forget where exactly right now.  I think it's in System>Preferences>Startup.  It lets you add apps to run in the background.  Dunno about a ram-clearing program.  I'm skeptical about them anyway, personally.
> Q-3) I am going to do a fresh install of Ubuntu 6.10 on my AMD Athlon 2600 XP+ with a nvidia FX 5200-Graphics Card. Some users have problems installing Ubuntu 6.10 with nvidia cards. So should i install ubuntu on my machine? Will there by any problems? And what is the 'right' method to do it?
In my forum and net browsing, most of the things that I've read indicate that Nvidia has much better support than ATI for discrete cards.  I have an FX5900, and I had two problems: the first was that Ubuntu doesn't appear to support my preferred resolution, 1280x1024, out of the box.  The second was that the screen was "offset" about a half-inch on my LCD.  This could be a side-effect of my set up, where I have my XP machine and my dual-boot machine  going through a KVM switch.  In any case, the latter problem was fixed with the Nvidia drivers from Automatix, and the former problem was fixed by reconfiguring my xorg.conf file.
> Q-4) Moreover as i am a Power Windows user, so  i would also like to be a Power Linux user, can you point me to some 'free' guide(s) on the net about using Linux completely from the shell or the command line? It should be concise yet in-depth, and ofcourse newbie friendly otherwise i shall get lost within the commands.
[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)
> Q-5) Moreover i downloaded the Desktop-i386-Ubuntu 6.10 ISO. Can i install it somehow without burning a disk? I would have to take my HDD to a friend's place for burning a CD, as i dont have a CD-Writer. Could you suggest some other way except Shipit? ;-)
I seriously doubt it.  ISOs are created for use in a 32-bit environment.  You might see if Kinko's or similar will let you download and burn from there.
> Q-6) I want to have all those 3D Desktop effects + wobbly and transperent windows on Ubuntu. But are they incompatible with some programs? Are they experimental or full-fledged and ready to be used by the end user? Moreover what is beryl? or XGL? Can i turn them-off, if they start behaving irresponsibly and return to the normal Ubuntu Look easily?
They are not fully mature, and some people do have problems.  If you're after stability, I'd avoid them.
> Q-7) I heard people saying Automatix is bad? Is it safe to use on Ubuntu 6.10 or does it "hurt" Ubuntu more that it does good?
The main complaint I've heard is that Automatix makes it too easy.  All it does is groups a bunch of commonly used things (codecs, apps, etc) and make installing them a matter of several clicks.  

Some people think that this is similar to cutting the butterfly out of its cocoon; ie, if you can't learn to install an MP3 codec, maybe Linux isn't for you.  I tend to go the other way, myself.  Why make things harder?  It's good to learn, but if I can't do things I take for granted on my XP machine, I won't use my Linux box and will never learn.  It's an ongoing debate. I've used Automatix twice, I like.  I don't think it's "bad" for Linux at all, just what I've outlined above.
> Q-8) Moreover i use the following programs on my Windows machine, are there equivalent "other" progams that i could use on Linux as replacements? If no, how 'bad' are the Linux programs as compared to their professional counterparts? And as a last resort, Is Wine or Some Windows emulator practical or effecient? or simply more of a pain?
List of Programs i use on Windows of whom i need replacement for Linux:
3DS MAX 9.0
CorelDraw 13
Photoshop CS2
Winamp (for listening to shoutcast and AOL (wtih XM) radio)
Avast antivirus
Zone Alarm Firewall
What Tortus said.  There is ClamAV included with Automatix if you so desire (you can pick and choose with Automatix).  I've heard PS7 will work in WINE, but CS and CS2 will not.  Never tried myself.  I'm not real happy with The GIMP, but part of that is because I am used to PS.  So maybe I could make the same things with G as I could with PS, but I just don't know where the menus are.
> Q-9) Can i run Google Desktop on Linux?
I run an offline Program for Dictionary work called WordWeb. I need these dictionary programs to be absolutely fast and responsive, so connecting to internet to retrieve definitions is not an option. Can i run a good freeware Like WordWeb (see [www.wordweb.info](www.wordweb.info))which gives Synonyms, definitions, usage, root, etc on Linux?
Can't help with that one, sorry.
> That is all, thank you for taking the time to go through my queries. I could really appreciate some detailed answers, and you may as well suggest some Links on the web to which i can refer to, for my questions.
Click on Wiki at the top right there, and always remember, Google is your friend.  In fact, google has its own linux section, [http://www.google.com/linux](http://www.google.com/linux)
> Thank you for your time and effort,
Namaste,
Ken
Hope I helped.  I have a few suggestions for you, or maybe just one with several options.

I broke the GUI several times when I was first getting Dapper set up.  If I hadn't had a second computer/OS to come here and get help, I'd have been screwed.  Having another computer seriously decreased my stress level, because at the end of the day, I can always just reformat if I absolutely have to.

You might be able to find a decent 1 GHz, 512 RAM machine on your local Craigslist for ~$100, maybe.  A new computer is probably more than you want to spend, though.  Dual-booting can cause problems as well, and depending on how many programs you have on your D: partition, you may not have a whole lot of room on that drive anyway.

If I were you, I'd try to get a second hard drive.  Then I'd do one of two things: Clone your current install of Windows to it and install Ubuntu to it.  Then unplug your current hard drive and keep it in the computer as a backup.  The other option would be to install Ubuntu to the second hard drive.  The drawback is that you'd probably have to physically connect and disconnect drives when you wanted to switch OSes.

It's late, I hope that wasn't too incoherent.

---

### Post by jimmyk on 2006-10-29
I really think you want to steer clear of using the same partition for windows files and running linux, thats gonna end in tears.  You should create a separate partition for ubuntu, you can easily mount other partitions for easy access in ubuntu.

---

### Post by Perfect Storm on 2006-10-30
I would recommend you go with Ubuntu 6.04 (dapper) as Edgy is more like on the experimental level. Also you can get Dapper with shipit if you don't have a burner.

---

### Post by RudolfMDLT on 2006-10-30
Hi there!

Very Nice detailed post! :)

First waring, Don't install Edgy(6.10). Please stick to Ubuntu 6.06 Dapper Drake. You will want to download the Deskop live cd


Question-1(Q1)
> This is my HDD. Total = 40GB, (PATA-7200rpm)
C: drive 10GB NTFS (running Windows XP Pro, recently formatted)
D: drive 30GB NTFS (My Data, Windows Programs, Movies)
So that is your current standing machine... My geuss is buying another harddrive would be best. If you need to partition, leave C alone. XP is a monster and needs as much resource as you allow it. I would take about 10 - 15 GB on Drive D just to be safe.

Partition manager would be your best bet for partitioning, but if not then: 

How to partition. Insert the 6.06 live cd and boot it. Here you can play with ubuntu and screw around. When you feel it's time to install, double click the icon on the desktop and follow the instructions. I can't remember the exact procedure but a window will appear, Gparted - the Gnome partition manager(I forgot, before installing make sure that drive D is defragmented in windows). Here you can select what to chop up and how. No matter what you use to partition , create 3 partitions. 

1) 512mb for Swap(Using Swap fs)
2) +-6Gb for HOME (Using Ext2 or Ext3)
3) The rest for / (Uding Ext2 or Ext3)(the / is called root)

Here's why, Linux doesn't have a drive c and drive d, it has one folder called root(/) and from root ecerything runs. Drive2, your HOME directory drive will be on a seperate drive, but Ubuntu will make it apear to be part of one BIG file system. The reason for this is when you back up, Tar and Zip files are cumbersome, creating and image is a much easier way of backing up. It's also better practise to have your home directoy seperate.



> Is there a way to shrink my current partitions through Windows and make them ready for Linux, or using some freeware, without loosing the current data on them?

Yes - Partion magic - First defragment
> 
( i mean theoretically vfat or NTFS should be OK for Linux, but which filesystem gives the "best" performance, and being compatible with a Windows OS, would be a nice touch but NOT a necessity.)
Linux will NOT run on NTFS and cannot write to it either. You can mount windows drivers and read them though. I have a plugin for windows which will allow your windows system to read and write in linux, thus you can transfer files.

> 
Q-2) I run a wonderful program called "FreeRAM XP Pro". Which frees my RAM from time to time. As i am a heavy multi-tasker, my RAM gets bloated. So how would i run something like this on Ubuntu to free my RAM? Moreover i use 'msconfig' in windows to control the Windows Services, and the Programs that automatically start at Startup.

Linux is not a RAM Muncher though it will be easy to find an app for this. I would not suggest screwing around with Linux services. the Linux Architecture is nothing like window's. Ubuntu will nor munch unneccesary resources.

> Q-3) I am going to do a fresh install of Ubuntu 6.10 on my AMD Athlon 2600 XP+ with a nvidia FX 5200-Graphics Card. Some users have problems installing Ubuntu 6.10 with nvidia cards. So should i install ubuntu on my machine? Will there by any problems? And what is the 'right' method to do it?

DO NOT INSTALL VERSION 6.10. I'm shouting mearly screaming a warning! :) (just kidding) I'm running 6.10 and clean installs seem to work fine. 6.06 is much stabler and is supported for years to come. Also Nvidia cards should be installed auromaticaly in 6.06.

(The diffrences in 6.06 and 6.10 is very little)

> Q-4) Moreover as i am a Power Windows user, so  i would also like to be a Power Linux user, can you point me to some 'free' guide(s) on the net about using Linux completely from the shell or the command line? It should be concise yet in-depth, and ofcourse newbie friendly otherwise i shall get lost within the commands.

This is a very good page:

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

Though i think this is what you are looking for:

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)


> Q-5) Moreover i downloaded the Desktop-i386-Ubuntu 6.10 ISO. Can i install it somehow without burning a disk? I would have to take my HDD to a friend's place for burning a CD, as i dont have a CD-Writer. Could you suggest some other way except Shipit? ;-)

I'm sorry but you need to burn it. It is possible to do a network install but thats tricky. 

> Q-6) I want to have all those 3D Desktop effects + wobbly and transperent windows on Ubuntu. But are they incompatible with some programs? Are they experimental or full-fledged and ready to be used by the end user? Moreover what is beryl? or XGL? Can i turn them-off, if they start behaving irresponsibly and return to the normal Ubuntu Look easily?
These are nice to have but lets just get the system up and running first. Yes it will be possible to have them.

For Beryl, XGL and COmpiz and all other related things:

[http://en.wikipedia.org/wiki/XGL](http://en.wikipedia.org/wiki/XGL)
[http://en.wikipedia.org/wiki/Compiz](http://en.wikipedia.org/wiki/Compiz)
[http://en.wikipedia.org/wiki/Beryl_%28window_manager%29](http://en.wikipedia.org/wiki/Beryl_%28window_manager%29)

> Q-7) I heard people saying Automatix is bad? Is it safe to use on Ubuntu 6.10 or does it "hurt" Ubuntu more that it does good?

Again, 6.10 i won't use if i where you. See the orange link to sound issues in my post for in for on Automatix. It is a very good app for beginners but I would reccomend intalling some things by hand, ie, the terminal.


> Q-8) Moreover i use the following programs on my Windows machine, are there equivalent "other" progams that i could use on Linux as replacements? If no, how 'bad' are the Linux programs as compared to their professional counterparts? And as a last resort, Is Wine or Some Windows emulator practical or effecient? or simply more of a pain?
List of Programs i use on Windows of whom i need replacement for Linux:
3DS MAX 9.0 - [COLOR="Blue"]Don't now what this is[/COLOR]
CorelDraw 13 - [COLOR="blue"]The Gimp isn't bad once you get used to it[/COLOR]
Photoshop CS2 - [COLOR="blue"]The Gimp[/COLOR]
Winamp (for listening to shoutcast and AOL (wtih XM) radio) - [COLOR="blue"]There are lots of player out there, Anarok, Kaffine ect.[/COLOR]
Avast antivirus - [COLOR="blue"]You won't need this in Linux[/COLOR]
Zone Alarm Firewall - [COLOR="blue"]Firestarter - Not as pretty but just as effective[/COLOR]

> Q-9) Can i run Google Desktop on Linux?
I run an offline Program for Dictionary work called WordWeb. I need these dictionary programs to be absolutely fast and responsive, so connecting to internet to retrieve definitions is not an option. Can i run a good freeware Like WordWeb (see [www.wordweb.info](www.wordweb.info))which gives Synonyms, definitions, usage, root, etc on Linux?

I don't use anything like this. You should be able to run it in Wine though I have no idea.

> Namaste

what does this mean? Just curiose.

There's gonna be a lot of setting new things that are not in this post that you will discover and maybe have problems with. Really feel free to post about anthing no matter how stupid is may sound to you. All we on the Forum want is for you to run Ubuntu happily. I really urge you to get the 6.06 version of Ubuntu. Specifically the Desktop version.

As for guides:

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)
[http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/index.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/index.html)

This one was written by a forum member, 
[http://www.psychocats.net/](http://www.psychocats.net/)

Anyhow,

Hope this helps, post back if you have any problems,

Cheers,

Rudolf 

PS: I'm at Varsity and using IE so I can't check my spelling! Sorry! :mrgreen:

---

### Post by ezphilosophy on 2006-10-30
kenthomson799,

I, and most users here, think Ubuntu is awesome and love using it.  We more than welcome you to the community if you really want a go at it.  
However, based on your post, in my honest opinion, I don't think Ubuntu will be for you.  You seem to have specific needs and Windows seems to get it done for you.  As much as people trash it here, XP "gets it done" for a lot of users.

My best advice: read some posts by aysiu.  He has written some great stuff and will give you a better idea of what you would be getting into.

[Is Ubuntu for You?]("http://ubuntuforums.org/showthread.php?t=63315")

If you decide "yes", then Welcome!

If not, then refer to this thread before you make another post and good luck to you!
[URL="http://ubuntuforums.org/showthread.php?t=219243"]
All my favorite Linux desktop readiness threads...[/URL]

---

### Post by msandersen on 2006-10-30
> 3DS MAX 9.0
CorelDraw 13
For Max, I think your best bet is [Blender]("http://en.wikipedia.org/wiki/Blender_%28software%29"). Have a look at the movie [The Elephant's Dream]("http://www.elephantsdream.org/"), it was made with Blender on Ubuntu (and MacOSX). To get serious on it, you may need the very latest 2.42a (included in Ubuntu 6.10). Check out [the Gallery]("http://www.blender.org/cms/Gallery.55.0.html"). There are plenty of community forums, like [blendernation.com]("http://www.blendernation.com/"). More links [here]("http://blender3d.org/cms/Websites.7.0.html").
It also has a Game Engine plugin. But it takes some getting used to if you're used to Max. You may prefer to use Max on XP for that.

Corel - A long while since I've used it, but check out [Xara Xtreme]("http://www.xaraxtreme.org/"). Very much like Corel. It was recently opensourced for Linux, hence free, but is still in development. The original is for Windows and is commercial, so you can try out the Demo on Windows first. The other popular one (by virtue of lack of competition) is Inkscape. It specialises in the SVG (Scalable Vector Graphics) format developed by the W3C. Personally I'd go with Xara Xtreme, though still Beta. But then, so's Inkscape.

For sharing documents between Windows and Linux, I use a dedicated partition in ext3 with the [ext2IFS driver]("http://www.fs-driver.org/") for Windows installed (on Windows, obviously), which makes ext2/3 native to Windows (with some limitations, like Permissions, and it shows all dot-files which are hidden on Linux by default). You will have to remember not to hibernate when switching OSes though, or the shared partition/drive will not be available for safety.

And yes, I think it is possible to install from an ISO file. Everything including CDs are mounted to the root filesystem. You can mount the ISO so it appears like a CD. Search for "[mount ISO]("http://www.ubuntuforums.org/search.php?searchid=9316979")" or "[install ISO]("http://www.ubuntuforums.org/search.php?searchid=9317411")" or something like that, and you get posts like [this]("http://www.ubuntuforums.org/showthread.php?t=232686&highlight=mount+iso").  Also found [this one]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20CD-IMAGES"). Or maybe you can do a Netboot.
But seriously, who doesn't have a CD burner? Everyone needs to back up. Every hard drive will eventually go the way of the Dodo, taking your data with it.
I haven't tried installing this way though.

XGL/Compiz/Beryl etc is experimental and under heavy development, despite what some Linux magazines might make you think. Best way is to install it as a separate Session (I followed the [official instructions]("https://help.ubuntu.com/community/CompositeManager/Xgl") for Dapper, should be much the same for Edgy), so you won't be locked out if an update breaks it or there are program incompatibilities, which there are in particularly with some OpenGL apps/games. There are plenty of other guides specifically for Edgy; one guide is found [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL"). [Another guide]("http://doc.gwos.org/index.php/BerylOnEdgy"). And [here]("http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit").

One note on Automatix: I used it on Dapper. It installs some things in an unofficial way, eg it puts Azureus (p2p app) in /opt, and at the time it offered FireFox 1.5 when the official repo was 1.07, but also put it in /opt. That's fine, but when upgrading to Edgy, the officially-installed version (from the package manager) was upgraded to FF2.0, but there was a symlink (like a super-Shortcut) at /usr/bin/firefox which pointed to the unofficial version, so that was the one starting up. Changing this to point to the official version fixed this. I haven't tried Automatix under Edgy, I assume it has a way to update FireFox from its install, as it has for other software. 
Also, there was a bug in the way Azureus was set up, in that Azureus periodically checks for updates itself and downloads them. The permissions for Azureus wasn't set to allow Azureus to do this, so it got errors whenever it tried to update, which was the first thing it tried to do on first starting. An easy fix on the command line, if you know how (with *chmod g+w -R /opt/azureus* and *chown root:admin -R /opt/azureus*), but annoying. I reported it, but the maintainer doesn't consider it a bug and won't be fixed (I assume he doesn't use Azureus himself).
Another option is EasyUbuntu, from which Automatix forked. It focuses on the extra codecs etc, not on extra/updated software.
There was some discussion about providing an official way through Add/Remove Software to provide the same functionality as EasyUbuntu/Automatix, perhaps with its own category, through some metapackage or such which would install the extra codecs (but not DeCSS for legal reasons) provided the unofficial repos were enabled. I don't know what happened to that.

---

### Post by Perfect Storm on 2006-10-30
You can also get Maya but it's not free in any way.

---

### Post by msandersen on 2006-10-30
> **Artificial Intelligence said:**
> You can also get Maya but it's not free in any way.
*"in any way"* being the operative words. Maya is now owned by AutoDesk who make 3ds Max, so who knows their future plans.

---

### Post by maruchan on 2006-10-30
I generally don't recommend that Windows power users make a cold-turkey migration to Linux. I hope you have a working Windows system nearby because it's quite a shock to find out how different things are in Linux land. :) ("good" different, but still different...)

Q1: I think you need to purchase more storage space. What does "drive for Linux+Windows programs" mean?

Use ext3 filesystem.

Q-2) I run FRamXPPro in Windows too. I don't think you'll need it in Linux. 

> Moreover i use 'msconfig' in windows to control the Windows Services, and the Programs that automatically start at Startup.

You can control startup services easily in Linux too. Task manager can be accessed using Ctrl+Alt+Del on my system. I like to keep a little CPU meter (right-click on panel, click "add" then "system monitor") which you can click on to immediately see all running processes.

Q-3) NVidia is the better-supported brand. I have an FX-5500 and it's always worked great.

Q-4) There are a *lot* of guides like this. Many have been featured in the Linux/Unix section (under "Technology") at digg.com and that includes links to hundreds of free e-books, etc. Also, be sure to look at the HOWTOs posted here in the forums and ask questions if you want to know how things work.

Q-5) No CDWriter = contact the closest Linux user group or get on Craigslist and ask someone local to burn the CD for you. I once got a CD within a day this way ;)

I'm not sure how netboot works.

Q-6) You will be able to turn 3D FX off if necessary but on a starter Linux system these 3D effects would be my last priority. Get all your desktop apps installed first and make sure everything's peachy, then try it.

Q-7) Automatix is good :)

Q-8) You can always purchase a Crossover Office license and try running your favorite apps directly. You have a lot of options though.

3DS MAX 9.0 - No Linux port available, try here for others:
[http://linuxlinks.com/Software/Graphics/Modeling/](http://linuxlinks.com/Software/Graphics/Modeling/)
CorelDraw 13 - Try XaraXtreme or Inkscape...
Photoshop CS2 - Try GIMP, Pixie, Krita, etc.
Winamp (for listening to shoutcast and AOL (wtih XM) radio) - I like Songbird for this, but everyone has their own preference.
Avast antivirus - Not needed unless you can prove your Linux machine is a virus vector :D
Zone Alarm Firewall - Not needed

Q-9) I doubt Google Desktop will work - what features do you need? Desktop search? Use Beagle in Linux. Etc.

As for WordWeb, try running it in Wine or Crossover Office. There's a good chance it will work fine in Wine.

Also, don't forget about Java software when you are looking for replacements for your Windows apps. The JRE is available through Synaptic so you can use those apps too, like the one in my sig, or Freemind, etc.

4 8 15 16 23 42

---

### Post by maruchan on 2006-10-30
BTW for more detailed design apps discussion, please see this forum post:

"Designer Wants to Take the Plunge"

[http://www.linuxactionshow.com/forum/comments.php?DiscussionID=93&page=1](http://www.linuxactionshow.com/forum/comments.php?DiscussionID=93&page=1)

My nick is Circular there - feel free to ask any questions.

---

### Post by fishpie on 2006-10-30
>  Is there a way to shrink my current partitions through Windows and make them ready for Linux, or using some freeware, without loosing the current data on them?
The Ubuntu and Kubuntu installation CDs double as live CDs and, contain gparted and Qtparted respectively, which you should be able to use to resize your ntfs partition without installing linux, but do not use ubuntu dapper for this purpose as there is a very nasty [ bug.]("https://launchpad.net/distros/ubuntu/+source/gparted/+bug/48229") I think knoppix also contains qtparted so you could probably use that.

>  Now my question is, what file system should i use for D: drive. I know that Linux reads a whole bunch of filesystems. But i dont know what are the advantages of one filesystem (maybe ext3) over say something else (like vfat). What i want is easy management, so a partition which windows can read would be fine, but not necessary, (becuase on D drive there are going to be Windows Programs + Movies + Data + ofcourse, Linux). You may suggest a filesystem for Linux which gives the most "performance". ( i mean theoretically vfat or NTFS should be OK for Linux, but which filesystem gives the "best" performance, and being compatible with a Windows OS, would be a nice touch but NOT a necessity.)

ext3 is the default file system for ubuntu, and is a good all round performer, dependable, compatible with windows, and well supported. However, reiserfs has a reputation for being slightly faster, but has problems with large(several gigabytes) files. ext3 and the forthcoming ext4 seem to have a lot more developers working on them than reiserfs, and the difference in speed is likely to change with future development. reiserfs is developed by Hans Reiser's company namesys. The future of reiserfs is in doubt because Hans Reiser is in jail charged with murdering his wife.

> Q-6) I want to have all those 3D Desktop effects + wobbly and transperent windows on Ubuntu. But are they incompatible with some programs? Are they experimental or full-fledged and ready to be used by the end user? Moreover what is beryl? or XGL? Can i turn them-off, if they start behaving irresponsibly and return to the normal Ubuntu Look easily?
Beryl is a window manager and is similar to compiz. A lot of people seem to run compiz and beryl without any problems. Installing and removing software using the apt package manager and its GUI front ends is a dream compared to windows. If you properly configure apt, then there is no need to use automatix. apt will keep all your software consistent and up to date, and will allow you to remove packages easily. I'm sure there will be plenty of threads on this forum that explain how to enable the universe and multiverse repositorys. You may also want to enable the plf repository and  the repository for beryl, see the beryl website for details. It is more than worthwhile to take a few minutes to configure apt. 

> Q-8) Moreover i use the following programs on my Windows machine, are there equivalent "other" progams that i could use on Linux as replacements? If no, how 'bad' are the Linux programs as compared to their professional counterparts? And as a last resort, Is Wine or Some Windows emulator practical or effecient? or simply more of a pain?
List of Programs i use on Windows of whom i need replacement for Linux:
3DS MAX 9.0
CorelDraw 13
Photoshop CS2

Krita is very good for photo editing and is much more user-friendly than the gimp. 

> Q-9) Can i run Google Desktop on Linux?
I run an offline Program for Dictionary work called WordWeb. I need these dictionary programs to be absolutely fast and responsive, so connecting to internet to retrieve definitions is not an option. Can i run a good freeware Like WordWeb (see [www.wordweb.info)which](www.wordweb.info)which) gives Synonyms, definitions, usage, root, etc on Linux?


the wordnet tab in Kthesaurus provides good dictionary definitions, synonyms, antonyms. meronym, holonyms...

---

### Post by msandersen on 2006-10-30
For 3D, there's also [POV-Ray]("http://www.povray.org/") ([Wikipedia]("http://en.wikipedia.org/wiki/POV-Ray")), [YafRay]("http://www.yafray.org/") ([Wikipedia]("http://en.wikipedia.org/wiki/YafRay")), and [Wings 3D]("http://www.wings3d.com/") ([Wikipedia]("http://en.wikipedia.org/wiki/Wings3D")).
Mark Shuttleworth, the Ubuntu founder, used POV-Ray on the International Space Station when he was a space tourist there to stress-test some laptops in space (zero-g affects cooling and radiation could affect batteries). The story behind it is [here]("http://www.oyonale.com/iss/english/makingof.htm").

---

### Post by RudolfMDLT on 2006-10-31
msandersen,

Wow, I didn't know the open source guys had that ability! Thanks! :) An open Movie, who would have thought?

---

### Post by msandersen on 2006-10-31
> **RudolfMDLT said:**
> msandersen,

Wow, I didn't know the open source guys had that ability! Thanks! :) An open Movie, who would have thought?
Yeah, The Orange Project was a project to showcase the abilities of Blender. They got some private funding, and the Dutch government put up the other half. For that, they could buy equipment and hire some of the best Blender artists for the duration of the project. As a direct result of the project, Blender got a major update in response to the animator's requests. It's all in the *Making Of* movie posted on the site. They sell the DVD as well to fund Blender and maybe a future movie project. The entire project files are available free for people to learn from.
An interesting fact: Because the movie is open source, a european company chose it to produce Europe's first HD-DVD pressing.

---

### Post by kenthomson799 on 2006-10-31
> **RudolfMDLT said:**
> 
Namaste - what does this mean? Just curiose.

Namaste means;
1)"I bow to the divine in you."

2)One beautiful interpretation: I honor that place in you where the whole Universe resides. And when I am in that place in me and you are in that place in you, there is only one of us.

----end of explanation of the word-------

I still have a few more questions, but i would better go through all the links that you guys have provided, before shooting all that has already been amswered somewhere.

BTW, if someone is comfortable with setting up Two Monitors, i could really use some help. My Question is:

ok, so...i am having a nvidia fx 5200 128MB, graphics card, with a VGA output to which my current CRT is connected. I dont have any other output on my graphics card, but i do have the (defualt output) of the motherboard (which is currently empty), Now my question is. Can i make two monitors work like this: One on the Graphic cards VGA, and the other on the Motherboards VGA?

If no, this is the second option. I have a REALLY REALLY OLD PCI graphics card, which has a VGA output. Is it possible to insert that ancient PCI card on my motherboard, and than have one monitor plugged into the Graphic card's VGA, and the other one in the *ancient* PCI's VGA output?"
----------------------------------------
END OF ORIGINAL QUESTION
-----------------------------------------

At this point can you answer this question:
1)Will one monitor on Motherboard's VGA and one on Graphic card's VGA would work?
OR
will one monitor on the (ancient) PCI card's VGA, and the other one on Graphic card's VGA would work?

I am a little reluctant to use the PCI card, becuase it is really old, I found it in the attic. It is manufactured by some company called "Ali-cat". And i dont even know whether it works or not.

Thank you for your time,
Namaste,
Ken

---

### Post by RudolfMDLT on 2006-11-01
Hi Ken,

Thanks for the translations! Very interpreting! What is the language? It really is a beautiful translation.

Good luck with Ubuntu!,

Rudolf

---

### Post by Forge42 on 2006-11-01
> **kenthomson799 said:**
> [FONT="Times New Roman"][SIZE="3"]

Q-3) I am going to do a fresh install of Ubuntu 6.10 on my AMD Athlon 2600 XP+ with a nvidia FX 5200-Graphics Card. Some users have problems installing Ubuntu 6.10 with nvidia cards. So should i install ubuntu on my machine? Will there by any problems? And what is the 'right' method to do it?




Others have addressed your other questions better than I could.  However, I would like to add that I am running this EXACT same set up.  Same GPU, same CPU.. I have a gig of RAM on an ASUS mobo (I forget the model).  At any rate, I have ubuntu 6.10 up and running from a fresh install.  I followed the howto for the Beryl/AIGLX install and (eventually) got it working (almost) flawlessly.  I am in love with Ubuntu.

FWIW - I have it running from a dual boot.  XP was installed first and then I used partition magic to carve out a linux partition and did the install from a Ubuntu boot CD.  Worked flawlessly.

---

### Post by kenthomson799 on 2006-11-01
Namaste,

> **Forge42 said:**
> ....I would like to add that I am running this EXACT same set up.  Same GPU, same CPU..I am in love with Ubuntu...I have it running from a dual boot...Worked flawlessly

It helps to know that, someone with the EXACT same setup (both the hardware and the software part) got it running flawlessly, though i certainly didn't doubt Ubuntu's capability earlier.

It just helps to know.

Thanks for dropping by, and adding few lines, other than simply glancing over the forum aimlessly. 

Thank you for your time,
Namaste,
Ken

---

### Post by kenthomson799 on 2006-11-01
Namaste,

> **RudolfMDLT said:**
> Hi Ken,

Thanks for the translations! Very interpreting! What is the language? It really is a beautiful translation.

Good luck with Ubuntu!,

Rudolf

Namasté or Namaskar (&#2344;&#2350;&#2360;&#2381;&#2340;&#2375;) is a Hindi (Indian National  Language) word derived from, Sanskrit (ancient Indian Language) "nama&#7717; te".

If you want to go further into spirituality, than i could go on...as i dont expect the people of "ubuntu" community would mind me "hijacking" their webspace. ;) 

(if you still cant get the above *wink*; "ubuntu" like "namaste" similarly has a philosphy attatched to it)

Namaste,
Ken

---

### Post by Forge42 on 2006-11-01
> **kenthomson799 said:**
> "namaste" similarly has a philosphy attatched to it)



It also has a hugely popular TV show attached to it:  LOST

---

