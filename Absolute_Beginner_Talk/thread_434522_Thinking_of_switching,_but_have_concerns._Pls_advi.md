---
title: "Thinking of switching, but have concerns. Pls advise"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by IgnattiousRavenhurst on 2007-05-06
Hi!

I'm completely new to Linux, but am a relatively competent computer user. 10+ years ago I sold/repaired windows boxes, and I have owned Macs. I started with DOS, so I'm not expecting too much culture shock from a CLI. A while ago I got fed up with it all and scrapped all my tech goodies and moved to a cabin in the woods to write my manifesto. (j/k about the manifesto, I'm harmless) Well, long story short, I'm back and things are much the same in Windows land. Windows is even bigger and clunkier, and more of a memory hog than ever. I like the IDEA of Linux and Open Source programs. When I looked into it, I was really impressed with the Ubuntu distro. I want to switch my laptop over (My only comppy now, and likely to stay that way for a while) but I have a few questions I need answered before I jump in head first. 

I have a "Ubuntu Bible" and I am currently reading it, and I am completely willing to learn the ins and outs if I decide this is the direction I want to go. I realize these questions of mine have probably been answered before in other threads, and I apologize, but I've gone over the forum for the last several hours and many answers are from earlier versions or several years ago. Rather than spend more time browsing for answers that may or may not be relevant anymore, I'll just ask and take my flaming like an adult.

My laptop is   Toshiba Satellite with a P4, 2GB ram, 100 GB HDD (30 or so free) built in wireless (super G), an ATI graphics card, a DVD burner, and surround sound. There is a little sticker on it that says "designed for windows xp" which it is currently running (with service pack 2.) Is that an issue? I also use an external Maxtor 200GB HDD which is less than half full with media. 

1) Is there likely to be a problem with my wireless connection? I leach wireless service from my landlord (and friend, he knows) and it is my only connection.

2) Should I Dual Boot? I don't use any apps that I need that can't be replaced with Linux freeware, but I am kind of nervous. 

3) I'm not really a huge gamer, but I love the Elder Scrolls games. Will they run ok with Wine? They are really the only games I play on my PC, and while I do love them I wouldn't die id I couldn't. But it would be nice if they worked.

4) Is there a good DVD player? MP3 player? I keep a lot of media stored on my laptop. I also need to synch it to my little Sansa MP3 player. Will this be an issue? It only reads mp3/mpa formats. 

5) How should I partition my HDD? What file system should I use? I have a lot of photos/movies/music I have to keep. Any choices I make have to be able to read my old media. Will I have to reformat my external drive?

6) Are there driver available for all the goodies that came built into my laptop? Are they in to distro or are they available for download before I start?

Well, that is it. I thank you in advance for any help you may provide. I'm sorry if these questions are answered in other places, but I need to figure out if Ubuntu is for me or I am going to be a slave to Bill Gates forever ;)

---

### Post by Whiffle on 2007-05-06
I say do it!  

Windows XP sticker is not an issue, its just there because some contract says it should be.  My Thinkpad T43 had the same sticker on it, and it was the first thing I removed :D  The TP runs much better under linux than windows though in my case.

The only caveat I can think of for your laptop off the top of my head might be the ATI graphics, but I've heard that they have gotten better recently.

1)  Wireless is kind of so so, sometimes, maybe, not always.  In some cases, it works flawlessly.  Sometimes, it doesn't.  I would download and burn a Live CD, and check out how it works.  Best case scenario is that it will pick up your wireless from the get go and you'll be in good shape.  Worst case is that it won't work, but I think that is very highly unlikely.

2) I've been using linux for about 5-6 years now, and I dual boot on both my computers.  Why? I dunno.  I've got the hard drive space, so why not?  There are a few apps that I need that run in windows as well.  But, if you've got no strong ties to windows, then there isn't any issue with just running linux.

3) Can't help ya here.

4) DVD players are abundant, kaffeine, mplayer, xine, totem, etc.  I've had less trouble playing media files in linux than i ever had in windows, assuming i have the right libraries and such installed.  If you install automatix, its really easy to get everything you need.  As far as music players, I use Amarok and it is seriousl the best music application I have used, ever, on any OS.  It flat out rocks.  It will sync up your sansa as well without any problem.

5) I tend to partition my hard drives in this way, I find that it allows me the most flexibility in dealing with data/linux and windows
```

On my 120GB laptop:
20 GB - Windows - ntfs
20 GB - Linux - ext3
1 GB - Linux Swap
5 GB - Ibm recovery partition - ntfs
74GB - /home - ext3

```

