---
title: "Format every 6 months?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by styphon on 2007-07-26
I am an XP user about to migrate over to an XP/Ubuntu dual boot. I'm a firm believer of the format windows every 6 months rule. Does Linux follow the same lines or is it more stable than windows and is fine without the format twice yearly?

---

### Post by Orochi on 2007-07-26
You definitely will never need to reformat for stability reasons.

---

### Post by styphon on 2007-07-26
OK, thanks for the info.

---

### Post by asmoore82 on 2007-07-26
> **styphon said:**
> I am an XP user about to migrate over to an XP/Ubuntu dual boot. I'm a firm believer of the format windows every 6 months rule. Does Linux follow the same lines or is it more stable than windows and is fine without the format twice yearly?
Indeed, if the power grid in your neighborhood is excellent, Linux will hardly reboot twice a year, much less need a format. However many Linux enthusiasts do re-format often just to try out other distros :). If you are up to the task of actively participating in the 'Partition' stage of installation; you can place the '/home' directory on a separate partition so that you can switch out Whole Linux OSes without loosing any personal files _or_ settings.

---

### Post by Orochi on 2007-07-26
Also keep in mind that a new Ubuntu version comes out every 6 months, so if you want the newest version you may want to reformat your drive and install the new one when it comes out (you can upgrade versions without reinstalling the whole OS, but lots of people prefer fresh installs). If you plan on doing fresh installs it's a good idea to make a separate /home partition like asmoore said.

---

