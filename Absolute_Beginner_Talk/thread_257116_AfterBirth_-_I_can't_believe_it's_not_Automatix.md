---
title: "AfterBirth - I can't believe it's not Automatix"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by dyssident on 2006-09-14
I, like every new Ubuntu user, love Automatix. However, I have a few problems with it. Having some time on my hands, I decided to try my hand at hacking some improvements. The product is AfterBirth. It has the same goals as Automatix, but aims toward the following improvements

- Be more sane about packages. Take better advantage of the Debian package system.
- Be more task oriented. If you need AfterBirth, you probably dont know much about which specific programs you want to install.
- Dont hose sources.list. Leave repositiories in sources.list when possible so we can take advantage of future updates.
- Better interface. Attempts to mymic the look of Synaptic updater tool.

Installing

```

wget -O - http://www.voxpopulimedia.com/pub/afterbirth/afterbirth-installer 2> /dev/null | sudo sh -

```

After installation, run `afterbirth` from the command line, from the Desktop or Applications > System Tools > AfterBirth.

Im in need of people with new installs willing to test AfterBirth out; any feedback would be much appreciated.

Current version is 0.1 and is still VERY EXPERIMENTAL. Only use on a system you can afford to lose.

Supported Apps

New System Essentials
- TrueType fonts including Microsoft Core Fonts
- Free Multimedia Codes
- Non-Free Multimedia Codecs
- Ctrl+Alt+Del Support
- Support for common archives (RAR, ACE, 7zip)
Browser Plugins
- Adobe Flash Player
- Java 5
- Acrobat PDF Reader
- Mplayer Plugin
Enhanced Drivers
ATI binary drivers
nVidia binary drivers
Eyecandy
- Gdesklets (Desktop widgets)
- SLAB (Enhanced Gnome menu)
- XGL/Compiz advanced graphics
Fair Use Tools
- DVD ripping packages
- GnomeBaker (Burning software)
- Grip (CD Ripper)
- k3b (KDE Burning software)
- Streamripper (Rip Internet Radio Streams)
File Sharing
- aMule (eDonkey client)
- Azureus (BitTorrent client)
- Bittornado (BitTorrent client)
Instant Messaging
- Gaim2 Beta
- aMSN (MSN Messenger)
- Xchat (IRC client)
Multimedia Applications
- amaroK (Full Featured Media Player)
- Beep Media Player
- Listen Media Manager
- Realplayer
- VideoLan
Security
- Firestarter personal firewall', 'firestarter'], },
- ClamAV antivirus scanner', 'clamav'], },
Windows Compatability
- Windows NTFS support (read-write files with ntfs-3g)
- Wine (Runs Windows programs)
Wireless Essentials
- NetworkManager (Manages wireless connections)
- Ndiswrapper (Windows network driver support)

---

### Post by halcyon on 2006-09-14
> **dyssident said:**
> VERY EXPERIMENTAL. Only use on a system you can afford to **loose**.

ARGH!  It's **lose** not loose! /grammarnazi :p 

Thanks though dyssident, I'll be sure to try it :D

---

### Post by blindluck48 on 2006-09-14
I just did a fresh install of Dapper 6.06 not a minute ago.

Dapper 6.06 (i386)
Alternate CD install (need raid)
Only packages installed are latest updates.


Hardware:
AMD FX-55
1 Gig Corsair XMS DDR-400
Nvidia 6800GT AGP 128mbyte/256mbit
2x 36 gig 10k WD Raptors (RAID0)


My aims - Nvidia drivers
          XGL/Compiz


I'll let you know how it works!

---

### Post by blindluck48 on 2006-09-14
```
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mollyj@theparthenon:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.afterbirth-`date +%Y%m%d%H%M%S`
mollyj@theparthenon:~$ echo 'deb http://archive.ubuntu.com/ubuntu/ dapper universe' | sudo tee -a /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu/ dapper universe
mollyj@theparthenon:~$ echo 'deb http://www.voxpopulimedia.com/debian dapper main' | sudo tee -a /etc/apt/sources.list
deb http://www.voxpopulimedia.com/debian dapper main
mollyj@theparthenon:~$ sudo apt-get install afterbirth
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package afterbirth
mollyj@theparthenon:~$

```

```
mollyj@theparthenon:~$ sudo apt-get update

```

then

```
Fetched 2493kB in 5s (464kB/s)
Failed to fetch http://www.voxpopulimedia.com/debian/dists/dapper/Release.gpg  Could not connect to www.voxpopulimedia.com:80 (62.214.98.57). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```


No go...?

---