I store all my data and such on /home.  I install this driver [http://www.fs-driver.org/](http://www.fs-driver.org/) in windows so I can access my data from there.  If i ever need to reinstall either linux or windows, i just wipe that partition and reinstall, piece of cake.  In the case of linux, all my personal settings are stored in /home, so even if i install a completely different distro, most if not all of my settings come back.  

You shouldn't have to format your external drive assuming its FAT32.  If its ntfs you'll have to use the ntfs-3g driver to access it I think.

6) Laptop goodies?  I'm not sure, depends on what they are :)  On mine, the thinklight worked right out of the box, and about 10 minutes of work got the fingerprint reader working.

---

### Post by candtalan on 2007-05-06
Welcome!

Most of your questions may  be answered by initially using the live CD, which will give a fully operating system, including (virtual) install of applicatiions and functions.

The culture shock I found was not the cli but the whole approach of choice and independence.  There is no big funded profit business out there to turn to if things are uncertain - you find out by asking the community (or paid for support of course) or do it yourself.

The lack of retail activity is a shock.

Your previous experience will tend to hinder you as much as anything. Your sense of helplessness at times will be more intense because you know how you would do things with other systems - which you took years to learn. Now you will want things to work not in years, but minutes!

Good luck and best wishes

---

### Post by Tundro Walker on 2007-05-06
I'll try to answer some of your concerns, but can't help you on others (like wireless), because I have no experience with them.  Well, onto the stuff I might be able to help with...

> 1) Wireless...will it be a problem?I haven't had experience with this, since I don't use wireless (I'm on wired cable modem), but from what I've read, Feisty Fawn made pretty good progress resolving peoples' issues with wireless.  However, this can be a huge make or break point for folks, because Ubuntu is pretty internet heavy.  By that, I mean it relies heavily on online updates, Add/Remove and Synaptic package/software managers that let you tap online repositories to install more software, etc.  Think of it like an online store that you don't pay for...you literally have hundreds, if not thousands, of things you can install at your whim, from word processors, to code libraries, to desktop themes, to support things that help you do some of that stuff, like a theme manager that helps you tap into a web-site where folks POST new themes, letting you download from that.  Ubuntu is very online-centric, so if you can't get your wireless working, I wouldn't use it (personally).

> 2) Should I Dual Boot?This is really the last question to answer, because it relies on the answer to your others questions.  If your mp3 player, Windows games, and all the work or what-not you've created in Windows Applications (EG: songs in Cakewalk or Sony Acid Pro) don't work in Linux, then you'll probably want to dual-boot to get the best of both worlds.  In dual-booting, most folks do whatever they absolutely need to do in Windows, and use Ubuntu for safety-related things like surfing the net or checking email (where it helps prevent a virus from ruining your day.)

> 3) Can it play Elder Scrolls (assuming Oblivion, and perhaps Morrowind)[This post]("http://ubuntuforums.org/showthread.php?t=349764") (in Ubuntu forums) should help you decide if it's worth dual-booting to Windows to play Oblivion instead of attempting to WINE it in Ubuntu.  Skimming through it, it doesn't look impossible to get Oblivion up and running in Ubuntu, but it does look...well, less than user-friendly.  You can also look at [this post]("http://www.uesp.net/wiki/Oblivion:Linux"), which is from the UESP (an Elder Scrolls fan-site I think).

For Morrowind, looks like someone named Loki created a client that can run Morrowind natively in Linux.  [This link]("http://liflg.org/?catid=7&gameid=38") should help.  Reading some forum posts, it looks like it some how hooks into the WINE emulator, helping it read the Morrowind files easier (or something...not sure).

[COLOR=Gray](BTW...USELESS TRIVIA...if you ever played Morrowind, you may have used a mod for it called "Lilarcor Talking Sword"...yeah, that was mine, the voice and coding.  Sad, isn't it...LOL!  Unfortunately, I kinda lost interest in video games before Oblivion came out, so I never got into it to do a sequel for Lilarcor.  I hear somebody made a version of him for Oblivion, though.  "Wouldn't it be cool if I could cast 'bad dubbing' on you every time I was equipped...'hunh, your kung fu is no good here'...LOL!)[/COLOR]

> 4) Is there a good (Multimedia) player?There's tons of them.  Totem is a good multimedia player, and comes default in Ubuntu for your music and movie needs.  You can install Amarock, Gnomad2, XMMS, etc from repositories, and they're all good music players.  I personally use XMMS as a WinAmp-style "lite" mp3 player, and use Gnomad2 to transfer mp3's back and forth on my Creative Zen Vision:M mp3/multimedia player.