### Post by styphon on 2007-07-26
OK, complete newbie to Linux but IT Administrator with XP. Just trying to get my head around some of the terminology. With XP I kept my "My Documents" folder on a different hard drive, let alone partition. I plan on making it a Fat32 partition and having the second hard drive "My Docs" and the equivalent (I'm guessing /Home) on the second harddrive.

---

### Post by Jerry N on 2007-07-26
Format Windows every 6 months?  Sounds silly to me -  I have been using Windows since Version 3.0 and the only version that has required regular re-installs was ME on a computer I was supporting.  ME was the worst piece of crap ever!

Jerry

---

### Post by FleetAdmiral74 on 2007-07-26
Yep, /home is where all your stuff will go. Even your desktop is in there, so you can access it as a folder if you prefer.

---

### Post by Orochi on 2007-07-26
Yeah what you want to do is set up the drive/partition where your /home files are to mount at /home. You can set this up in the initial installation if you select manual configuration of partitions. This makes the /home folder be on your other drive/parition instead of on the main partition where the rest of Ubuntu is installed. 

The /home folder contains your Ubuntu desktop and all your documents. Really anything you make or download should go in there. Most programs store their settings files in there too. Because of this, if /home is on a separate partition you can reformat/reinstall Ubuntu on the main partition and not lose any of your settings or files (although you will have to reinstall any programs you downloaded).

Oh and if you're making the second drive have both My Documents and /home, you'll need to have a separate partition for each. The /home partition should be formatted as ext3.

---

### Post by styphon on 2007-07-26
> **Jerry N said:**
> Format Windows every 6 months?  Sounds silly to me -  I have been using Windows since Version 3.0 and the only version that has required regular re-installs was ME on a computer I was supporting.  ME was the worst piece of crap ever!

Jerry

Agreed, ME was so unstable. Most versions of windows (everything upto and including XP, not tried Vista) generates so much crap in just general every day use that it slows itself down. Windows is inherently crap in its architectural structure. As a gamer seeking performance, Windows being reformated every 6 months helps keep that performance up.

---

### Post by asmoore82 on 2007-07-26
you deffinitely don't want to use FAT32 for any of your Linux system critial files and folders.

---

### Post by az on 2007-07-26
> **Orochi said:**
> if you want the newest version you may want to reformat your drive and install the new one when it comes out 


There is no reason to do a fresh install if you upgrade from one release to the next.  

You may get into trouble if you customised your system using software from outside the Ubuntu repositories or outside of the control of the pacage manager.  But those are the exception to the rule.

---

### Post by styphon on 2007-07-26
> **Orochi said:**
> Oh and if you're making the second drive have both My Documents and /home, you'll need to have a separate partition for each. The /home partition should be formatted as ext3.

Ah, thats the problem. I want to be able to have 1 set of music files and images etc. Is there a way to have both Windows and Linux view the same folder as My Docs & /Home?

---

### Post by asmoore82 on 2007-07-26
> **styphon said:**
> OK, complete newbie to Linux but IT Administrator with XP. Just trying to get my head around some of the terminology. With XP I kept my "My Documents" folder on a different hard drive, let alone partition. I plan on making it a Fat32 partition and having the second hard drive "My Docs" and the equivalent (I'm guessing /Home) on the second harddrive.
in the beginning you may have a lot of fun (trouble) with a true case sensitive system.
There will be a big difference between /home and /Home

Also in the beginning i wouldn't get too fancy. trying to make direct translations of Winders "Power User" setups over to Linux is a good way to cripple your shiny new linux system. Not trying to be too harsh but almost all advanced windows experience is of no use at all on Linux systems. The real irony is that you would probably be better off in Linux not to have that advance windows knowledge. But be patient and have FUN.

---

### Post by alex_anthony on 2007-07-26
I think I read somewhere about pointing My Documents in Windows to a different place...
Probably best not to try the other way round because the equivalent of program files are in your /home, so when you install programs they will get confused

---

### Post by styphon on 2007-07-26
> **asmoore82 said:**
> 
Also in the beginning i wouldn't get too fancy. trying to make direct translations of Winders "Power User" setups over to Linux is a good way to cripple your shiny new linux system.

What would be the best way then to have one place to store all my common files (MP3's and Images mainly) that is accessible to both Linux and Windows?

---

### Post by Orochi on 2007-07-26
I would suggest on your second driving making an ext3 partition and a FAT32 partition. Mount the ext3 as /home. Then mount the FAT32 as /home/media or /home/music or something similar. That way all your linux-specific stuff will be on ext3, and the stuff that's common to both OS's can be on FAT32.

> **az said:**
> There is no reason to do a fresh install if you upgrade from one release to the next.
I know there isn't, I won't be fresh installing myself. I just know a lot of people like to do fresh installs, so I was mentioning it.

---

### Post by asmoore82 on 2007-07-26
> **styphon said:**
> Ah, thats the problem. I want to be able to have 1 set of music files and images etc. Is there a way to have both Windows and Linux view the same folder as My Docs & /Home?

Unfortunatly, Linux can read NTFS but not reliably write to it. (Microsoft vehemently refuses to document NTFS or else linux would quickly do NTFS better than Vista/XP)
Windows can read ext3 but not reliably do anything, much less write to ext3.

And in my experience, people who take the easy way out and set up a FAT32 because Win and Linux can read/write to it will be sorely dissapointed in Linux for various mysterious reasons.
It is my firm belief that having to read/write large amounts of data to such an inferrior file system adversely affect Linux Desktop Performance. I have seen Linux computers much faster than mine load a playlist _much_ slower than mine; guess what type of filesystem _his_ mp3's were on ;).

Also keep in mind that all the way down to it's CORE Linux is a multiuser operating system and wants to maintain Owner/Group info as well as 3-way (Owner/Group/Others) permission on every single file and only UNIX based file systems can accomodate this.

---

### Post by scrooge_74 on 2007-07-26
> **styphon said:**
> OK, complete newbie to Linux but IT Administrator with XP. Just trying to get my head around some of the terminology. With XP I kept my "My Documents" folder on a different hard drive, let alone partition. I plan on making it a Fat32 partition and having the second hard drive "My Docs" and the equivalent (I'm guessing /Home) on the second harddrive.

One advice your /home partition needs to be in ext2 or ext3 format for linux to read your info it can be in M$ formats.

You can have a /home and then point other partitions with fat32 format to folders inside your /home

---

### Post by Orochi on 2007-07-26
> **asmoore82 said:**
> Windows can read ext3 but not reliably do anything, much less write to ext3.

This is incorrect, there is a Windows driver that allows it to read and write to ext3 reliably. Just do a google search for windows xp ext3 driver. The only downside is that it doesn't respect linux permissions, so anyone can view and edit every file on the ext3 drive.

---

### Post by Nekiruhs on 2007-07-26
> **asmoore82 said:**
> Unfortunatly, Linux can read NTFS but not reliably write to it. (Microsoft vehemently refuses to document NTFS or else linux would quickly do NTFS better than Vista/XP)
Windows can read ext3 but not reliably do anything, much less write to ext3.

And in my experience, people who take the easy way out and set up a FAT32 because Win and Linux can read/write to it will be sorely dissapointed in Linux for various mysterious reasons.
It is my firm belief that having to read/write large amounts of data to such an inferrior file system adversely affect Linux Desktop Performance. I have seen Linux computers much faster than mine load a playlist _much_ slower than mine; guess what type of filesystem _his_ mp3's were on ;).

Also keep in mind that all the way down to it's CORE Linux is a multiuser operating system and wants to maintain Owner/Group info as well as 3-way (Owner/Group/Others) permission on every single file and only UNIX based file systems can accomodate this.
Linux is perfectly reliable with NTFS. After you install ntfs3g it reads/writes it perfectly. Windows can't even read ext3. Windows shows it as unformatted. You have to go on and install special drivers in Windows to enable ext3 support.

---

### Post by fastpakr on 2007-07-26
> **Nekiruhs said:**
> Linux is perfectly reliable with NTFS. After you install ntfs3g it reads/writes it perfectly. Windows can't even read ext3. Windows shows it as unformatted. You have to go on and install special drivers in Windows to enable ext3 support.

I've also had no trouble with reading/writing NTFS after installing NTFS3G.

---

### Post by styphon on 2007-07-26
> **alex_anthony said:**
> I think I read somewhere about pointing My Documents in Windows to a different place...
Probably best not to try the other way round because the equivalent of program files are in your /home, so when you install programs they will get confused

Yea, thats the idea. I have a folder called My Docs on my D:/ drive in XP. I then point My Documents in XP to this folder. I am trying to find a similar solution in Linux so I can hold all my files in one place.

From looking at these replies, it seems the best solution would be to have a Partition on my slave drive in ext3 for /home and then a second partition in NTFS with all my files on it that I need for both, and then install ntfs3g. 

Oh, and just to complicate things, did I mention I wanted to do this on a 64bit version? Does having 64bit affect this at all?

Edit: Thinking about it, would Ubuntu be screwed if windows could access it's /home drive? I'm planning on using Windows only for stuff that wont work on Ubuntu, such as games. That means most of my documents would only be accessed in Linux, occasionaly from Windows so would it be better to have an Ext3 partition and install the necessary drivers for that in Windows?

---

### Post by Dead_$partan on 2007-07-26
There are tools that loow windows and Linux to read or write to NTFS/ext3 partitions, not sure if that's a good idea though :)

---

### Post by asmoore82 on 2007-07-26
> **Orochi said:**
> This is incorrect, there is a Windows driver that allows it to read and write to ext3 reliably. Just do a google search for windows xp ext3 driver. The only downside is that it doesn't respect linux permissions, so anyone can view and edit every file on the ext3 drive.

you call trampling and borking permissions "reliably" ??

---

### Post by Orochi on 2007-07-26
> **asmoore82 said:**
> you call trampling and borking permissions "reliably" ??

Ignoring permissions doesn't really affect it's ability to read and write to the drive. It's annoying, but it's not like it'll corrupt your drive with a mis-write and it's clearly possible to read from it.

I still say the best way to do it is to make two partitions. One ext3 for /home and the other NTFS or FAT32 for My Docs and then mount the My Docs partition as /home/Docs in Linux (after installing ntfs3g if necessary). However making the whole thing ext3 and installing the ext3 driver in XP will work fine too (although if you do it that way, I don't think you'll be able to make the My Docs folder in Windows point to the ext3 drive, I'm not sure though).

---

### Post by einversuchisteswert on 2007-07-26
I only want to mention that FAT32 does not accept files lager than 4GB. 

If you think that this is not important than make some DVD ISO ;)

[http://en.wikipedia.org/wiki/Fat32](http://en.wikipedia.org/wiki/Fat32) <- look at the table.

I often reinstalled my OS in the beginning (damn X-Server!). Just remember to backup your files if you are changing stuff (xorg.conf etc...).

---

### Post by p_quarles on 2007-07-26
> **styphon said:**
> Yea, thats the idea. I have a folder called My Docs on my D:/ drive in XP. I then point My Documents in XP to this folder. I am trying to find a similar solution in Linux so I can hold all my files in one place.

I haven't done this, but it should be fairly simple. Keep your Linux /home/user folder on the separate drive (on an ext3 partition), mount the disk in your Linux installation, and then change the home user folder on the main drive into a symbolic link pointing to the folder on the separate drive.

> Edit: Thinking about it, would Ubuntu be screwed if windows could access it's /home drive? I'm planning on using Windows only for stuff that wont work on Ubuntu, such as games. That means most of my documents would only be accessed in Linux, occasionaly from Windows so would it be better to have an Ext3 partition and install the necessary drivers for that in Windows?

I think the better solution would be to partition your secondary drive -- one ext3 partition for Linux, and a NTFS partition for any files you want accessible to both OSes.

---

### Post by djheadley on 2007-07-26
When I first started with Ubuntu I "labeled" my fat32 partitions for what they were in Windows so that my transition would be easier.  example:  /win/c  

Now that I am pretty familiar with Ubuntu, I've decided to leave it this way.  I haven't had ANY trouble with r/w on any of these partitions and I've been using various versions for 2 years now, currently on 6.06LTS.

---

### Post by styphon on 2007-07-27
Thanks for all the help with this guys. Nothing I'm ever going to store on my secondary drive is going to be over 4GB so Fat32 may be the solution I'm looking for because both OS's can r/w it natively.

One more quick question, if I create two partitions on my secondary drive, one EXT3 for /home and one Fat32 for all my files, how big should I make the EXT3 partition, leaving enough room for extra themes and the like? Other than personalised config files is anything else important held there?

---

### Post by Lord Illidan on 2007-07-27
1-5 gbs should be enough to cover much of your tracks..

That said, I don't like the way you're going to do it. I preferred using Linux exclusively.

---

### Post by AceofSpades19 on 2007-07-27
depends on how much stuff you download and save

---

### Post by styphon on 2007-07-27
> **Lord Illidan said:**
> That said, I don't like the way you're going to do it. I preferred using Linux exclusively.

Thats the aim eventualy. But 1, I've never used Linux before and require some functionality from my PC whilst learning how to use Linux. When I have time I'm going to port all the programs I use in Windows over to Linux and learn to use the Linux equivalent. Also, I'm a gamer at heart and not all games work on Linux so I'll need Windows for them.

> **AceofSpades19 said:**
> depends on how much stuff you download and save

I want to be able to save everything to the Fat32 partition. Only the bare minimum I have to have should be on the /home partition.

---

### Post by Lord Illidan on 2007-07-27
> Thats the aim eventualy. But 1, I've never used Linux before and require some functionality from my PC whilst learning how to use Linux. When I have time I'm going to port all the programs I use in Windows over to Linux and learn to use the Linux equivalent. Also, I'm a gamer at heart and not all games work on Linux so I'll need Windows for them.

That's ok. What applications/games are you using on Windows?

---

### Post by styphon on 2007-07-27
At the moment I play Eve Online (I've read there is a problem running that with WINE under the latest patch), GRAW 2, BF2. I'm also a fileplanet subscriber and get to run a lot of Beta's. I also use XFire and TeamSpeak for comms.

Programs are standard and I'm fairly confident from reading around that everything I need is covered. I use Adobe Photoshop/Image Ready, Macromedia Studios (Dreamweaver, FireWorks and Flash), WinAmp, PowerDVD and thats about it.

---

### Post by eentonig on 2007-07-27
> **styphon said:**
> Thats the aim eventualy. But 1, I've never used Linux before and require some functionality from my PC whilst learning how to use Linux. When I have time I'm going to port all the programs I use in Windows over to Linux and learn to use the Linux equivalent. Also, I'm a gamer at heart and not all games work on Linux so I'll need Windows for them.

....

I want to be able to save everything to the Fat32 partition. Only the bare minimum I have to have should be on the /home partition.

Those two statements contradict eachother :popcorn:

Anyway. To answer your partition problems.

HD1 
- Partition1 :[COLOR="Blue"] Windows install ("c:\")[/COLOR]
- Partition2 :[COLOR="Sienna"] Ubuntu install ("/")[/COLOR](10G is more then enough if you're going to put home somewhere else. You could even go by wit only 2GB. But that will leave little room for expansion. I think the current official minimum requirements are 4G?)

HD2
- Partition1 : [COLOR="Blue"]My documents  (ie. "f:\My Documents")[/COLOR] and [COLOR="Sienna"]("/home/<username>/Windocs")[/COLOR]
- Parttion 2 : [COLOR="Sienna"]HOME ("/home/")[/COLOR]


HINTS/TIPS:
##########
- since most of your userdocs wil be on the 'My documents' partition, give this the most space on the partition
- The files that really, really need to stay on the linux partition, are mostly config files and are linux specific. 

After your initial install, read up on mounting drives to setup the environment the way you want it. Basically, you'll want to know how to define the 'mountpoint', so you can make it appear under your home drive. (Allthough, I usually create symlinks to external volumes.)

---

### Post by styphon on 2007-07-27
Thanks a lot for the assitance everyone.

One question Eentonig, how do those statements contradict? I want to be able to move over to Linux completely whilst retaining full fuctionality that I have now. Unitll that time I will use Windows and as such I need to be able to access all my files on both Windows and Linux, hence using a Fat32 partition.

---

### Post by Smu on 2007-07-27
> **styphon said:**
> At the moment I play Eve Online (I've read there is a problem running that with WINE under the latest patch), GRAW 2, BF2. I'm also a fileplanet subscriber and get to run a lot of Beta's. I also use XFire and TeamSpeak for comms.

Programs are standard and I'm fairly confident from reading around that everything I need is covered. I use Adobe Photoshop/Image Ready, Macromedia Studios (Dreamweaver, FireWorks and Flash), WinAmp, PowerDVD and thats about it.

Photoshop and the Macromedia Studios work really good with wine. I'd recommend you to install a windows on a virtual machine (VirtualBox), thanks to a virtual machine my physical windows installation is becoming useless. Don't know how good games work on virtual machines though...

---

### Post by styphon on 2007-07-27
> **Smu said:**
> I'd recommend you to install a windows on a virtual machine (VirtualBox), thanks to a virtual machine my physical windows installation is becoming useless. Don't know how good games work on virtual machines though...

From what I've read on these forums about VM's, they aren't good at 3D graphics and as such cant run modern games. It's a shame cause that was going to be my initial solution.

---

### Post by Paulmd on 2007-07-27
> **styphon said:**
> I am an XP user about to migrate over to an XP/Ubuntu dual boot. I'm a firm believer of the format windows every 6 months rule. Does Linux follow the same lines or is it more stable than windows and is fine without the format twice yearly?

1) You don't have to do that in windows. 
2) You don't have to do that in linux either.

---

### Post by rich.bradshaw on 2007-07-27
Fat32 is a crappy FS, just use ext3, then use the IFS drivers for windows.

I doubt you will use windows much anyway after installing Linux - there is little point.

---

### Post by LaRoza on 2007-07-27
> **styphon said:**
> ... hence using a Fat32 partition.
I use seperate partitions for storage for many reasons, it is the most sane way to organize your disk. I don't have a seperate /home, I actually don't use it for storage.

---

### Post by LaRoza on 2007-07-27
> **rich.bradshaw said:**
> Fat32 is a crappy FS

It works, albeit sloppily.

FAT32 is the easiest and most reliable, inasmuch as FAT32 is reliable, way to go.

---

### Post by rich.bradshaw on 2007-07-27
Yeah, if you think you will be using Windows as well, it's probably easiest.

I wouldn't make you /home fat32 though - I'd make a seperate partition just for sharing files.

The NTFS-3G drivers are fine as well - I use them everyday and have had no probs.

My personal set up is to have all Documents/Music/Videos etc on an external NTFS drive, then just have the settings in /home and nothing else.

Windows can read NTFS (obviously!) and using NTFS-3G means Linux can as well.

---

### Post by styphon on 2007-07-27
Ah ok, I'll give those drivers a go.

---

### Post by lamar_air on 2007-07-27
> 
Originally Posted by styphon  
I am an XP user about to migrate over to an XP/Ubuntu dual boot. I'm a firm believer of the format windows every 6 months rule. Does Linux follow the same lines or is it more stable than windows and is fine without the format twice yearly? 



> **Paulmd said:**
> 1) You don't have to do that in windows. 
2) You don't have to do that in linux either.

I find that winxp gets slower and slower the longer you go between reformatting, I find I can barely make 6 months with it.  Defrag's help but it's no replacement for a good old xp reformatting.  I only install some basic apps but adding and removing large files often.

---

### Post by styphon on 2007-07-27
> **Paulmd said:**
> 1) You don't have to do that in windows. 

You do if you want to keep performance up.

---

### Post by lamar_air on 2007-07-27
I agree.

---

### Post by rich.bradshaw on 2007-07-27
I disagree that Windows needs to be reformatted every 6 months - I tend to leave mine around a year before reformatting.

It's not that bad, just use CCleaner and another few things, don't install loads of junk etc.

Shame the average user can't do it though - they don't know how to reinstall either...

---

### Post by phr0ze on 2007-07-27
I format my windows once a year too. Toward the end it does get really crappy. Now I have other windows systems that I only use sometimes for special tasks. They go much longer without a format.  If you don't find the need to reinstall windows once or twice a year, then you aren't using it enough.

---

### Post by hessiess on 2007-07-27
id dus if you use it for verry resorse demanding aplications, then it becosmes so slow its uttely usless. my windows install is about a year old and takes 10 munites to load after logging on, then it responce time is worse than a 8 year old win 98 masheen

i am just going to nuke the disk and only run linux, windows is hogging 90 gig of the 110 gig disk

---

### Post by Paulmd on 2007-07-28
> **lamar_air said:**
> I find that winxp gets slower and slower the longer you go between reformatting, I find I can barely make 6 months with it.  Defrag's help but it's no replacement for a good old xp reformatting.  I only install some basic apps but adding and removing large files often.

I've found with win2k and XP if you can avoid the virii, and don't install registry cleaners and such nonsense, that you can go a very, very long time without reformatting.  Then again, It's my job to fix computers (just not in linux, about which I know enough to get myself into, but not out of trouble), so I tend to avoid doing the Really Dumb Stuff that afflicts so many computer users. (Like install HP all-in-one printers with the massively bloated drivers. Those drivers ruin a perfectly good piece of hardware and bog down the computer. They also have bad memory leaks in the utilities.)

Another thing I've found out is that firmware (bios) bugs are more common than people think, and they're often subtle, Often updating the bios can solve a lot of your issues. 

The only reasons Ive really had to reformat are software problems I'm too lazy to fix (like viruses that survive the first attempts at removal). Or to make things easier after a motherboard replacement.

Sometimes also, people reformat because they thing it's just windows, when in reality their hard drive is starting to die. And then they discover that they have a couple hundred bad sectors.

---