### Post by halcyon on 2006-09-14
Worked for me, but I cheated and opened /etc/apt/sources.list with my text editor and pasted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe (had this already)
deb [http://www.voxpopulimedia.com/debian](http://www.voxpopulimedia.com/debian) dapper main 

in it, ran Synaptic, refreshed repositories, and it was there.

---

### Post by blindluck48 on 2006-09-14
> **halcyon said:**
> Worked for me, but I cheated and opened /etc/apt/sources.list with my text editor and pasted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe (had this already)
deb [http://www.voxpopulimedia.com/debian](http://www.voxpopulimedia.com/debian) dapper main 

in it, ran Synaptic, refreshed repositories, and it was there.

Followed same procedure, working now.

Currently installing items.

---

### Post by blindluck48 on 2006-09-14
```

Setting up mplayer (0.99+1.0pre7try2+cvs20060117-0ubuntu8) ...

Setting up mplayer-386 (0.99+1.0pre7try2+cvs20060117-0ubuntu8) ...
Setting up mozilla-mplayer (3.17-1ubuntu1) ...
Setting up mplayer-fonts (3.5-2) ...



INFO: Finished installing Browser Plugins


```

That's where it's stopped for me... and I don't have any cpu activity going on either.

---

### Post by givré on 2006-09-14
```
sudo apt-get update && sudo apt-get upgrade
sudo cp /etc/apt/sources.list /etc/apt/sources.list.afterbirth-`date +%Y%m%d%H%M%S`
# Make sure universe is enabled
echo 'deb http://archive.ubuntu.com/ubuntu/ dapper universe' | sudo tee -a /etc/apt/sources.list
echo 'deb http://www.voxpopulimedia.com/debian dapper main' | sudo tee -a /etc/apt/sources.list
sudo apt-get install afterbirth
```
You forgot to run apt-get update after adding the repo

---

### Post by one_stinky_bum on 2006-09-15
Stops here for me. I presume it may be some network error:
```
DEBUG: Adding debian-multimedia.org key
gpg: requesting key 1F41B907 from hkp server wwwkeys.eu.pgp.net
gpg: key 1F41B907: public key "Christian Marillat <marillat@debian.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
gpg: no ultimately trusted keys found
OK
DEBUG: Adding debian-unofficial.org key
gpg: requesting key 6823D007 from hkp server subkeys.pgp.net

```

---

### Post by dyssident on 2006-09-15
> **givré said:**
> You forgot to run apt-get update after adding the repo

thanks. this is why i try to never post things from memory, only cut+pasting from a terminal.

oh, and thanks for your tutorial on setting up ntfs read+write with ntfs-3g. im basing a package on it.

---

### Post by dyssident on 2006-09-15
> **blindluck48 said:**
> 
INFO: Finished installing Browser Plugins
That's where it's stopped for me... and I don't have any cpu activity going on either.

thats a bit strange. if that was the last group of packages you had chosen to install, you should have gotten a 'Finished installing' message. there is really nothing that could cause a hangup between completion of one package and the start of another. 

when it stopped doing anything did control return to the ui? or to put it more clearly, were you able to check/uncheck boxes, scroll etc the AfterBirth gui?

---

### Post by dyssident on 2006-09-15
> **one_stinky_bum said:**
> Stops here for me. I presume it may be some network error:
gpg: requesting key 6823D007 from hkp server subkeys.pgp.net


sounds like gpg wasnt able to get the key and it just waited forever. could you run the program again to see if it works this time? trying to reload existing keys wont hurt anything.

---

### Post by one_stinky_bum on 2006-09-15
Seems fine now. I went ahead and tried it on my Dapper production box. Nothing is broken so far.

---

### Post by djcronos on 2006-09-15
Fresh install of Dapper 6.06.  I uncommented everything in /etc/apt/sources.list and added the other repository.  Did an apt-get update then an apt-get upgrade, rebooted the machine.

Now I ran AfterBirth, selected everything, and it's installing...

I'll let everyone know how it goes.

---

### Post by djcronos on 2006-09-16
Everything installed perfect, as far as I know.  This is great - good job!

---

### Post by xpod on 2006-09-16
> Thanks though dyssident,

ARRHHHHH....(dissident)=D>

EDIT:...god am i slow today=D>

---

### Post by dyssident on 2006-09-17
> **blindluck48 said:**
> 
My aims - Nvidia drivers XGL/Compiz


I just noticed that you are going for xgl/compiz. the package is not included with the current afterbirth (0.0.1). however, the package currently seems to work pretty well, so you can install it manually. make sure that /etc/apt/sources.list includes 'deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main'. install it with 

```

sudo apt-get update && sudo apt-get install afterbirth-xgl-gnome

```

---

### Post by dyssident on 2006-09-17
AfterBirth is now version 0.0.2

Changes
Much improved handling of apt repository entries
Defaults to saving new repository entries so you can recieve updates for what you installed
New menu item for Gnome Eyecandy (XGL/Compiz, SLAB menu)
Added XGL/Compiz package (afterbirth-xgl-gnome)
Improved ntfs read+write support package (afterbirth-ntfs-3g)

---

### Post by dyssident on 2006-09-17
> **djcronos said:**
> Everything installed perfect, as far as I know.  This is great - good job!

> **one_stinky_bum said:**
> Seems fine now. I went ahead and tried it on my Dapper production box. Nothing is broken so far.

thanks for the feedback. if you have a fairly recent graphics card (ATI and nVidia work better than most), you should try the XGL/Compiz package in version 0.0.2. just select Gnome Eyecandy and install.

---

### Post by dyssident on 2006-09-30
Current version is now 0.1. 

- Totally new interface; better mymics Synaptic updater
- More packages

---

### Post by NoWhereMan on 2006-09-30
(the audience) scree-nies! scree-nies! we want scree-nies! :-D

---

### Post by dyssident on 2006-09-30
Sorry, where are my manners.

When installing:
[IMG]http://www.voxpopulimedia.com/pub/afterbirth/screen-installing.png[/IMG]

That 'Installing Windows' will say 'Installing Windows Support' very soon.

---

### Post by NoWhereMan on 2006-09-30
nice ;)

---

### Post by Rick Henson on 2006-10-09
[SIZE="3"]dyssident,

I have tried all the instructions and so far I can not get this to install. It does not seem to find the distro and then fails to find the package. Is the site still up for this to work?

Looks great in the screen shot, hope this is still supported.

Oh P.S. I have Edgy 64 so not sure wether this might be the problem or not. Thanks in advance for any help with this.[/SIZE]

---

### Post by gn2 on 2006-10-09
> **Rick Henson said:**
> [SIZE="3"]dyssident,

I have tried all the instructions and so far I can not get this to install. It does not seem to find the distro and then fails to find the package. Is the site still up for this to work?

Looks great in the screen shot, hope this is still supported.

Oh P.S. I have Edgy 64 so not sure wether this might be the problem or not. Thanks in advance for any help with this.[/SIZE]

Maybe you should try using XFCE with your Edgy 64?

---

### Post by Breeegz on 2006-10-13
Trying it out...   will post results

---

### Post by DarkN00b on 2006-10-13
[size="3"]For all that is holy, please change the name![/size] [SIZE="1"]I was there when my children were born.[/SIZE] :shock:  *FULL BODY SHUDDER*

---

### Post by puppy on 2006-10-13
I thought the same - it's a nice application but that name is just plain nasty :-#

---

### Post by Sweet Spot on 2006-10-13
> **puppy said:**
> I thought the same - it's a nice application but that name is just plain nasty :-#

I have to agree whole heartedly with the last 2 statements. Even before I saw them, I thought the same thing, but didn't bother to say anything because I was sure that someone else would ! Sounds like a fantastic improvement over automatix, but the name really has to go. I hope you don't take offense to these comments. Perhaps you wouldn't mind some ideas for a new name ?

By the way, have you added anything new to it lately ? Any improvements or fixes etc ? 

Doug

---

### Post by wilberfan on 2006-10-14
Good idea...but I'm not sure it's ready for Prime Time.

I did get it installed, but could NOT get it to work very well.  Lot's of error messages, messed up repositories....   Bleah.

Is there an easy way to uninstall it?

---

### Post by randiroo76073 on 2006-10-15
You might have a fine app but it'll never get out of the starting gate with a name like that.  You could definitely do better with a little thought :)

---

### Post by BLTicklemonster on 2006-10-15
> **puppy said:**
> I thought the same - it's a nice application but that name is just plain nasty :-#

It's better than Placentu.

Anyway, I have automatix one and two, so there's no reason for me to install this, so I did.

Worked fine. 

One thing: can anyone of you find humans make the gui show what we already have installed, and have an uninstall feature? I'd do it myself, you know, but that would take the wind out of your sails (koff bullshikoff koff).

:)