The issue isn't whether there's good players (Open Source software is as good as, if not better, then commercial software in some cases, because profit, budget and time schedule have been removed from the equation, letting programmers produce really elegant, wonderful stuff as they see fit).  The issues are...[LIST]
[*]a) can it run formats you want to use (EG: MP3's), and
[*]b) can it work with your mp3 player (which you mentioned).[/LIST]a) Ubuntu by nature kind of shuns the use of proprietary formats, like MP3, WAV, WMV, MPEG, etc, because it wants to be completely free and open.  So, it steers clear of incorporating proprietary and/or licensed formats in its distro.  However, that's not to say you can't use them period.  In the past, you used to have to hook into a repository, and install the necessary lib's, etc to get this stuff to work.  Or, as some would do (to make it easy), they'd use EasyUbuntu or Automatix, which helped install lots of stuff like that very fast and easy (although tended to mess up  a person's install, so upgrading was usually buggy, forcing a complete re-installation when upgrading).  However, Ubuntu and Canonical have take a more moderate approach lately.  They still won't bundle that with their distro, but if you try to play an MP3, it'll let you know that it's a restricted format, and gives you the option to have Ubuntu automatically install the necessary whatevers to get it working.  Basically, a pop-up messages displays letting you know that using such licensed or proprietary formats in certain parts of the world is illegal or such without paying for it.  You have to answer "yes" that you take responsibility for installing stuff on Ubuntu letting you use that stuff, and it'll do it.  It's quite painless.  Likewise, you can pre-emptively go into the "Add/Remove" system menu (which is a dumbed-down Synaptic repository manager, helping you install useful software), and go to the "Restricted" section to install proprietary drivers, codecs, etc.

b) Will your mp3 player work?  Well, up to Ubuntu 6.10, my Creative Zen, which is a sub-classification of USB called MTP (Media Transfer Protocol) didn't work.  Reason being, MTP is a format Microsoft pushed heavily into USB land, and folks like Creative, who are big time Microsoft hardware supporters, ate it up and spat out products like the Zen that for a long time would only work on Windows.  However, some Linux dev's create an MTP library, which the latest version of Gnomad2 that you can get through Feisty Fawn uses.  So, when I was using Ubuntu 6.10, my Zen was detected as a camara (d'oh!).  As of Feisty Fawn, it's detected as an mp3 player when I use Gnomad2, and can transfer mp3's back and forth.  However, I'm still not sure if I can transfer movie files over to it...I never use it for movie-watching, so I'm not sure.  If your mp3 player is the type that just acts like a USB flash key/drive, then you shouldn't have any issues at all.  Ubuntu should detect it easily, let you drag mp3's onto it (and other files, but you'll only be able to listen to the mp3's, obviously), and you're good to go.

I think folks in [this post ]("http://ubuntuforums.org/showthread.php?t=261947&highlight=sansa+mp3+gnomad2")answered whether Sansa works or not.

> How should I partition my hard drive?Assuming you're going to dual-boot, or even if you're going to go all Ubuntu, I'd partition my drive to have a large "holding bin" for movies and mp3's.  Then, you'd naturally have partitions for Ubuntu and Windows.  In addition to that, Ubuntu also requires a "swap" partition which it uses for its swap file.

So, something like this for dual-booting...[LIST]
[*]Partition 1) Windows (NTFS most likely if you're using XP)
[*]Partition 2) SHARED (FAT32 for movies, mp3's, etc)
[*]Partition 3) Ubuntu (ext3)
[*]Partition 4) Extended
[*]Partition 5) Linux Swap (which is actually a sub-parition in Partition 4)[/LIST]If you use a LiveCD to install Ubuntu, it'll actually do a pretty good job of hand-holding you through the partitioning.   It lets you choose if you want to do the partitioning, or if you want it to totally wipe your drive and install the Ubuntu & Swap partitions, or if it should use the largest available free space to install Ubuntu & Swap partitions.  If you choose to manually tweak the paritions, it'll start a program called "gparted", which is a very easy to use GUI paritions manager.  You just graphically alter the Windows partition down, then create a FAT32 partition for your SHARED content, then leave about a 3rd left for Ubuntu.  Don't actually make the Ubuntu partitions...just leave it empty on your drive.  Use gparted to enact those changes (make sure you defrag Windows, first...to make sure all the files are clustered together on it's partition tightly, lest you accidentally resize some files off the partition).  When the changes made, you can go "back" in the installation process and tell Ubuntu to use the largest available free space on your hard drive (being that 1/3 empty space you freed up), and it'll toss itself in that, doing the partitioning for itself for you.  It'll detect Windows, so it'll install and setup GRUB for dual-boot.  Should be fairly painless.

