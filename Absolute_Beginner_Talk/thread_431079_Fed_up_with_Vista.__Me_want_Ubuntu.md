---
title: "Fed up with Vista.  Me want Ubuntu"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by the lemming on 2007-05-02
Hello

I have decided to take the plunge with Ubuntu after a not so happy experience with a legitimate version of Vista.  However I have a few questions before I finally commit and install a new Operating system onto my PC and Laptop.  If my questions are in the wrong forum then I would appreciate it is somebody could point me towards the correct place to post them.

I am a home user who wants to use my computer for the following:

surf the internet
chat to mates on-line
send and receive mail
use applications similar to Microsoft Office
Listen to my MP3 collection
copy and watch DVD's
manage and edit my photo collection
use my British Ordinance Survey Digital Maps 

Before I plunge in with my questions it may help if I mention the specs of my computers.  The Pc spec is:
Dual Boots XP and Vista (Vista soon to be dumped.
AMD 64 3400+ processor 2205MHz
2gb RAM
Nvidia GeForce FX 5700 Graphics card
1 DVD Re-write drive
1 DVD Read only drive
2 Hard Drives 112GB with several partitions all of which are NTFS
2 External Hard Drives with several partitions and all of which are NTFS
Belkin 802.11g wireless card model F5D 7000uk
Medion TV-Tuner 7134 MK 2/3

My Laptop spec is

Intel 1596 Mhz processor
1.5GB RAM
33GB Hard Drive with one partition which is NTFS
1 Dual Layer DVD Re-Write drive
Internal Intel Pro/Wireless 2200BG network card

Hopefully all this information will be of some use to help me achieve a smooth transition away from a completely Windows dependant environment.  I am hoping to be able to dual boot my computer and Laptop so that I have a foot in both camps.

With all this in mind here are my questions.  The first one is, is it wise to keep my filing system as NTFS or is it better to re-format them to FAT 32?  I've had some success with G-Parted in the past partitioning my drives for various projects.

Should I install a firewall, anti-virus and spyware?  If I should could somebody recommend any applications?

Even though my PC has a 64 bit processor is it better to stick with a 32 bit operating system or would I get good results installing the 64 bit version?

My main passions are photography, listening to MP3's, watching DVD's  and using my digital maps.  I have learnt that I can find Linux based applications for almost all my needs except for my digital maps which will probably have to be run through XP. However I have been told about something called WINE.  Would I be able to use this tool to view my digital maps and download them onto my Garmain GPS?

At the moment I can not access the internet, via my wireless router, while using the Live CD.  Would this change when I install Ubuntu onto my PC?

And my last question is would I still be able to clone my Hard Drive by using Norton Ghost 2003?  At the moment Vista does not let me, which is one of the annoying reasons for me wanting to get rid of Vista.

I realise that this is a very long posting for somebody's first ever posting and I thank you for your patience and persistence in reading it all.

I would greatly appreciate any help or advice that anybody could offer me with my first ever attempts to move away from a Windows dependant environment.  I have seen the future of Vista and I don't like how it has slowed down my enjoyment of tinkering on my computer.

Thank you

---

### Post by oilchangeguy on 2007-05-02
did you purchase your computer with vista preinstalled? or did you upgrade from xp? if you upgraded just reload the original xp setup, and dual boot with ubuntu. keep whatever version of windows and dual boot. there's alot that you do that will be hard if not impossible to do in linux.

---

### Post by bobplano on 2007-05-02
for most of the stuff you want to do, almost any OS will work. about the DVD's though, it may be harder since some are encrypted. Ubuntu comes with a firewall called iptables and you can install a GUI for that called firestarter. you don't need anything else than that unless you want to, because there are no known working viruses for linux. the 32-bit version has easier installs(for wine and flash) and more support than the 64-bit one. i'm not sure about your maps, but if you want to you can run windows on a virtual console so any non-3d program will work. mp3's will need codecs that aren't already there but there are repos with them making it a lot easier to get them. you might have to use ndiswrapper for that wireless card, which "wraps" the windows drivers so ubuntu can use them. there are programs for disk images and disk dumping in linux and an easy place to get these would be synaptic or sourceforge.just remember ubuntu isn't windows so don't get discouraged if something doesn't work, the wonderful people here will be able to help you do most anything.  good luck with ubuntu

---

### Post by the lemming on 2007-05-02
> **oilchangeguy said:**
> did you purchase your computer with vista preinstalled? or did you upgrade from xp? .

Hello

My computer came installed wit XP which I keep ticking over by using Norton Ghost 2003.  A couple of months ago I bought an OEM of Vista Home Premium which does not like me using Ghost or even legitimate DVD's, but it will let me watch DVD's which I have un-encrypted myself.  Weird.

This weekend I intend to wipe all traces of Vista off my computer and install Ubantu which will duel Boot with XP.  I've read that XP will become unsupported by Microsoft in 2009 and I'm hoping to learn something gradually before then.

At the moment all my hard drives are formatted with NTFS.  Do you know if I should re-format them to FAT 32 or if I can keep them as NTFS?

Cheers

---

### Post by sawjew on 2007-05-02
For viewing your maps, depending on the format they are in, you may be able to use one of the GIS packages available for linux.  Quantum GIS, or Qgis as it is sometimes called, is available in the repositories.  I use Qgis at home and I am able to open and work on Mapinfo files from work although Qgis is not as full featured as Mapinfo.  Qgis also has a plugin to enable interfacing with GPS units.  If you want the latest Qgis though, which has quite a few more editing tools, you will have to compile it from source as the version in the repositories is rather old, just get the latest source code from the Quantum GIS web site.

There is also Grass GIS and SAGA GIS, both of which are very full featured but not as easy to use as Qgis.  All of these are available in the repositories.

I have recently completely erased my Windows partition and now use 64 bit Ubuntu exclusively and have not yet had the need for any Windows apps.  The only problem I have had with 64 bit compared to 32 bit is the lack of a reliable browser plugin for java.

Good luck with the change.

Added: (forgot about this) I would stick to NTFS for your other partitions as it tends to be a bit faster and more stable than fat32.  By default Ubuntu has read only access to NTFS partitions when it is installed (unless this has changed with Feisty, but I don't think so).  It is quite easy to set up read/write access with ntfs-3g (I think it was ntfs-3g, I don't use it anymore because I no longer have any Windows partitions) just search the forums and you will find a how-to.  The other thing is, if you use ext3 for your linux install you can install a driver in Windows (ext2 IFS I think it's called) which will enable you to mount your linux partition in Windows so you can read and write directly to it from Windows.  I did this and then just pointed My Documents on Windows to the Documents directory on my Ubuntu partition and shared all my documents.

---

### Post by the lemming on 2007-05-02
> **bobplano said:**
> for most of the stuff you want to do, almost any OS will work. about the DVD's though, it may be harder since some are encrypted. Ubuntu comes with a firewall called iptables and you can install a GUI for that called firestarter. you don't need anything else than that unless you want to, because there are no known working viruses for linux. the 32-bit version has easier installs(for wine and flash) and more support than the 64-bit one. i'm not sure about your maps, but if you want to you can run windows on a virtual console so any non-3d program will work. mp3's will need codecs that aren't already there but there are repos with them making it a lot easier to get them. you might have to use ndiswrapper for that wireless card, which "wraps" the windows drivers so ubuntu can use them. there are programs for disk images and disk dumping in linux and an easy place to get these would be synaptic or sourceforge.just remember ubuntu isn't windows so don't get discouraged if something doesn't work, the wonderful people here will be able to help you do most anything.  good luck with ubuntu

Thank you for mentioning about a fire wall and the fact that there are no known viruses.  That bit really cheered me up:) 

My mapping system is by a company called Memory Maps and it uses British Ordanence Survey information.  This means that it can display maps in 2D and 3D form and allow me to do fancy stuff with them.  I don't mind re-booting my PC into XP for this as it is a very usefull application indeed.

I do have one more question which I forgot to mention in my OP and that is the quality of my JPEGS.  They don't appear as sharp or as clear as when I view them in Windows.  Do you think this can be improved on when I finally install Ubuntu onto my PC?

Thanks

---

### Post by gazj on 2007-05-02
Phew a few q's there i will answer what i know, hopefully someone else will fill the rest of the gaps.

You will be able to all of your tasks in ubuntu in some way or another, the only one i don't know about is your maps.  Wine may work, but it's completely hit and miss.  Keep a windows partition around until you see how this goes at least.

The specs of your pc should be fine, you should have no troubles as far as i can see.

As for your laptop, they are always the ones that cause trouble.  The wireless chipset you speak of i have heard of it working, although you may need to do some research and go through a lot of tinkering before it will work.  There is something called ndiswrapper that will most likely work if all else fails.  This basically uses your windows drivers for the wireless device, converts them into something linux can understand.  (not sure of the exact science behind it but it works).

The fat32 ntfs thing,  really your desision.  The problem as you probably know is the 4gb file size limit with fat32.  The upside is fat32 can easily be read in linux.  NTFS is more tricky but it can be done, although i am not sure how reliable.  Fat32 has been proven over years with linux.  Many people have windows on NTFS, then a seperate FAT32 for documents shared by windows and ubuntu.

You really don't need any anti virus or ant spyware software on your ubuntu system, some may say you do if you share documents with your windows os so to protect that, but your windows av should pick it up if it is scanning in realtime before it does any harm.  I really don't see the point.  If your router has a firewall built in it that should suffice.

You can pretty much backup linux with open source software that makes the use of norton ghost redundant.  I have never tried using it on ubuntu or any linux so i don't know the real answer, but i see no need.  (probably a no, as ubuntu uses the ext3 filesystem not NTFS or FAT32)

```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```

that one command would backup your whole system to a file called backup.tgz,it seems daunting but it's not when you have been using linux for a while.

A full thread about this found here [http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

If you like tinkering Ubuntu/Linux is the place to be.  Be prepared to learn and have fun while you do it.  Things may seems alien for a start, but after a little while it all makes sense.  You will wonder why you ever used windows. :)

Good Luck

---

### Post by the lemming on 2007-05-02
> **sawjew said:**
> you will have to compile it from source as the version in the repositories is rather old, just get the latest source code from the Quantum GIS web site.


Thanks for the advice on maps.  I think that messing around with source codes is way over my head.  I can barely programming in BASIC on my Commodore Vic 20 over 22 years ago.  :( 

Cheers

---

### Post by bobplano on 2007-05-02
for the formatting you need to resize your partition and then format the free space as ext3 (which doesn't really need defragging). you can have information on a fat32 partition if you want. as for the source code compiling it really isnt as hard as you think. you do need the packages (possibley from [www.packages.ubuntu.com](www.packages.ubuntu.com)) cpp, gcc, build-essential, linux-headers-(your kernel)

---

### Post by the lemming on 2007-05-03
> **bobplano said:**
> for the formatting you need to resize your partition and then format the free space as ext3 (which doesn't really need defragging). you can have information on a fat32 partition if you want. as for the source code compiling it really isnt as hard as you think. you do need the packages (possibley from [www.packages.ubuntu.com](www.packages.ubuntu.com)) cpp, gcc, build-essential, linux-headers-(your kernel)



Morning

After reading all the replies so far I am beginning to get a little confused about what sort of filing structure I should have for a Linux based operating system.  I'm a simple happy user of windows who has picked up a few buzz words and bits of jargon from surfing the net and chatting with IT chaps at work but my skills and abilities are limited to basic stuff such as knowing how to use a mouse button.  

.I've just read about ext3 and my little brain has just gone pop.  With my extreemly limited knowledge of computers in mind could somebody please recomend a simple method for setting up my hard drives?
I am going to keep the XP partition as NTFS.  But is is the data partitions and Ubuntu partitions that are giveing me a head ache.  I am hoping to be able to use any data created by myself in both XP and Ubanutu.  And my last question is what sort of size partition should I allocate to Ubanutu?

---

### Post by darkrose on 2007-05-03
windows on NTFS
Ubuntu on ext3 - give it at least 6GB, which will give you some room to play with.

For your shared partition the best option is either:
NTFS - and install ntfs write support in ubuntu (ntfs-3g is in the repositories so is easy to install)
ext3 - and install ext3 support in windows (available from [http://www.fs-driver.org/](http://www.fs-driver.org/) )

---

### Post by adza on 2007-05-03
lemming,

  after reading another of your posts (looking for other distro's) i wouldn't start out with linux by trying to dump your familiar OS straight away.. too much pressure to learn too much straight away (and believe me - you've just embarked on a learning curve!).. dual boot for a while, let yourself get confident with being able to surive totally on linux, knowing that you have your XP (or whatever) partition there for when you just need to get something done... one thing i will say though, there ain't no windows communities like this one :)

---

### Post by tact on 2007-05-03
Hey there...

I think a lot of people have answered a point or two here and there so between all the posts so far you might have most of the answers you were looking for (??)

I would just clear up a few details for you if I can....  someone mentioned leaving drives formatted as NTFS but they were not sure if Fiesty has the needed driver to read/write to NTFS.   It does, so you can leave all your windows partitions formatted to NTFS.  

I used to dual boot XP and ubuntu (Edgy and now Fiesty).   My XP partition was NTFS and I had no issues sharing data.  I kept the XP partition a while until I had seen how well XP runs in a VM on Fiesty...  hehehe it runs very well!  

Because XP ran so well in a VM (and because I only needed it to run a mapping program (AussieExplorer) to connect to my garmin GPS - I am not a gamer) I ended up getting rid of the XP partition.  Whenever I need to run a windows program that will not run under WINE I just use XP in a VM.

I have the same intel networking chipset as you and both Edgy and Fiesty found it and supported it (WiFi and wired adapters)  no problem.  Fiesty is better.

---

### Post by tact on 2007-05-03
...oh ya.

Don't crack your head over what formatting to use in ubuntu.  the default ext3 is just fine.

If you plan to keep the XP partition and get rid of Vista...  just use whatever tool you have in XP (disk manager) to delete the vista partition and leave the space "unallocated".   Let ubuntu install to the unallocated space.  It should install GRUB bootmanager automatically to allow you to select ubuntu or XP at boot time.

How much space to allocate....  thats a wide open field...  as some kind of indicator:
My ubuntu only laptop with 80G HDD is set up with 3 partitions...
6Gigs  for "root" ...  after a few months hard use and constantly adding new programs its still only half full.
2.2 Gigs for swap (approx 1.5 times my RAM size)
the rest is allocated to "/home"
(all ext3 formatted)

---

### Post by Lucifiel on 2007-05-03
Oh, fat32 partitions are good because they can be recognised by Windows without having to install some extra software, to enable Windows to see them.

However, be warned that sometimes, copying files to a fat32 partition might result in permission errors and other errors. In which case, your only choices are to try again using more advanced methods like running gksudo nautilus in Terminal(this enables you to run as root temporarily), copy to another partition or if that doesn't work, convert the partition to a different format like ext3 instead of fat32 . 

When I say "running as root", it's the equivalent of using a master key or a combination code to access some secret hideout door, that not everyone can access. :P

Edit: The only problem is that for partitions using another type of file format other than ntfs and ext3, you will need to install software on Vista or XP so that it can see them. And if you're running Vista, this could be a problem as Vista is still quite new. What I mean is: there's likely software for seeing ex3 partitions on Vista but if you run into any problems, it could be a bit difficult trying to fix them or to get help for them. 

Here's a guide to installing extifs so Vista/XP can see your ext3 partitions. 
[http://www.go2linux.org/node/51](http://www.go2linux.org/node/51)

---

### Post by neotasic1 on 2007-05-03
Your system is very similar to mine. (Although I am not sure about your video card - can't remember if mine is a Nvidia or ATI.)   Also, your computer needs appear to be almost identical to mine with the exception of your digital maps.  I have successfully installed Feisty Fawn 7.04 onto my desktop (64 bit version) with no significant problems.  

I chose to dual boot my machine (XP and Linux) to allow me access to those windoze programs I haven't yet found Linux substitutes for yet,  (although the range of programs is vast and I have no doubt that when I bother looking I will find them) and to let me do what I know how to do in windows until such time that I learn how to do it in Linux.  I expect it will take time to become as proficient in Linux as I have become in windows, so this dual boot path allows me to get things done in either system without tearing my hair out when I make mistakes.  I could be wrong, but it seems to me it makes more sense to use windows programs in windows, rather than an emulator - particularly if you have access to windows anyway.

For your needs:-

Surf the internet - Firefox which is part of the default Gnome desktop installation
Chat with mates - Gaim also installed by default
Send and receive mail - Evolution (looks almost identical to Outlook 2003)also part of the default Ubuntu Gnome installation (or you can install Mozilla Thunderbird or others if you prefer)
MS Office - OpenOfficeOrg - very similar and mostly compatible with Microsoft Office - contains word processor, spreadsheet, presentation application, database, drawing program - has some extra features and is part of the default installation
Listen to MP3's - Totem - part of the default installation (but I added GXine for DVD playback and copy - easier to configure for commercial DVD playback
Watch DVD's - you have many choices - but I chose to install GXine because I am new to this and it seemed the best documented and easiest to configure.
Copy DVD's - K9copy - works like DVD shrink, but faster - there are many others (maybe even better) but this one is easy to use.
Burn DVD's - GnomeBaker.
Manage and edit photos - the default F spot photo manager seems pretty good to me, along with GIMP (photoshop substitute) but if you need something more sophisticated and you have a broadband connection probably all that you need is just a few mouse clicks away.

I have toyed with Linux on an off over several years - each time in the past I found the learning curve a bit steep but still worthwhile but still too fiddly for me to ditch windows. This latest distribution is the best and easiest I have ever installed and I am 98% convinced I will convert fully to Linux.

Regarding the filesystem, just allow the installation program to create the partitions it needs by resizing one of your hard drives. It will do this by reclaiming unused space. Allow the installation program to use the default settings.  You will find it creates a partition formatted to ext3 filesystem (think of this as a LInux NTFS) and a separate swap file.  I found the guided automatic partitioning very user friendly but I suppose it depends how much exposure you have had to partitioning software.  Good idea to Ghost your machine first or backup your essential data, as partitioning can do massive damage if you get it wrong.  I would not bother to create any FAT32 partitions, as linux is capable of reading NTFS partitions after you have mounted them.  This is easy to do in Ubuntu, and as an added safety feature, it makes these mounted partitions read only so you can copy, read etc but won't irreversibly damage any files on your windows partitions.  Incidentally, your windows installation will not see your linux partitions or data.

I cannot vouch for whether your wireless network will work trouble free, as I personally have a hard wired network (which I find is faster, more secure and more reliable than wireless -  even in windows), and I note from the numerous postings here that this can be a source of problems.  I have installed a previous version of Ubuntu (cant remember which but think it was Breezy Badger) on a Dell inspiron laptop with a built in wireless network card, and it worked "out of the box" after some minor configuration.  I personally found it easier to set up in Linux than in Windows.  

I would recommend you keep one of your computers with windows installed exclusively and a working internet connection, until you have a reliable internet connection in Ubuntu otherwise you will find it hard to ask for or look for help.  (and you will need to - this is not windows and you will have much to learn) It is a pain to reboot your computer to load windows to go on the internet if your wireless card doesnt work straight away in Linux.

I would recommend taking the plunge with a dual boot installation and just playing with it and learning as you go.  These forums are a great source of help and information as is Google, but you have to put effort into this yourself.  Read all the stickies at the beginners forum - follow the links and you will learn much - I certainly have.

If your experience is like mine the installation will be trouble free - you will have most of what you want there and then.  Other bits of what you want you will need to put in some effort.  These include - MP3 playback (possibly)  DVD playback and ripping - definitely - but these days not that hard - start with the Ubuntu help accessible by clicking on the ? icon in the top tool bar.  

Is it been worth it?  For me - absolutely.  I now have a significantly faster system, that does 98% of what I need with minimal fuss, I get to interact with a community of helpful people and contribute, learn many new things, and free myself of the constant need to upgrade equipment and software at great expense on a regular basis. Hopefully, it will be the same for you.  Good luck and welcome.

---

### Post by neotasic1 on 2007-05-03
One other thing, if you intend ripping and copying disks, you will probablly need to have about 30gig space or more for linux to allow you to store the ripped files and the ISO image until after you have burned it to disk.  Otherwise your DVD copying will fail with an inscrutable error message.  I started with 20gig and ended up with this problem.

---

### Post by Lucifiel on 2007-05-03
For listening to songs, I use songbird for the quality is almost on-par with Winamp's. Here's a tutorial on how to install it. :) 
[http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

For watching movies and avis and so on, I use Mplayer. Totem is a good choice too, although it is a bit too simplistic for my tastes, as in, it can't handle certain file formats. And some of my AVI files refused to play in Totem while Mplayer handled them beautifully. 

For email: thunderbird . You can try evolution but it's too complicated for my tastes.

For browsing: Firefox. If Firefox proves unstable like too many crashes and freezes, etc., then try Swiftfox. It's an optimised version of Firefox. If Firefox isn't up to your taste, try Opera.

For chatting: either Pidgin or Kopete. There are many other choices, though. :) 

For antivirus, while you don't need it most of the times, if you receive plenty of files from Windows users, I suggest that you try ClamAV with KlamAV as the GUI frontend. It's not going to be fun to find out later on, that you've got a couple of virus infestations on Ubuntu. :P

---

### Post by Nevis on 2007-05-03
> **darkrose said:**
> windows on NTFS
Ubuntu on ext3 - give it at least 6GB, which will give you some room to play with.

For your shared partition the best option is either:
NTFS - and install ntfs write support in ubuntu (ntfs-3g is in the repositories so is easy to install)
ext3 - and install ext3 support in windows (available from [http://www.fs-driver.org/](http://www.fs-driver.org/) )

I've done this exact same thing as a new Ubuntu user 2 months ago. It has worked perfectly for me. I never dual boot anymore but keep a VMWare copy of Windows handy just in case.

I found that wireless will be difficult to get working on certain chipsets (ie ones who won't release opensource firmware for a driver). Others work great. I have a Belkin F5D7010 which uses a Broadcom chipset... bad news for me. If yours is similar it'll be a challenge for you.

---

### Post by the lemming on 2007-05-03
may I say thank you to everybody for your swift and helpful advice in my quest to replace a Windows Operating System.

Thankfully I have made a Ghost image of XP before installing Vista which means that I can wipe all traces of it from my computer before installing Ubuntu.  

from what I've gathered, and I hope I'm correct in this, is that I can access documents created in Open office and Microsoft Office when using Ubuntu or XP if they are on a seperate partition to both operating systems?

Once again

Cheers

---

### Post by neotasic1 on 2007-05-03
Short answer is yes you can as long as the partition you save these documents to is one that both operating systems can read and understand. Linux can read (and write if you care to configure it) to NTFS partitions.  So can XP.  Both can read and write to FAT32 partitions although you may run into issues with permissions with FAT32 so this may not be the best option.  Windows can access ext3 partitions with the installation of software (name escapes me - but I saw it on a link in these forums), so I suppose even a Linux partition would serve.

If you need to access your files from both MS Office and Open Office you will need to save them in .doc .xls etc format so the MS side of things can open them.  You will find that although compatibility is very good - it is not perfect some formattiing can be very slightly different, and if you use macros, they may not fully be supported.  Otherwise it is all good.

---

### Post by Nevis on 2007-05-05
> **neotasic1 said:**
> Windows can access ext3 partitions with the installation of software (name escapes me - but I saw it on a link in these forums), so I suppose even a Linux partition would serve.

You're probably talking about [Ext2 IFS]("http://www.fs-driver.org/"), an installable file system for Windows. Works great the little I've used it. Truth is since I installed Linux I never boot to Windows anymore. :-)

---

### Post by jimrz on 2007-05-05
> **oilchangeguy said:**
> did you purchase your computer with vista preinstalled? or did you upgrade from xp? if you upgraded just reload the original xp setup, and dual boot with ubuntu. keep whatever version of windows and dual boot. there's alot that you do that will be hard if not impossible to do in linux.

HUH! ... don't know about your ordinace maps, but all the rest is no problem on ubuntu. hardware looks fine for linux, except that you might want to see which chipset your desktops wifi card has and research how it works (or just try the live cd and see how it does). the intel card in your laptop will be fine.

---

### Post by DerArzt on 2007-05-07
im not sure if anyone has mentioned this yet, but the belkin f5d7000 wireless card is a royal pain in the ***. I have a version 3000 of that card and due to it i am writing this post from xp. if u plan on using any sort of encryption beyond wep, be prepared for a pain

---

### Post by the lemming on 2007-05-07
> **DerArzt said:**
> im not sure if anyone has mentioned this yet, but the belkin f5d7000 wireless card is a royal pain in the ***. I have a version 3000 of that card and due to it i am writing this post from xp. if u plan on using any sort of encryption beyond wep, be prepared for a pain


Thanks for the tip.

I think I will have to ditch WAP and go for WEP.

But that is the least of my problems at the moment.

Cheers

---