---

### Post by CaveRat on 2006-10-15
> **BLTicklemonster said:**
> It's better than Placentu.

Anyway, I have automatix one and two, so there's no reason for me to install this, so I did.

Worked fine. 

One thing: can anyone of you find humans make the gui show what we already have installed, and have an uninstall feature? I'd do it myself, you know, but that would take the wind out of your sails (koff bullshikoff koff).

:)

That would be nice. Go for it.

---

### Post by BLTicklemonster on 2006-10-15
Surely I jested. Indeed!:mrgreen:

---

### Post by dunetails on 2006-10-15
I'm a bit of a n00b but someone was asking how to remove afterbirth as they had problems.  I had the same errors and then couldnt open synaptic.

I edited the sources.list file and removed all the afterbirth entries, seemed to work.

---

### Post by Sweet Spot on 2006-10-16
I'd really love to see erm, Afterbi... this script refined. I just turned Ubuntu on to a friend, who has dealt with other Linux distros, and didn't find them to be terribly intuitive or good enough to be a replacement for Windows. This time though, I think he'll be pleasantly surprised. Automatix is good, but this one seems to encompass more of what a Windows person would like to see out of the box when switching. 

Doug

---

### Post by az_human on 2006-10-17
Please understand I am not trying to sound snobby or anything as I ask this...