With all that said, my current Feisty (which I did a fresh install of), only has 2 partitions...Ubuntu & Linux Swap...which use the whole drive.  However, I still think making a SHARED partition is good, because it sections off your stored content from the Ubuntu installation.  So, if Ubuntu hoses up (on the rare chance), you can just wipe the Ubuntu partition and reinstall, leaving your SHARED partition alone.   I regretted not doing this when upgrading from 6.10 to 7.04 hosed up my Ubuntu install (which was my fault, because I used Automatix2 to install some restricted drivers, and Automatix had a tendancy to "break" an Ubuntu install in the past, making upgrading a bit buggy...I knew the risk, so wasn't shocked when it happened).  However, I just used the LiveCD to boot from, and mounted my Ubuntu partition, saved off whatever I wanted to keep onto a flash stick, then reformatted and fresh-installed Feisty.  I guess I don't exactly practice what I preach...LOL!  But then again, I don't have too much on my computer I care about if I lost it.

> 6) Are there drivers for my laptop goodies?I guess you mean like built-in web cam or such?  Since Linux is sort of an uninhibited playground for developers, there's drivers for almost everything out there.  The only driver problems would arise if something is really, really new, and a Linux dev has gotten ahold of some Widows drivers to reverse-engineer, or if it's considered "restricted" stuff by Ubuntu.  For instance, I had to use the "restricted manager" to add in the drivers for my Nvidia card.  But, like I said, with the release of Feisty Fawn, the Ubuntu developers have made it less painful to install "restricted" drivers.

-------------------

With all that said, you should be able to decide if you want to dual-boot or not.  The best thing you can do is burn the latest .iso to cd so you have a LiveCD on hand.  That helped me quite a bit, when I inadvertently jacked around with settings in XFCE on Xubuntu, or forced an uninstallation of something which I later found out was critical when I was messing with my system.  Ubuntu has been amazingly resilient to my sometimes destructive tweaking, but sometimes I do something to keep it from booting up the desktop or such.  Having the LiveCD on hand has let me boot to a fully functional OS from just the CD, and then I can mount the drive and modify whatever config file I screwed up.  Saved my bacon a couple times.

With the Feisty Fawn LiveCD, you may be able to answer your questions about the Sansa mp3 player detection, too.  Just plug it in and see if it's detected.

Hope all this helps, and I hope you decide to give Ubuntu a try.

---

### Post by userundefine on 2007-05-06
1) Is there likely to be a problem with my wireless connection? I leach wireless service from my landlord (and friend, he knows) and it is my only connection.

**Best to get the chipset and version before we can correctly answer this.  Either way, wireless support on Linux has become very good.**

2) Should I Dual Boot? I don't use any apps that I need that can't be replaced with Linux freeware, but I am kind of nervous. 

**Yes, at least at first just in case something goes wrong, like your wireless isn't configured.  As you don't have a wired connection, you'd need to be able to get help via forums and such.  But, if you're serious about it, dualboot should mainly be used as a last-ditch option in order to fix your Linux install if there's a problem (like inet connection).**

3) I'm not really a huge gamer, but I love the Elder Scrolls games. Will they run ok with Wine? They are really the only games I play on my PC, and while I do love them I wouldn't die id I couldn't. But it would be nice if they worked.

**This I'm not sure.  Check the winehq.com database.**

4) Is there a good DVD player? MP3 player? I keep a lot of media stored on my laptop. I also need to synch it to my little Sansa MP3 player. Will this be an issue? It only reads mp3/mpa formats. 

**Mplayer will play just about everything.  Linux certainly does not lack in quality media playback programs.**

5) How should I partition my HDD? What file system should I use? I have a lot of photos/movies/music I have to keep. Any choices I make have to be able to read my old media. Will I have to reformat my external drive?

**Aside from the dual boot which the installer will do for you, I'd do / on one partition (5-10gb with the 10gb used if you're planning on installing games in / instead of somewhere in your /home).  And then I'd give the rest to /home making the exception for a swap partition.  A /home partition is always a good thing.**

6) Are there driver available for all the goodies that came built into my laptop? Are they in to distro or are they available for download before I start?

**Like before, depends on the laptop.  Post all the specs.**

Well, that is it. I thank you in advance for any help you may provide. I'm sorry if these questions are answered in other places, but I need to figure out if Ubuntu is for me or I am going to be a slave to Bill Gates forever ;)

**Welcome.**

---

### Post by jimrz on 2007-05-06
> **IgnattiousRavenhurst said:**
> Hi!

