---
title: "cant run any .exe file"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Pebbie on 2007-07-25
i just downloaded the ubuntu. it can run, work well. but i cannot install anything from my CDs. not even my mother board's driver. 

can any1 tell me wat kindda file ubuntu cant run?

and how to run those .exe file in ubuntu?

---

### Post by skymera on 2007-07-25
the .exe can be run using Wine from the repositoires

but im not sure you need the driver for the mother board though =S

---

### Post by Mornedhel on 2007-07-25
Pebbie,

Am I understanding correctly that you have actually installed Ubuntu, and that you are not running it from the LiveCD anymore ? If this is the case, then you do not need to install anything from vendor-provided hardware drivers CDs, everything is included in Ubuntu. As a side note, those .exe files are Windows executables and will not run under Linux - not that you need them to, so everything's all right. If you later need to run Windows executables and cannot find Linux equivalents, check the Wine package and other related threads in this forum.

Did you manage to get Internet access on Ubuntu ? If so, good. If not, please post details on your configuration (more precisely about your network).

---

### Post by Pebbie on 2007-07-25
i went to wine webpage. all they give me is some code. how to use the code?

and... i seen u guys showing those code, sudo, etc, etc ,etc, where u guys type it to? i dun c any place i can type code into.

---

### Post by Pebbie on 2007-07-25
@ mornedhel

yes, i can connect to internet. im using ubuntu right now.

---

### Post by mjwhitfield on 2007-07-25
You don't need those motherboard drivers.  I strongly advise that you don't run them under WINE.

---

### Post by kinematic on 2007-07-25
> **Pebbie said:**
> i just downloaded the ubuntu. it can run, work well. but i cannot install anything from my CDs. not even my mother board's driver. 

can any1 tell me wat kindda file ubuntu cant run?

and how to run those .exe file in ubuntu?

at least do a small amount of research before jumping in to it,i know you're new to this but this is just silly.(LINUX IS NOT WINDOWS).
if everything is working you don't need to hunt for drivers expect if you have a graphics card on wich you want to enable 3d but those are more then likely in the repository.
as for those windows .exe. files...what programs are they for and we'll se if there are alternatives.

---

### Post by Hatchetfish on 2007-07-25
First of all, you probably don't need the motherboard drivers if all your system hardware is recognized and functioning, so don't worry about them.*