... but what exactly do these programs (Automatix and AfterBirth) do that Synaptic doesn't?  Is the wheel being reinvented here?

---

### Post by Tomosaur on 2006-10-17
Whereas Synaptic lets the user search for stuff they want, scripts like this make downloading and installing the most common / necessary / desirable things much easier. You don't need to go searching one by one for all the stuff that most users want on their systems.

---

### Post by dannyboy79 on 2006-10-17
i'd like to see wifi-radar be a choice of what gets installed as I believe that it handles multiple access points, wep keys, wpa keys better than the other choices.

---

### Post by Zyphrexi on 2006-10-17
yeah plus with synaptic the user has to enable repos by his or herself, whereas in an automatic proggy like automatix, that stuff is set up for you.

Really all that matters (imho) are the repos. I would have absolutely no idea where to go to get them if they weren't right in front of my face, and i'm a linux oldbie. Plus I love seeing new software, and it's hard to download something if you don't know it exists.

---

### Post by BLTicklemonster on 2006-10-17
Synaptic is a bit overwhelming, whereas AB has "what you will want/need" right there for you in plain site. It's like synaptic-lite almost, kinda sorta.

---

### Post by Breeegz on 2006-10-18
> **Breeegz said:**
> Trying it out...   will post results
Well it didn't work well for me, Not that I tried very hard--
errors about repositories and such|
Maybe I'll try after a couple of months...  4 reinstalls of ubuntu after being stupid and stuff like deleting system files/reconfiguring X server (and getting everything to work the way I want again) within 3 months is a little tiresome.

I like the GUI though, nice and simple for us Windoes Babies

?Name Change?

!AfterBuntu!

---

### Post by sktfeelsdapper on 2006-10-18
I can  install it from the repositories.
But when I try and open it it says something about konsole needing some pty read write access?

So yah, anybody want to help here? I just want to try it, I haven't been able to get everything else to work. So why not?](*,) [-( 

EDIT: Breeegz (whatever) Can you believe that I've had Ubuntu (pick flavor here) for a little over a month and have reinstalled close to 6 or 7 times? I feel your pain brother, I feel it.

Stupid alsa.

---

### Post by Breeegz on 2006-10-19
I can beleive it...  I installed 2 computers in August and reinstalled my extra desktop 4 times and my wife's dual boot laptop 2 times.  Eventually I hope to learn enough that I can fix my problems without "starting from scratch".

---

### Post by rowster27 on 2006-10-19
when i run afterbirth from the Desktop or Applications > System Tools > AfterBirth a terminal came out and says: 

(gksudo:31174): Gdk-WARNING **: locale not supported by Xlib

(gksudo:31174): Gdk-WARNING **: cannot set locale modifiers
Gdk-WARNING **: cannot set locale modifiers at /usr/lib/perl5/Gtk2.pm line 59.

what seems to be the problem here guys?:confused:

---

### Post by wilberfan on 2006-10-19
> **Breeegz said:**
> Well it didn't work well for me, Not that I tried very hard--
errors about repositories and such|
Maybe I'll try after a couple of months...  

I like the GUI though, nice and simple for us Windoes Babies



I agree. I didn't try all that hard either--but it DID miss up 2 or 3 things which I managed to repair.   It just doesn't seem 'ready for prime time' yet...

Still...   

I'm rootin' for it (and the name is kinda growin' on me, believe it or not...) 8)

---

### Post by BLTicklemonster on 2006-10-19
You know, I think the knee jerk reaction to the name may wear off. I mean after birth there's what... life. (unless you think you're really cute and say death, because we all know that one already, so pat yourself on the back for being so cunning, go stand in the street and verify your theory, please)

Whoa, tangent... anyway, life, and ... dang. I have no idea where I was going with this.

---

### Post by Sweet Spot on 2006-10-19
So it's still not really stable eh ? Too bad, as it looks like I might have to re-install Ubuntu due to some wierd thing that happened (don't know what it is) which has now caused WMV and divx/Avi. files to not be able to play anymore. Used to play just fine, today in fact. Just happened out of nowhere. 