I'm completely new to Linux, but am a relatively competent computer user. 10+ years ago I sold/repaired windows boxes, and I have owned Macs. I started with DOS, so I'm not expecting too much culture shock from a CLI. A while ago I got fed up with it all and scrapped all my tech goodies and moved to a cabin in the woods to write my manifesto. (j/k about the manifesto, I'm harmless) Well, long story short, I'm back and things are much the same in Windows land. Windows is even bigger and clunkier, and more of a memory hog than ever. I like the IDEA of Linux and Open Source programs. When I looked into it, I was really impressed with the Ubuntu distro. I want to switch my laptop over (My only comppy now, and likely to stay that way for a while) but I have a few questions I need answered before I jump in head first. 

I have a "Ubuntu Bible" and I am currently reading it, and I am completely willing to learn the ins and outs if I decide this is the direction I want to go. I realize these questions of mine have probably been answered before in other threads, and I apologize, but I've gone over the forum for the last several hours and many answers are from earlier versions or several years ago. Rather than spend more time browsing for answers that may or may not be relevant anymore, I'll just ask and take my flaming like an adult.

My laptop is   Toshiba Satellite with a P4, 2GB ram, 100 GB HDD (30 or so free) built in wireless (super G), an ATI graphics card, a DVD burner, and surround sound. There is a little sticker on it that says "designed for windows xp" which it is currently running (with service pack 2.) Is that an issue? I also use an external Maxtor 200GB HDD which is less than half full with media. 

1) Is there likely to be a problem with my wireless connection? I leach wireless service from my landlord (and friend, he knows) and it is my only connection.

2) Should I Dual Boot? I don't use any apps that I need that can't be replaced with Linux freeware, but I am kind of nervous. 

3) I'm not really a huge gamer, but I love the Elder Scrolls games. Will they run ok with Wine? They are really the only games I play on my PC, and while I do love them I wouldn't die id I couldn't. But it would be nice if they worked.

4) Is there a good DVD player? MP3 player? I keep a lot of media stored on my laptop. I also need to synch it to my little Sansa MP3 player. Will this be an issue? It only reads mp3/mpa formats. 

5) How should I partition my HDD? What file system should I use? I have a lot of photos/movies/music I have to keep. Any choices I make have to be able to read my old media. Will I have to reformat my external drive?

6) Are there driver available for all the goodies that came built into my laptop? Are they in to distro or are they available for download before I start?

Well, that is it. I thank you in advance for any help you may provide. I'm sorry if these questions are answered in other places, but I need to figure out if Ubuntu is for me or I am going to be a slave to Bill Gates forever ;)

1. Depends on your wifi card ... most can be made to work, many work "out of the box" upon installation, but some provide more challenges. First off try the "live"cd to see how your h/w all works initially, then if wifi does not come up initially search these forums for your card (make/model/chipset) and see what others have done to get it working.

2. By all means. It will (maybe) releive your nervous feeling and give you a backup while you find your way around ubuntu and get comfortable with it. You can always dump win later, if you choose.

3. Not a gamer either, so I don't know. Dual boot would also give you time check this out, while still leaving you a for sure place to play.

4. Plenty of good media apps available for free. Not familiar with your Sansa mp3, again search will provide info. My Samsung mp3 player works perfectly with ubuntu.

5. If after checking things out with the "live cd" and you decide to give it a shot, go back into xp and defrag your xp drive (probably a couple of times would be better) then run the live cd again and click the Install icon on the desktop. The install includes a partitioner which you can use to shrink your xp partition (leave maybe 15-20 Gb open) and create the partitions for your ubuntu. I would recommend first creating an extended partition then puttiing your ubuntu ( / partition (5-6 Gb) + swap (should = 1.5 x your amount of ram) + (a separate) /home partition (whatever space is left) in the extended partition.  -OR-  if you have Partition Magic or similar (the Gparted "live cd" is a free download that works quite well for this), use it to shrink your xp (defrag is still a MUST) then, since linux can read but not write to ntfs, create a FAT32 partition that may be used by either os then move whatever files you would want to access from either into this partition. Next go back to your partitioning utility and shrink xp (defrag is still a MUST again and follow the steps listed above for the install partitioning. For linux file systems I use ext3 (believe this is the default on the installer) for / + /home and the partitioner automatically set up both your swap partition and GRUB with the correct file systems.

6. Yes there are. Again, the live cd will answer many of your questions about hardware without touching your harddrive. ATI linux support is not real good. This is common knowledge and my experience confirms it. Again it depends on which ATI card you have. My ThinkPad has an ATI mobility 9600 128 Mb a) works well using the free "ati" in the kernel which does give hardware acceleration but not nearly as good as in xp and b) is not supported for direct rendering by the official ATI drivers from Radeon. Like you I am not a big gamer so this is not a big problem. This does limit some of the "eye candy" options but, again, this is not important to me on the laptop. In fact, the only time I really ma bothered by this is when using Google Earth, which does run but is dramatically slower than when running it on the xp side :(.

Welcome ... hope you enjoy it.

sorry about being so long winded, but you asked about a lot of stuff ;)