Second, windows programs (.exe's) don't run under linux without [WINE]("https://help.ubuntu.com/community/Wine"), and some of them don't run *with* WINE.  Before messing with a lot of your windows stuff, my advice is to see what's out there to replace it in ubuntu.  A good place to start with that is here: [Windows Application Equivalents]("https://help.ubuntu.com/community/WindowsApplicationsEquivalents").

If you can't find an equivalent on that page, *then* worry about WINE.  or, try a bit of research.  either post here about the specific program you want a replacement for, or what i often find works is a google search on the type of program and the term 'gpl', for example looking for a photoshop replacement (which is GIMP, btw) searching 'photo editing gpl' will find open source photo editors, many (most) have native linux versions.

Hopefully that clears up the confusion, but if not, ask.  Somebody probably knows.

* If any hardware *isn't* working, you probably still don't need the drivers on the cd that came with the board, but instead drivers for linux, which you can get help with here if you explain what isn't working.  Hopefully everything works though, and it sounds like it does.

---

### Post by Mornedhel on 2007-07-25
> **Pebbie said:**
> i seen u guys showing those code, sudo, etc, etc ,etc, where u guys type it to? i dun c any place i can type code into.

The GNOME terminal is under Applications, Accessories. (Someone please correct me on this, I don't have it there anymore, I only use the keyboard shortcut...) Alternatively, you can type Alt-F2, and in the box type gnome-terminal. Ask back if there is anything in particular you need help for, that's what we're here for. Your system does not sound like it needs anything more installed (except probably the 3D acceleration if you have any).

---

### Post by Pebbie on 2007-07-25
so.. basically the thing with window and linux is the same except the file type and user interface? in term of program

everything works fine so far, just need a lil bit of configuration to suit my visual need. 

so... i need to run WINE if i wan to install my game? and i suspecting my graphic card is not working. i have a intergrated graphic card which comes with my mother board if my mother board is working, the graphic card should be rite? coz when i view video, they seems sort of "chocky"

how to see what program is running in my computer? and the workload of my CPU. i mean the function of alt+ctrl+del for window

i have finish donwload WINE, but my add/remove application window seems freeze. is it normal for install a new application?

---

### Post by Hatchetfish on 2007-07-25
I wouldn't worry about the command line quite just yet, but when you need it, you can open a terminal by going to the Applications menu, then Accessories, and picking Terminal.

---

### Post by mlentink on 2007-07-25
The "code" you are referring to are commands
Go to Applications>Accessories>Terminal and open it. You will see a prompt ending with $. After this prompt you can type the commands, or even paste them after you have copied them.

Usually, the first thing I do when I install a new piece of software is to move my mouse over all of the menu's so I can see what options there are. This usually tells me a lot about what the software can do for me. Take a look at the "Applications", "Locations" and "System" menu's at the top left of your screen. Also, have a look at the sticky posts in this forum. Thirdly, I think you will find the [wik]("http://https://help.ubuntu.com/")i a great help in learning your new system.

Welcome to the free world!

---

### Post by Mornedhel on 2007-07-25
At the core Windows and Linux are * very * different, but that's probably not something you need to know right now.

For the basic home user, there is little to no difference once everything is set up, except for this interesting fact : you don't have to pay anything for (almost) anything Linux, and I mean that in the legal way.

The core functionalities of your graphic card are apparently working, but could you be a little more specific as to what kind of video card it is ? (Apart from ATI drivers I have very little experience in that field so we'll need someone else to chime in.)

And what game do you want to run ? It may be working under Wine, it may not, it may be usable after some tweaking, or it may already have been implemented for Linux (hey, we're gamers too).

---

### Post by Hatchetfish on 2007-07-25
> **Pebbie said:**
> so.. basically the thing with window and linux is the same except the file type and user interface? in term of program

Not exactly, but probably close enough for now.  There are actually many differences between the two systems, mostly stemming from linux following the traditions of UNIX, as opposed to windows not really following any tradition except garage hobbyists in the 70's.  Most of the differences are advantages over windows though, once you understand the reasons for them.  Until then, some of them might be a little irritating.

> everything works fine so far, just need a lil bit of configuration to suit my visual need. 

so... i need to run WINE if i wan to install my game? and i suspecting my graphic card is not working. i have a intergrated graphic card which comes with my mother board if my mother board is working, the graphic card should be rite? coz when i view video, they seems sort of "chocky"

how to see what program is running in my computer? and the workload of my CPU. i mean the function of alt+ctrl+del for window

Themes, Desktop Background (wallpaper) and Fonts, under System>Preferences will probably cover the basics of getting it to look right.

as for a ctrl+alt+del equivalent, well, don't do ctrl+alt+del.  since you're asking i'm guessing you figured it out, it does a near instant reboot.  what you're after is the system monitor, available under System>Administration>System Monitor

as for graphics card, i'm going to defer to others, because my personal experience with it is a bit unusual.

---

### Post by cmeeks2662 on 2007-07-25
Find out what chip set the video carf is running and ask here these people helped me out before with this problem.
There are thousands of packages AKA programs you can install and again you can ask for suggestions here .
Though Linux is more stable, less of a resource hog and just plane out cool the best feature about Ubuntu is right here in these forums.  Good luck have fun and ask for help when you need it.

---

### Post by Pebbie on 2007-07-25
im not sure wat graphic card im using as i always just put in my mother board's driver and click install.

im not sure wat game i will play in the future, but now, i aint playing any. WoW perhaps. now that my add/remove application is freeze.

i click the box which show Wine Windows Emulator. then i download some kindda file, 32 file to be exact (i think). when the file finish running, the add/remove application freeze up. and there's this description which show tat "Wine Windows Emulator cannot be installed on your computer type (i368). Either the application requires special hardware features or the vendor decided to not support your computer type."

---

### Post by Mornedhel on 2007-07-25
OK, go to a command line (the gnome-terminal thing) and type lspci, then copy-paste the results here. (Copy-pasting can be tricky in the terminal until you get the hang of it. Now to discover a wonderful feature of Linux : you can copy-paste by selecting text, then pressing your middle mouse button. Or, you can copy from the terminal with Ctrl Shift C - because Ctrl C in the terminal already is used for something.)

---

### Post by Pebbie on 2007-07-25
i click alt+f2 then a bar come out. i type in lspci. then the bar automatically close. i dunno y. i did it 3 times. even click the Run in terminal box. the same thing happen. is it because of my freezed add/remove application?

---

### Post by Mornedhel on 2007-07-25
Nonono, you have to type lspci in a terminal. The terminal is the thing that pops up when you type gnome-terminal in that box you've been typing lspci in.

---

### Post by Pebbie on 2007-07-25
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

btw, the internet connection in my area is sort of not stable, it goes on and off for 1sec every few couple minute. normally it will spoilt my downloads if i download without a download manager. will it affect my updates and application download and install?

---

### Post by benx009 on 2007-07-25
> **Pebbie said:**
> 00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

btw, the internet connection in my area is sort of not stable, it goes on and off for 1sec every few couple minute. normally it will spoilt my downloads if i download without a download manager. will it affect my updates and application download and install?

if you're looking for video hardware acc., i think you're out of luck.  i don't think the via unichrome series (or any via chipset for that matter) has an official linux video driver.

---

### Post by Mornedhel on 2007-07-25
> **Pebbie said:**
> btw, the internet connection in my area is sort of not stable [...] will it affect my updates and application download and install?

No. It may interrupt the retrieval, but if it does, just try again (and all already downloaded packages won't even have to be downloaded again). Under no circumstances can it interrupt the installation once every package has been retrieved.

This is your video card :
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

I'm no expert on these, but from what's in the repositories, I'd say you need the  xserver-xorg-video-via or xserver-xorg-video-unichrome package installed. I don't know exactly which one though. Could you check in Synaptic (in the terminal, type gksudo synaptic - it will prompt you for your password) if one of those two packages is installed already ? It would have the leftmost checkbox colored green if it is.

(And could someone more knowledgeable with VIA stuff provide some input ?)

---

### Post by Pebbie on 2007-07-25
> **benx009 said:**
> if you're looking for video hardware acc., i think you're out of luck.  i don't think the via unichrome series (or any via chipset for that matter) has an official linux video driver.

so you are saying tat, if i want to do anything which require my video card, i need to switch into my window?

---

### Post by maldojr88 on 2007-07-25
pebbie....
it is normal to install stuff on ur linux computer. 
but what these guys are trying to tell you is that there are other software availiable for linux 
distributions that do the same things as for a windows computer.
For instance.....in a windows you use aim(Instant Messenging)...rite? good....and when you
download the program you get a .exe file. This is an executable to windows pc. 
Now linux by default doesnt run .exe files. You can you WINE to be able to run those executables
or you can just do what I and many people do. 
You find a program for linux that does the same thing. 
I found gaim...which is the linux version of aim...and it works almost exactly if not better than the windows aim and you can see your friends and they can see you.


Now what exactly is it that you need?

---

### Post by Mornedhel on 2007-07-25
> **benx009 said:**
> if you're looking for video hardware acc., i think you're out of luck.  i don't think the via unichrome series (or any via chipset for that matter) has an official linux video driver.

Apparently there is : xserver-xorg-video-via shows up in the repositories.

> **maldojr88 said:**
> Now what exactly is it that you need?

I was going to ask the same thing. Ask here if you need Linux equivalents to Windows programs.

---

### Post by Pebbie on 2007-07-25
@ mornedhel and maldojr

i know there's alot of replacement to the stuff tat i normally use. wat i wan to learn is, set up my ubuntu and know how to find the stuff. 

most of the program i see in add/remove application, they always show "(application name) cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

and some guy said that the USB port is not working. is it true?

where can i get server-xorg-video-via? and what is a repositories?

---

### Post by Mornedhel on 2007-07-25
That's weird. Did you install a 64 bit version of Ubuntu ? Alternatively, you should try Synaptic, it's less user-friendly (fewer pretty images), but gives you more control and lists precisely every package.

Edition for the USB port : Unless you're * really * out of luck, it should work out of the box.

---

### Post by Pebbie on 2007-07-25
im not sure which version of Ubuntu i have. but 95% of the stuff in add/remove application show tat i cannot install em. tat really upset me. where can i get the Synaptic?

the donwload link for me to download the ubuntu is [http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-i386.iso](http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-i386.iso)  i dunno which version is it. then when i run it, i allocated 100gb for this and 40gb for swap. then there's 100 update, which i have finish update. yet, the problem of cannot install application still not solved

---

### Post by Mornedhel on 2007-07-25
OK, so you do have the i386 version. Now why Add/Remove says you don't is beyond me. Synaptic is already installed on your Ubuntu, just go to the terminal (remember, gnome-terminal ?...) and type gksudo synaptic. Hope Synaptic won't choke on architecture conflicts. Anyone ever experienced this ?

Wait wait wait, what ?! 40 GB for swap ?! Swap is there for your extra memory needs, in case you don't have much RAM. If you have under 512MB RAM, use twice that swap (twice the RAM, that is). From 512 MB and up, use the same amount of swap (again, the same quantity of memory that your RAM provides). I have 1GB RAM and never need to swap unless I'm rendering a 3D drawing in Blender AND watching a video AND browsing the internet AND having plenty of other apps open. You never need more than 1GB swap. That's 39GB you have sitting there.

---

### Post by jd65pl on 2007-07-25
Here are some videos on installing using ubuntu, [http://jamie.dumbill.googlepages.com/l_how_to_vids.html](http://jamie.dumbill.googlepages.com/l_how_to_vids.html)

There is a sticky on the beginner forum on installing [http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

---

### Post by threeonethree on 2007-07-25
hahahahaha this thread is funny rofl

---

### Post by Pebbie on 2007-07-25
no no, it says tat the application CANNOT INSTALL ON i386. which i doubt about it. why would ubuntu release something tat most application cannot support?

for example, i type in wine, it shows this:
" Wine Windows Emulator
This application is provided by the Ubuntu community.
Wine Windows Emulator cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

about the swap thinggy, nvm about it, i can nvr finish using my hard disk space anyway...

---

### Post by threeonethree on 2007-07-25
its not problem with ubuntu but its problem with ur computer or some mistakes that u made while installing

---

### Post by threeonethree on 2007-07-25
can u tell me how did u install ubuntu? downloaded and burned from website ? or ordered a cd ? or burrowed from friend?

---

### Post by Mornedhel on 2007-07-25
OK, first things first, Wine * can * install on your computer, maybe it's just Add/Remove that's being stubborn about it. I have Wine installed on mine, and it's defintely i386.

What I am suggesting is, try to install it from Synaptic, using the instructions I gave you. Just search for "wine" there and check the package, then Apply. If you're lucky, Synaptic will install it just as Add/Remove would have, otherwise search the forum for relevant threads.

Edition : threeonethree, please edit your posts to avoid doubleposting, and use proper English (no IMspeak).

---

### Post by El Viejo Lobo on 2007-07-25
> **Pebbie said:**
> so.. basically the thing with window and linux is the same except the file type and user interface? in term of program

everything works fine so far, just need a lil bit of configuration to suit my visual need. 

so... i need to run WINE if i wan to install my game? and i suspecting my graphic card is not working. i have a intergrated graphic card which comes with my mother board if my mother board is working, the graphic card should be rite? coz when i view video, they seems sort of "chocky"

how to see what program is running in my computer? and the workload of my CPU. i mean the function of alt+ctrl+del for window

i have finish download WINE, but my add/remove application window seems freeze. is it normal for install a new application?

To see the working  apps you go to "**System/Preferences/Sessions"**.
To kill a freezed  Apps you can go to the Panel Right click then click on Add to panel and look for **Desktop & windows** and look for an icon that is called **Force quit**.
I used Wine to install I. Explorer on Ubuntu but did not liked the performance of it.

To see the Hardware recognized by Ubuntu go to System/Preferences/Hardware Information.  You should  see your Graphic card  in that list.
Congratulations for coming to Ubuntu, I am sure that you will enjoy it 100% in a short time.

---

### Post by Pebbie on 2007-07-25
i download from the link i provide just now. then i burn it into empty cd with 12X spd. take about 4mins. i restart my computer with windows's installation cd. then i delete and re-allocate the partition i have. i have 400gb space, i make 100gb for ubuntu, 40gb for swap, then 150gb for storage, then the remaining for future use. after i re-partition, i re-boot and replace windows cd with the cd tat i just burn. then i just follow the instruction with the installation. after tat, i just start this thread. 

is it possible tat my hardware cannot support ubuntu? im using pentium 4 3.06 ghz HT, 2X SATA, 2gb ram, and a micro ATX mother board which i believe the serial is GA-8VM800PMD-7550RH by gigabyte

ok, now im in the synaptic package manager. there's couple of white box and green box. what are they stand for? and some of it have a ubuntu logo.  in short, how to use the synaptic package manager?

---

### Post by hyper_ch on 2007-07-25
Hi there

First of all I recommend you to have a read here:  [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

It's an excellent guide for beginners. That will tell you the most basic things.

---

### Post by jd65pl on 2007-07-25
Why dont you try searching the forum for your answers. You seem somewhat confused about basic concepts perhaps reading up on them may help you. There is plenty of information on installing on the forums try reading it.

---

### Post by Mornedhel on 2007-07-25
> **Pebbie said:**
> in short, how to use the synaptic package manager?

Look for interesting packages, using Search if necessary. Green means already installed, white is not installed yet. "Mark for installation" if you want to install. Lather, rinse, repeat. (Ubuntu-flagged packages are the ones available on the install CD.)

Once every interesting package is marked for install, click Apply, and wait until installation is complete.

---

### Post by Pebbie on 2007-07-25
@ jd65pl

most of the thing in forum i cannot understand as im not really good at computer.

---

### Post by Pebbie on 2007-07-25
ok. thx. i really learn alot in this thread. thx mornedhel and others for teaching me get used to lunix

i found this website. can any1 explain what are they talking about? tat guy using the same video card as me and having the same problem. but i dun understand what are they talking about.

[http://www.linuxquestions.org/questions/showthread.php?t=488245](http://www.linuxquestions.org/questions/showthread.php?t=488245)

---

### Post by pointyblue on 2007-07-25
.

---

### Post by Mornedhel on 2007-07-25
Good grief pointyblue, you should have read the rest of the thread before posting that...

---

### Post by pointyblue on 2007-07-25
@Mornedhel

I know, sorry. I read the first page and didn't see there were several more than the one I read - until right after I pressed the submit button!  Duh!

Guess I was a little too eager to help out...

:lolflag:

---

### Post by Pebbie on 2007-07-25
so... any1 can help me sort of translate wat are they saying? simplify thier terms and those

---

### Post by Pebbie on 2007-07-25
bump

---

### Post by thefoolisme on 2007-07-25
I think you really need to read the information in the links that the others have provided.  The forum group has no problem clarifying information, in fact, they love to do that.  Or point you in the right direction when you can't find it, but just saying you're not good at computers...sounds like you just don't feel like reading.  There is SOOOOOO much information out there about Ubuntu, Wine, basic linux, installation instructions...you need to do some reading while you set up your machine.

---