Maybe Ubuntu is just sick of all the pr0n, eh ? :mrgreen::-k

Doug

---

### Post by Peepsalot on 2006-10-19
> **BLTicklemonster said:**
> You know, I think the knee jerk reaction to the name may wear off. I mean after birth there's what... life. (unless you think you're really cute and say death, because we all know that one already, so pat yourself on the back for being so cunning, go stand in the street and verify your theory, please)

Whoa, tangent... anyway, life, and ... dang. I have no idea where I was going with this.
It should just be renamed to BeforeDeath.  As in "I want to get Ubuntu set up properly before I die."  :rolleyes:

---

### Post by Sweet Spot on 2006-10-19
I reinstalled Ubuntu. Automatix doesn't work with Dapper anymore. And I'm not installing Edgy builds, so, I'm gonna try placenta flush, erm, I mean, afterbirth.... 

Doug

---

### Post by BLTicklemonster on 2006-10-19
> **Peepsalot said:**
> It should just be renamed to BeforeDeath.  As in "I want to get Ubuntu set up properly before I die."  :rolleyes:

Or maybe perhaps the inevitable...


[SIZE="6"]TAXES[/SIZE]


:p

---

### Post by Sweet Spot on 2006-10-19
Well, it didn't go as smooth as I'd have liked it to, but *something* happened.  At the very end, well, at least I guess it was the end, everything just hung. It didn't crash, but just hung. I didn't get a message saying anything like "finished installing, please exit" or anything similar to that. 

Rather, each screen just stayed there, and nothing closed. The last thing it said it was doing, was installing Gnomebaker, but I got no confirmation of it finishing that either. Here's what happened :

>            => `./trebuc32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97

HTTP request sent, awaiting response... 200 OK
Length: 554,208 (541K) [application/octet-stream]

    0K .......... .......... .......... .......... ..........  9%  197.87 KB/s
   50K .......... .......... .......... .......... .......... 18%  483.64 KB/s
  100K .......... .......... .......... .......... .......... 27%  531.98 KB/s
  150K .......... .......... .......... .......... .......... 36%  640.18 KB/s
  200K .......... .......... .......... .......... .......... 46%  595.11 KB/s
  250K .......... .......... .......... .......... .......... 55%  574.08 KB/s
  300K .......... .......... .......... .......... .......... 64%  600.06 KB/s
  350K .......... .......... .......... .......... .......... 73%  591.84 KB/s
  400K .......... .......... .......... .......... .......... 83%  576.36 KB/s
  450K .......... .......... .......... .......... .......... 92%  593.51 KB/s
  500K .......... .......... .......... .......... .         100%  600.12 KB/s

19:34:15 (489.01 KB/s) - `./arial32.exe' saved [554208/554208]

--19:34:15--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/comic32.e](http://easynews.dl.sourceforge.net/sourceforge/corefonts/comic32.e) xe
           => `./comic32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|.. connected.
HTTP request sent, awaiting response... 200 OK
Length: 246,008 (240K) [application/octet-stream]

    0K .......... .......... .......... .......... .......... 20%  196.60 KB/s
   50K .......... .......... .......... .......... .......... 41%  485.57 KB/s
  100K .......... .......... .......... .......... .......... 62%  577.93 KB/s
  150K .......... .......... .......... .......... .......... 83%  596.95 KB/s
  200K .......... .......... .......... ..........           100%  600.16 KB/s

19:34:16 (404.03 KB/s) - `./comic32.exe' saved [246008/246008]

--19:34:16--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/courie32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/courie32). exe
           => `./courie32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646,368 (631K) [application/octet-stream]

    0K .......... .......... .......... .......... ..........  7%  196.64 KB/s
   50K .......... .......... .......... .......... .......... 15%  485.91 KB/s
  100K .......... .......... .......... .......... .......... 23%  581.59 KB/s
  150K .......... .......... .......... .......... .......... 31%  597.90 KB/s
  200K .......... .......... .......... .......... .......... 39%  598.39 KB/s
  250K .......... .......... .......... .......... .......... 47%  580.26 KB/s
  300K .......... .......... .......... .......... .......... 55%  598.04 KB/s
  350K .......... .......... .......... .......... .......... 63%  590.54 KB/s
  400K .......... .......... .......... .......... .......... 71%  582.38 KB/s
  450K .......... .......... .......... .......... .......... 79%  596.94 KB/s
  500K .......... .......... .......... .......... .......... 87%  598.34 KB/s
  550K .......... .......... .......... .......... .......... 95%  572.84 KB/s
  600K .......... .......... .......... .                    100%  597.13 KB/s

19:34:18 (501.96 KB/s) - `./courie32.exe' saved [646368/646368]