---

### Post by rhonaldmoses on 2007-05-06
Howdy,

I've noticed that lots of ppl have given their good suggestion. This is how I did. I have to keep Windows XP Pro with Service Pack 2 in my Laptop (Dual Core 2, 4GB RAM, 120GB SATA, 256MB nVidia, bla bla bla) to run Visual Studio .NET (C#, ASP.NET), SQL Server 2005 for my office works. Otherwise, Linux is what I run (for all my personal needs since I am PHP/Perl, MySQL, C++ programmer for hobby and now pondering around Mono).

In my 120GB Hard Drive (since I had 120GB, 80GB, 500GB External drives under Fat32 file system, I didn't bother about making a common FAT partition for both filesystems to access in my laptop), I alloted 35GB for Windows XP (NTFS) and the rest for Ubuntu (prior to Ubuntu 7, it was openSUSE 10.2). If you need a file sharing between OSes, you can either use NFTS writing through 3rd party stuffs mentioned in one of the above replies or, u can have a small parition with Fat32 or you can use your external hard drive, assuming it is formated with FAT32 - or vfat as middle man in file sharing.

I never had wireless problem so far, so I am not sure about that.

Otherwise, I never had problem with any lack of applications.

Games... I am not sure whether you can run the game you wanted, but you can go through Ubuntu repository and get some cool game for time pass which I did.


But foremost, be open minded and prepare to learn something when you get into Linux. Unlike windows which restricts what you can do with the box, linux lets you free like a wild horse. You can do anything you want, provided you allot some time for it.

My verdict for your total linux adaption (which includes throwing away your windows completely) is 'thumbs up'.

My other desktop is complete linux since I dont use it for office works ayway. I've kept as my server (web, file and internet at home).

have great time.
community is always here to help you out. try live cd (remember that since it's live, it will be slow and not necessarily all the hardwares will be detected) before installing it.

Adios.

---

### Post by IgnattiousRavenhurst on 2007-05-06
Wow, you guys are awesome! So quick to answer my (admittedly noobish) questions.

What I meant by goodies on my laptop was my dvd burner and surround sound. I just wanted to be sure that I could still burn disks. 

As long as I can play my "proprietary" media on Linux players (and synch my Sansa) I could just load it all on my external drive (with a backup of windows), format and partition my laptop drive and load it all back. Maybe I should burn it to dvd's as well, just in case. (I have my whole, substantial music collection on my laptop. I use it as sort of a music server for when I'm home. It would take forever to re-rip all those cd's.)

I'm downloading the live cd now, and when it is done, I plan to burn it. I'll give it a shot, and hope I still have my connection. I really want to switch, but I'm (still) a little nervous. The only OS replacement I've ever done is way back to OS/2 Warp (and that used the same file system as Windows, so I didn't worry about it as much.)

My built in wireless is Atheros super G 802.11. Where can I find out what chipset it uses? Would it tell me in Windows, or would I have to go to the Toshiba website? Same with my ATI card. I bought it refurbished, so it didn't come with much documentation. 

Thank you all so much for your help. I'm glad if I ever need a hand, I have someone to ask.

---

### Post by sailor2001 on 2007-05-06
remember for dual booting when ready is to defrag your windows......chipset can be found at bottom signature

---

### Post by Whiffle on 2007-05-06
> **IgnattiousRavenhurst said:**
> Wow, you guys are awesome! So quick to answer my (admittedly noobish) questions.

What I meant by goodies on my laptop was my dvd burner and surround sound. I just wanted to be sure that I could still burn disks. 

As long as I can play my "proprietary" media on Linux players (and synch my Sansa) I could just load it all on my external drive (with a backup of windows), format and partition my laptop drive and load it all back. Maybe I should burn it to dvd's as well, just in case. (I have my whole, substantial music collection on my laptop. I use it as sort of a music server for when I'm home. It would take forever to re-rip all those cd's.)

I'm downloading the live cd now, and when it is done, I plan to burn it. I'll give it a shot, and hope I still have my connection. I really want to switch, but I'm (still) a little nervous. The only OS replacement I've ever done is way back to OS/2 Warp (and that used the same file system as Windows, so I didn't worry about it as much.)

My built in wireless is Atheros super G 802.11. Where can I find out what chipset it uses? Would it tell me in Windows, or would I have to go to the Toshiba website? Same with my ATI card. I bought it refurbished, so it didn't come with much documentation. 

Thank you all so much for your help. I'm glad if I ever need a hand, I have someone to ask.


DVD burner should work.  Surround sound depends on the chipset.

Atheros wifi stuff uses the madwifi drivers, and last i checked they work quite nicely.

---

### Post by IgnattiousRavenhurst on 2007-05-06
OK, I finally got the live cd downloaded, matched the checksum, and burned it to a disk. I booted from it, and got to the main screen. Wow. Looks great. My sound and dvd worked fine except for some skips in the sound. No wireless though. It recommended  I use NDISwrapper, which it said was on the live cd. When I followed the instructions in help, which directed me to run add/remove program, it said that I needed a live internet connection. There didn't seem to be a way to search the disk for it. Did I overlook something? Can I download it while I'm using windows and install it under Frisky Fawn? Or am I going to have to suck it up and ask Dave (my friend/landlord downstairs) if I can hijack his ethernet connection for a while?

From what I've seen so far, I love it. I'm seriously considering doing away with my dual boot idea and just running Ubuntu straight. I think with some judicious dvd burning I can swap my media back and forth between my drives and format them both. Ubuntu kicks serious butt. I did have one more question about the firefox that comes with it. Can I import my preferences and all my "remember me" log in information from my current firefox install along with my bookmarks? How about my plugins, are they platform specific?

Thank you for all your help. As soon as I get the wireless thing worked out I'm going to do a full install. 

I've been up for over 20 hours playing with this thing, so I'm going to take a nap before I try and tackle my remaining problems.

Thank you all again. When I learn enough to loose my "noobishness" I promise to help out anyone I can. The community of supporters is probably the best thing about this distro! I've never seen anything like it as long as I've been around computers. In my research, I heard that other distros were a little more Noob friendly, but Ubuntu had by far the best community. And it turned out to be true. You all politely answered questions that would have earned me an rtfm or been ignored in other venues. Brings back my faith in the internet, I tell ya.

:)

---

### Post by jimrz on 2007-05-06
> **Whiffle said:**
> DVD burner should work.  Surround sound depends on the chipset.

Atheros wifi stuff uses the madwifi drivers, and last i checked they work quite nicely.

concur ... your atheros is probably the 5212 chipset, as are both of my wifi equipped boxes and they both work "out of the box" on feisty ... all you likely will need to do is locate and select  your AP in network-manager (towards the right-hand end of your top panel) and enter your networks settings (wep or wpa), if needed. if it is wpa, you will need to set up your keyring and a password for it (make it different from your user pw,as it does not like them the same) which you will have to enter each time you connect, so that network-manager can access your passcode, which is stored on the keyring. if this is needed it will automatically pop up the screens you need to complete the proceedure. this is a bit of a pain but also another layer of security, and it does not take too long to get used to ;). of course, if the AP is wide open none of the keyring stuff will be needed, just select it and go on.

---

### Post by IgnattiousRavenhurst on 2007-05-08
Hi guys!

I got my wireless working! I am now running Ubuntu and on the net at the same time. I'm still interested in how I can import all my info into this version of Firefox. It has a lot of username/passwords that would be a hassle to put in manually. Still, I'm pretty excited about the whole thing. And by the next time I post I hope to have it all installed permanently. And running flawlessly! I also got the skips out of my sound. I am really excited about this. I feel like I accomplished something, instead of just sitting in front of my computer, fiddling with it. 

Thank you all for your help. I'm still confused by some of the terminology, but I have  few Ubuntu books I'm working through, and it's helping.

I'm sure I'll still have questions, but between my books and this forum, I'm sure I'll be fine.

You guys rawk! :guitar: 

Iggy

---

### Post by jiminycricket on 2007-05-08
You can copy firefox passwords: [http://forums.mozillazine.org/viewtopic.php?t=229924&highlight=](http://forums.mozillazine.org/viewtopic.php?t=229924&highlight=) or [https://addons.mozilla.org/en-US/firefox/addon/2848](https://addons.mozilla.org/en-US/firefox/addon/2848)

Or try Google Browser Sync: [http://www.google.com/tools/firefox/browsersync/](http://www.google.com/tools/firefox/browsersync/)

---

### Post by Boelcke on 2007-05-08
I second the "you guys rawk" motion.  In the absense of any linux gurus near me, these forums have made me ubuntu capable.  A critical resource -- a deal maker, in my opinion.

I'll give you another interesting wow-I'm-gushing-about-the-Linux-experience.  Note that I fully recognize that I've spend more time fiddling with my computers since switching from XP, but it has been more fun, and less virus cleaning.  Anyhow, I got a new mp3 player from Creative (a Zen), just after it came out.  The library that supported the MTP (some odd music protocol designed to keep consumers from owning the stuff they buy) didn't cover that model.  I thought I was out of luck, and would have to return it.  A discussion here on this forum pointed me to the mailing list for that library.

After a little conversation on there, the GUY WHO MAINTAINS THAT CODE added that model the next week!  Now, I'm sure he was planning to do it anyway, and it wasn't just for me.  However, how cool is that?!?  I don't get that sort of response and involvement from commercially sold software!

It's an entertaining trip.

---

### Post by IgnattiousRavenhurst on 2007-05-09
Thank you for the links. Unfortunately, I formatted my hdd before you posted it. 

I have noticed some strange things going on, and I was wondering if anyone knew what was happening. 

First, I can't get any bittorrent client to work. I used Azureus (which I used in windows) and it wouldn't even open. It just flashed on the screen and gave me an error [X is not a file] . When I clicked on (ok) it closed. Weird. bittornado never connected to anyone, even after sitting for a half hour.  It also wouldn't remember any changes I made in prefs. Specifically designating a listening  port. I also can't designate a static I.P. addy. I used the same settings I used in Windows that worked fine. I looked in "Wiley's Ubuntu Bible" and "Non-geeks guide to Ubuntu" but they didn't offer anything that solved the problem. (just to show I tried to solve it on my own. ;) )

Also internet related things tend to lock up my system. The whole system, not just the browser.  Does a hard reboot cause the same damage to a Linux system it does to a Windows system? Cuz I have had to power off and restart fairly often since I did the full install. I'm assuming it is something I did, or something about my system, because if this is the standard result, there wouldn't be this big of a community around it. 

For the record I did a hands off install, letting it do what it wanted. The only extra software I installed was Wine, some media libs, bittornado and Azureus, Aria download manager, and the VLC media player.  Oh, and an archive manager. (I forget which one.) 

I'm kinda bummed now, but I want to get this working. I am determined to make this work. 

Iggy

PS. A dumb question, but do programs for the KDS window manager work under Gnome? I wasn't sure, so I stayed away from them.

---

### Post by livingtarget on 2007-05-09
To give you an answer on Elder Scrolls Morrowind, I never did get that to work on [wine](http://www.winehq.org/). You could pay for [cedega](http://www.transgaming.com/index.php?module=ContentExpress&file=index&func=display&ceid=29) and you'll probably have more luck, but would you pay for something like that? I just choose to have a dual boot.

Last time I booted in windows was to play some Oblivion :)

> 
PS. A dumb question, but do programs for the KDE window manager work under Gnome?

Yes they do, you may need to install some kde components but they'll work. I run Amarok in gnome and I'm glad it does.

---

### Post by shadowboxer_k on 2007-05-09
about the DVD burner...i have to tell you that my cd burner had stopped working under windows for like a year and it started working immediately after i switched to linux. so if anything, writing cds/dvds will be a breeze, i'm sure.

---

### Post by zami on 2007-05-12
[QUOTE=IgnattiousRavenhurst] 
First, I can't get any bittorrent client to work. I used Azureus (which I used in windows) and it wouldn't even open. It just flashed on the screen and gave me an error [X is not a file] . When I clicked on (ok) it closed. Weird. bittornado never connected to anyone, even after sitting for a half hour. It also wouldn't remember any changes I made in prefs. Specifically designating a listening port. I also can't designate a static I.P. addy. I used the same settings I used in Windows that worked fine. I looked in "Wiley's Ubuntu Bible" and "Non-geeks guide to Ubuntu" but they didn't offer anything that solved the problem. (just to show I tried to solve it on my own.  )
[/QUOTE]

I understand this is a three day old post, and mabye you've figured out your torrent conundrum by now.  
But! If not, I wanted to let you know that KTorrent is the only torrent program I ever got running properly.  It is a KDE program, but if you install it through the Add/Remove Applications mathingy, it will install all the KDE components you might need.  Don't let the "for the KDE desktop" message deter you.  :)

Good luck!  Hope everything else is going smooothly for you!

(And when you feel like complicating things for yourself again, you can start tinkering with other desktops (KDE, Fluxbox, XFCE, etc), Beryl or Compiz, Gdesklets, Adesklets, and just general, enjoyable, time wasting.  Muah, hah, hah....)

-zami

---