--19:34:18--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/georgi32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/georgi32). exe
           => `./georgi32.exe'
Resolving easynews.dl.sourceforge.net... 
Connecting to easynews.dl.sourceforge.net|. connected.
HTTP request sent, awaiting response... 200 OK
Length: 392,440 (383K) [application/octet-stream]

    0K .......... .......... .......... .......... .......... 13%  195.72 KB/s
   50K .......... .......... .......... .......... .......... 26%  476.82 KB/s
  100K .......... .......... .......... .......... .......... 39%  570.89 KB/s
  150K .......... .......... .......... .......... .......... 52%  562.32 KB/s
  200K .......... .......... .......... .......... .......... 65%  602.79 KB/s
  250K .......... .......... .......... .......... .......... 78%  579.56 KB/s
  300K .......... .......... .......... .......... .......... 91%  599.79 KB/s
  350K .......... .......... .......... ...                  100%  600.73 KB/s

19:34:19 (453.68 KB/s) - `./georgi32.exe' saved [392440/392440]

--19:34:19--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/impact32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/impact32). exe
           => `./impact32.exe'
Resolving easynews.dl.sourceforge.net... 
Connecting to easynews.dl.sourceforge.net|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173,288 (169K) [application/octet-stream]

    0K .......... .......... .......... .......... .......... 29%  190.04 KB/s
   50K .......... .......... .......... .......... .......... 59%  493.37 KB/s
  100K .......... .......... .......... .......... .......... 88%  583.93 KB/s
  150K .......... .........                                  100%  562.07 KB/s

19:34:19 (349.44 KB/s) - `./impact32.exe' saved [173288/173288]

--19:34:19--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/times32.e](http://easynews.dl.sourceforge.net/sourceforge/corefonts/times32.e) xe
           => `./times32.exe'
Resolving easynews.dl.sourceforge.net... 
Connecting to easynews.dl.sourceforge.net| connected.
HTTP request sent, awaiting response... 200 OK
Length: 661,728 (646K) [application/octet-stream]

    0K .......... .......... .......... .......... ..........  7%  192.36 KB/s
   50K .......... .......... .......... .......... .......... 15%  469.69 KB/s
  100K .......... .......... .......... .......... .......... 23%  579.93 KB/s
  150K .......... .......... .......... .......... .......... 30%  595.07 KB/s
  200K .......... .......... .......... .......... .......... 38%  597.35 KB/s
  250K .......... .......... .......... .......... .......... 46%  573.18 KB/s
  300K .......... .......... .......... .......... .......... 54%  593.49 KB/s
  350K .......... .......... .......... .......... .......... 61%  593.28 KB/s
  400K .......... .......... .......... .......... .......... 69%  578.02 KB/s
  450K .......... .......... .......... .......... .......... 77%  597.89 KB/s
  500K .......... .......... .......... .......... .......... 85%  597.22 KB/s
  550K .......... .......... .......... .......... .......... 92%  579.36 KB/s
  600K .......... .......... .......... .......... ......    100%  597.40 KB/s

19:34:21 (499.55 KB/s) - `./times32.exe' saved [661728/661728]

--19:34:21--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/trebuc32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/trebuc32). exe
           => `./trebuc32.exe'
Resolving easynews.dl.sourceforge.net... 
Connecting to easynews.dl.sourceforge.net|6
HTTP request sent, awaiting response... 200 OK
Length: 357,200 (349K) [application/octet-stream]

    0K .......... .......... .......... .......... .......... 14%  199.59 KB/s
   50K .......... .......... .......... .......... .......... 28%  460.13 KB/s
  100K .......... .......... .......... .......... .......... 43%  574.94 KB/s
  150K .......... .......... .......... .......... .......... 57%  595.14 KB/s
  200K .......... .......... .......... .......... .......... 71%  590.37 KB/s
  250K .......... .......... .......... .......... .......... 86%  584.66 KB/s
  300K .......... .......... .......... .......... ........  100%  606.62 KB/s

19:34:22 (446.72 KB/s) - `./trebuc32.exe' saved [357200/357200]

--19:34:22--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/verdan32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/verdan32). exe
           => `./verdan32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351,992 (344K) [application/octet-stream]

    0K .......... .......... .......... .......... .......... 14%  192.99 KB/s
   50K .......... .......... .......... .......... .......... 29%  476.53 KB/s
  100K .......... .......... .......... .......... .......... 43%  581.19 KB/s
  150K .......... .......... .......... .......... .......... 58%  595.64 KB/s
  200K .......... .......... .......... .......... .......... 72%  598.83 KB/s
  250K .......... .......... .......... .......... .......... 87%  580.46 KB/s
  300K .......... .......... .......... .......... ...       100%  608.82 KB/s

19:34:23 (443.27 KB/s) - `./verdan32.exe' saved [351992/351992]

--19:34:23--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/webdin32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/webdin32). exe
           => `./webdin32.exe'
Resolving easynews.dl.sourceforge.net... 
Connecting to easynews.dl.sourceforge.net|0... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185,072 (181K) [application/octet-stream]

    0K .......... .......... .......... .......... .......... 27%  199.57 KB/s
   50K .......... .......... .......... .......... .......... 55%  482.64 KB/s
  100K .......... .......... .......... .......... .......... 82%  582.66 KB/s
  150K .......... .......... ..........                      100%  622.25 KB/s

19:34:24 (369.34 KB/s) - `./webdin32.exe' saved [185072/185072]

Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
warning: /usr/share/X11/fonts/TrueType/larabie-deco does not exist or is
   not a directory
warning: /usr/share/X11/fonts/TrueType/larabie-deco does not exist or is
   not a directory
warning: /usr/share/X11/fonts/TrueType/larabie-straight does not exist or
   is not a directory
warning: /usr/share/X11/fonts/TrueType/larabie-straight does not exist or
   is not a directory
warning: /usr/share/X11/fonts/TrueType/larabie-uncommon does not exist or
   is not a directory
warning: /usr/share/X11/fonts/TrueType/larabie-uncommon does not exist or
   is not a directory
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Reading package lists...

dpkg: totem-gstreamer: dependency problems, but removing anyway as you request:
 totem depends on totem-gstreamer (>= 1.4.3-0ubuntu1) | totem-xine (>= 1.4.3-0ubuntu1); however:
  Package totem-gstreamer is to be removed.
  Package totem-xine is not installed.
Reading package lists...

Reading package lists...

Reading package lists...

Reading package lists...

Warning: Tried to connect to session manager, Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Downloading...  done.


Reading package lists...

Warning: Tried to connect to session manager, Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.

Reading package lists...

Reading package lists...


DEBUG: Installing nVidia drivers

Reading package lists...



DEBUG: Card is not ATI. Nothing has been changed
DEBUG: Installing nVidia drivers

Reading package lists...



Reading package lists...

Reading package lists...


Reading package lists...

*** unhandled exception in callback:
***   Undefined subroutine &main::install_grip called at /usr/bin/afterbirth line 332.
***  ignoring at /usr/share/perl5/Gtk2/GladeXML/Simple.pm line 40.


Well, gonna reboot and see what's what.

---

### Post by Sweet Spot on 2006-10-19
Does XGL/Compiz need a specific graphic card in order to do its thing ? I'm only running w/a Nvidia Gforce 2 MMX 400. I don't see anything in reference to xgl anywhere, but I did have AB install it. Also, I'm now being told to update to edgy from the update manager, if I want a full update. Before using AB, this message didn't pop up, and previously, I thought that I was using ALL of the repositories available. Which one (repository list address) is responsible for that ? 

Doug

---

### Post by arnieboy on 2006-10-19
> **Sweet Spot said:**
> I reinstalled Ubuntu. Automatix doesn't work with Dapper anymore. And I'm not installing Edgy builds, so, I'm gonna try placenta flush, erm, I mean, afterbirth.... 

Doug

have u tried
```
sudo apt-get install automatix2
```

---

### Post by confused57 on 2006-10-19
> **arnieboy said:**
> have u tried
```
sudo apt-get install automatix2
```

I really like the layout of automatix2, works great in Edgy, also.
Can't get much easier to install, even manually(copy&paste).

Maybe I'll try AfterBirth, when it's stable.

---

### Post by 5ampl3 on 2006-10-20
a knee jerk is probably what i would consider the reaction. when i first heard it i was like ehhh? odd.. then i thought about it for a few minutes and it hit me.. you mostly use this program after the "birth" of a fresh ubuntu box. i like the idea of this spiffy lil app. cant wait for a smooth running stable release! keep up the good work!

---

### Post by Sweet Spot on 2006-10-20
> **arnieboy said:**
> have u tried
```
sudo apt-get install automatix2
```

I actually have AM2 on my list but here's what I get: And I don't want to mess with Edgy until it's an official/stable release to be honest w/you. So I guess that means I suffer until that's available. I wish you'd have left AM1 up until that time came. 

Doug

---

### Post by Sweet Spot on 2006-10-20
So technically speaking, the only differences between AB and Automatix(2) is which apps they come loaded with (and the GUI which handles the app of course), right ?  I'm only asking because I'm trying to figure out why there need to be two of the same type of scripts (yes, I know ... we like choices), instead of perhaps a colaboration between the two authors to create just ONE killer script instead ? 

I'm just sayin', is all.... 

Doug  ;)

---

### Post by arnieboy on 2006-10-20
> **Sweet Spot said:**
> So technically speaking, the only differences between AB and Automatix(2) is which apps they come loaded with (and the GUI which handles the app of course), right ?  I'm only asking because I'm trying to figure out why there need to be two of the same type of scripts (yes, I know ... we like choices), instead of perhaps a colaboration between the two authors to create just ONE killer script instead ? 

I'm just sayin', is all.... 

Doug  ;)

not sure what u are actually talking about.. but u have installed the edgy version of AX2(Automatix2) on dapper. That should be obvious from the message.
AX2 (Automatix2) is the next gen version of Automatix(1). Automatix1 is being slowly phased out making way for Automatix2 which has many sophisticated security and easy-to-use features none of its peers have. To read more, go to [http://www.getautomatix.com/wiki](http://www.getautomatix.com/wiki)

---

### Post by Sweet Spot on 2006-10-20
> **arnieboy said:**
> not sure what u are actually talking about.. but u have installed the edgy version of AX2(Automatix2) on dapper. That should be obvious from the message.
AX2 (Automatix2) is the next gen version of Automatix(1). Automatix1 is being slowly phased out making way for Automatix2 which has many sophisticated security and easy-to-use features none of its peers have. To read more, go to [http://www.getautomatix.com/wiki](http://www.getautomatix.com/wiki)
  
Are you saying that there is an AX2 version for Dapper ? Because I did not see that, hence my message, which yes, I understood. I just didn't know there was an AX2 version for Dapper.  Also, AX1 doesn't just seem to be being phased out, it seems that it just doesn't work period.  I tried installing it, but it wasn't found in any of the repositories I had installed (which I think were all of them)

Doug

---

### Post by arnieboy on 2006-10-20
> **Sweet Spot said:**
> Are you saying that there is an AX2 version for Dapper ? Because I did not see that, hence my message, which yes, I understood. I just didn't know there was an AX2 version for Dapper.  Also, AX1 doesn't just seem to be being phased out, it seems that it just doesn't work period.  I tried installing it, but it wasn't found in any of the repositories I had installed (which I think were all of them)

Doug
phased out ==> replaced by AX2. 
cannot install !==> does not work
cannot install ==> no longer in the repos (replaced by AX2)

---

### Post by Albi on 2006-10-20
Why compiz and not beryl?

---

### Post by raqball on 2006-10-20
> **Sweet Spot said:**
> Are you saying that there is an AX2 version for Dapper ? Because I did not see that, hence my message, which yes, I understood. I just didn't know there was an AX2 version for Dapper.  Also, AX1 doesn't just seem to be being phased out, it seems that it just doesn't work period.  I tried installing it, but it wasn't found in any of the repositories I had installed (which I think were all of them)

Doug

Cut and past from Automix website:

Installing on (K,X)Ubuntu 6.06 i386,amd64 (Dapper)

Edit your sources.list:

sudo gedit /etc/apt/sources.list 

from terminal

Substitute gedit with the text editor of your choice.

Add the following to your sources.list:

NOTE: Kubuntu/Xubuntu users will need to uncomment all the additional sources as well as add the automatix repository.

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

Now save the file and close it.

Now from terminal do the following:

wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -

To finish off:

sudo apt-get update
sudo apt-get install **automatix2**

---

### Post by Sweet Spot on 2006-10-21
Yeah, I was going to reply after my last post, last night but, I had to go. I did actually see the AX2 for Dapper, but for some reason didn't see it the other day, go figure. 

I guess I'm going to do a clean install of Ubuntu again then...maybe.... I dunno, what do you guys think ? My thing here is, I could just mess around with what I've got until Edgy becomes stable, and then just do a clean/fresh install of Edgy, BUT, when is Edgy going to finally make its stable build appearance ?  That's the deciding factor. Because if it's going to take quite some time, then I'll just do a clean install of Dapper, again. 

Doug

---

### Post by Peepsalot on 2006-10-22
> **Sweet Spot said:**
> BUT, when is Edgy going to finally make its stable build appearance ?
.
[quote=https://launchpad.net/distros/ubuntu/+milestone/ubuntu-6.10]Name:  ubuntu-6.10
Date expected: 2006-10-26
For: Ubuntu Edgy[/quote]

---

### Post by Tethtibis on 2007-06-29
i got it from a repository from "ubuntu ultimate games edition" and ran it, ooh man is it a nice program. :O)

---

### Post by tm24fan on 2007-09-16
> **Tethtibis said:**
> i got it from a repository from "ubuntu ultimate games edition" and ran it, ooh man is it a nice program. :O)

I got it from Ubuntu Ultimate as well, my question though, is whether I should use it having already used Automatix as well.

---

