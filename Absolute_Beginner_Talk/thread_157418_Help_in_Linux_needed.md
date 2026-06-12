---
title: "Help in Linux needed"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by Amorphous_Snake on 2006-04-09
I am new to Linux. I downloaded and installed Ubuntu to my old PC (PIII 1.2 GHz and 256 MB RAM) from curiosity. I really want to learn to use this OS, but I just can't!

I can't do anything! I can't update Firefox, I can't install the latest nVidia drivers, I can't play MP3s or install video codecs. But the worest thing really, is that I can't benefit from others' help. All the sites that I have seen use abbreviations and other things as if a Linux guru is the one seeking help. I don't know what the heck is a RPM... or what to do with tar files!

Please help me understand this OS. I already managed to enable my internet connection on it and I have a 256 Kbit/sec DSL account, so downloading stuff won't be a problem.

---

### Post by htinn on 2006-04-09
You probably want to look at this:

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

### Post by Jimmey on 2006-04-09
In this case, synpatic is your friend =-) 

MP3s are a restricted format, and you'll have to download the non-open souce codecs if you want to play them in the music players you already have. That, or, you could download a new player that already has MP3 support: The two most notable are probably XMMS, and my personal favourite, Xfmedia.

To get these installed, you simply type the following into a terminal window:
> sudo apt-get install xfmedia 
And you can see how this method easily applies to XMMS ( and most other software packages ).

An RPM is an exectuable installer, for RedHat based systems. These, with some work, can be used on Debian based systems ( like Ubuntu ), but, you're better trying to find a .DEB equivalent to this package ( .Deb, Debian, geddit? :P )

Tar files are compressed files ( similar to a zip file, you may have seen on Windows. ). To extract the contents of a tar file, you just right click on it, and depending on where you want to extract it, select the appropriate option.

For the drivers and Firefox, I can only recommend Automatix. I've never had use for Automatix, and have never personally used it. But from what I can gather from these forums, it's your best bet.

Finally, and the most important on this list, is that here is the place where you're most likely to benefit from others help. Try to tackle each problem as it comes - That way, when you do run into trouble, you can just come here, with a 99% chance of your problem being solved ( sometimes within minutes ).

Hope this helps :)

---

### Post by GaFFy on 2006-04-09
Your lucky, enabling internet connection has always been my biggest hurdle with linux distros.  

Have you checked out [http://ubuntuguide.org/](http://ubuntuguide.org/) yet?
It was a huge help getting me started on Ubuntu.

One suggestion for anyone new to linux is to make your searches distro specific.
Searching for answers to your problems randomly using general linux terms can be frustrating.  If your searching for an answer to an Ubuntu problem and you get the answer on a Fedora forum chances are its not gonna work.

---

### Post by trent dillman on 2006-04-09
Welcome to Ubuntu, Linux, and the forums!

First off, Linux is a whole different beast. Imagine what it was like when you first used a computer.

A good place to start is at [http://www.linux.org/lessons/](http://www.linux.org/lessons/)

This will guide you through the basics.

If you have any specific questions, ask them here. There is always someone willing to walk you through your problems, baby steps at a time if needed.

My first Linux experience was being fed up with Windows. I managed to get infected on my dial-up computer using a firewall and antivirus. At first, I played with a Live CD. Then I installed dual-boot. For the first 2 months, I had no Internet access in Linux, and I couldn't get into my external hard drive. Was it frustrating? You bet. But I wouldn't give it up for anything, now.

EDIT: Damn, y'all beat me. :-p

---

### Post by r4ik on 2006-04-09
I would go for this one,

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

Good luck !

---

### Post by Sef on 2006-04-09
check out Restricted Formats in the wiki.

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by catlett on 2006-04-09
Go here and follow the directions. [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405) This is the best thing  since silicon.Iit is a script that someone far smarter than I'll ever be put together to  set up your copy of Ubuntu. When you run the script it will load your system with all the codecs needed for movies and mp3s. It will update your browser and put all the olug ins. Basically it will get your computer where you can do everyday things easily. Now you can search the web, play movies, listen to music and have the tools to tweak your system as time goes by. It is a definate must install sfter you install Ubuntu. Good luck.

---

### Post by r4ik on 2006-04-09
[QUOTE=catlett]Go here and follow the directions. [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405) This is the best thing  since silicon.Iit is a script that someone far smarter than I'll ever be put together to  set up your copy of Ubuntu. When you run the script it will load your system with all the codecs needed for movies and mp3s. It will update your browser and put all the olug ins. Basically it will get your computer where you can do everyday things easily. Now you can search the web, play movies, listen to music and have the tools to tweak your system as time goes by. It is a definate must install sfter you install Ubuntu. Good luck.[/QUOTE]

Don't be offended but you can do all this yourself by reading the suggestions above
also i would not say Automatix is definate must.

---

### Post by exod40 on 2006-04-09
[QUOTE=Jimmey]

To get these installed, you simply type the following into a terminal window:
 
And you can see how this method easily applies to XMMS ( and most other software packages ).

[/QUOTE]


I wrote it on the terminal, but it couldn't find the package: "E: Couldn't find package xfmedia". What can i do? This problem happend with other packages too.

---

### Post by Amorphous_Snake on 2006-04-09
Thanks to all. I never thought that I would get that much of answers in so little time! What guided me was more than curiousity, really. I wanted to change and I also wanted to have, if only for once, a PC having 100% genuine software. I am 20 years old, I used Windows since I was 10! But all this time, I never had an original copy. Sorry Mr. Gates!

Not only that, but I am a Sony fan, and I heard that the PS3 will have Linux pre-installed on it, so that means if I ever want to get a PS3 (in the distant future!) I will have to learn how to use Linux.

---

### Post by Mustard on 2006-04-09
[QUOTE=Amorphous_Snake]Thanks to all. I never thought that I would get that much of answers in so little time! What guided me was more than curiousity, really. I wanted to change and I also wanted to have, if only for once, a PC having 100% genuine software. I am 20 years old, I used Windows since I was 10! But all this time, I never had an original copy. Sorry Mr. Gates!

Not only that, but I am a Sony fan, and I heard that the PS3 will have Linux pre-installed on it, so that means if I ever want to get a PS3 (in the distant future!) I will have to learn how to use Linux.[/QUOTE]

Heh.  Funnily enough I can relate to this.

I started with win98 many years ago and had quite a few applications of questionable legality on my system.  Eventually I got tired of it, and started seeking out good free software, becoming a bit of a freeware junkie.  This led me to discover that a lot of good free software was designed to run on linux systems.  As I jealously watched friends and family switching to XP systems while I remained mired in my win98 install, I decided I needed to find a solution by way of a linux operating system.  I've never looked back since. :)

Lack of money has always been the problem I have with feeding my computing addiction.  Linux is the answer to my prayers. ;)

---

### Post by Amorphous_Snake on 2006-04-09
The thing I want to know is that can you play games in Linux. I mean real games, like FEAR and Civilization IV (not on my PIII system of course), but if I install it on my main PC (P4 2.4 GHz, 1 GB RAM, GeForce 6600), will I be able to enjoy such games, or do I have to stick to Windows on the main PC and leave the old one to Linux?

I have installed Automatix by the way. It's downloading the requested programs. It looks great! Also the unofficial Ubuntu 5.10 guide is good. The same goes for the guide on linux.org. Thanks everyone!

---

### Post by Mustard on 2006-04-09
[QUOTE=Amorphous_Snake]The thing I want to know is that can you play games in Linux. I mean real games, like FEAR and Civilization IV (not on my PIII system of course), but if I install it on my main PC (P4 2.4 GHz, 1 GB RAM, GeForce 6600), will I be able to enjoy such games, or do I have to stick to Windows on the main PC and leave the old one to Linux?

I have installed Automatix by the way. It's downloading the requested programs. It looks great! Also the unofficial Ubuntu 5.10 guide is good. The same goes for the guide on linux.org. Thanks everyone![/QUOTE]

Game play is a difficult issue with linux and for a serious gamer I think the best option is to keep a windows partition installed so that you can still play your games on windows and run a 'dual boot' system.

There are methods of getting windows games working on linux, but they are not always succesful or very easy to implement (especially for someone new to linux).   There exist the amatuer solutions that the hobbyist can undertake to get games working, or there are commercial options. Even the commercial options have limited success.

I can run Homeworld 2, Railroad Tycoon 3, and Masters of Orion 3 on my linux install (using a commercially available application called, Cedega).  I switch to a win98SE install to play Medieval Total War and Rome Total War.

For using windows games on linux you would need to look at an application called 'Wine' (if you want to fiddle around getting them to work yourself), or subscribe to the Cedega service which is a pay for service that offers a software package specifically aimed at running windows games.  Not all games work with Cedega though, so it's value to you will really be a judged on whether it can get 'your favourite games' working.

---

### Post by catlett on 2006-04-09
[QUOTE=r4ik]Don't be offended but you can do all this yourself by reading the suggestions above
also i would not say Automatix is definate must.[/QUOTE]

> 
I can't do anything! I can't update Firefox, I can't install the latest nVidia drivers, I can't play MP3s or install video codecs. But the worest thing really, is that I can't benefit from others' help. All the sites that I have seen use abbreviations and other things as if a Linux guru is the one seeking help. I don't know what the heck is a RPM... or what to do with tar files!

When someone leaves a post like that they are lost. They are having trouble doing basic things. A lot of guides act matter of factly about someone's ability to handle tar files etc. A new to Linux person doesn't have the faintest idea what the guide is talking about. I always direct people to Automatix because it gives someone a working PC right away. Noone knew to Linux is going to be able to do all of this to there system. > 

Capabilities:
1) Installs multimedia codecs
2) Installs all Firefox plugins (java, flash, etc) (except Adobe reader and mplayer)
3) Installs RAR, ACE and UNRAR archive support
4) Installs skype
5) Installs Acrobat reader 7 and firefox plugin for the same.
6) Installs Gnomebaker (CD/DVD burning s/w for GNOME)
7) Installs gftp (FTP client for GNOME with ssh capability)
8) Installs Amule (File sharing program)
9) Installs Frostwire (GPL clone of Limewire)
10) Installs multimedia editors (Audacity (audio), Kino (video), EasyTag (ID3))
11) Installs DVD (dvdrip) ripper
12) Installs Mplayer and mplayerplug-in version 3.05 for Firefox
13) Installs totem-xine, Realplayer, VLC and Beep Media Player (with docklet)
14) Installs Opera Browser
15) Installs Debian Menu (shows all installed applications) (this kills and restarts your gnome-panel without warning u but its a completely harmless operation!)
16) Installs Bittornado and Azureus (Bittorrent clients)
17) Installs Avidemux (Video editing tool) (New version 2.1.0)
18) Enables Numlock on (turns numlock on Gnome startup)
19) Installs Programming Tools (Anjuta (C/C++ IDE), Bluefish (HTML editor) and Screem (Web Development Env.))
20) Install GnomePPP (Graphical Dial up connection tool)
21) Installs MS true type fonts
22) Configures ctrl-alt-del to start gnome-system-monitor (aka windows)
23) Installs Streamripper and Streamtuner
24) Installs NON-FREE audio and dvd codecs
25) Installs ndisgtk (WiFi configurator Graphical user interface)
26) Upgrades Open Office to 2.0 (final version), installs openoffice clipart and installs OO2 thumbnailer.
27) Adds 3 nautilus scripts (open any file with gedit as root; open a nautilus window as root in any folder; open gnome search tool in any folder (Right click in a nautilus window and look under "scripts")
28) Installs SUN'S JAVA JRE version 1.5
29) Installs SUN'S JAVA JDK version 1.5
30) Installs wine (u need to run winecfg manually after installation)
31) Enables ejection of CD when CDROM drive button is pressed.
32) Installs AMSN 0.95 (MSN client with webcam support)
33) Installs Mercury Messenger (Java based MSN client with webcam support)
34) Installs BUM (Boot-up Manager)
35) Installs DCPP (Linux DC++ client)
36) Installs sbackup (Backup and restoration solution)
37) Installs Listen Music manager (with repository)
38*) Installs firestarter (GNOME firewall frontend) and adds firestarter to GNOME startup
39*) installs gdesklets (GNOME eyecandy) and adds gdesklets to GNOME startup
40*) Gamepads (Makes USB gamepads work)
41*) Turns DMA ON on Intel and AMD machines (needs a restart)
42*) NVIDIA cards (Detects Nvidia cards and installs drivers) (Needs a restart)
43*) Adds midi capability to your Ubuntu box Ubuntu with Automatix installed has more capabilities than a Windows install. An Automatix enabled system will keep a new person around. They can do all the average things(some people may even get more because they might not have dvd codes on windows). Then they can learn to use Linux. A good number of people leave because they can't get their system comfigured. So they keep booting back into windows to watch a movie, go to a web site that uses flash,load their mp3 etc. Now they don't have to leave Ubuntu. And the more time they spend in Ubuntu the more they  will learn about their  Linux sytem. But to think someone who says they "can't do anything" can set up their system like Automatix, well I don't think any further reply is needed.
Automatix is similar to Dell and Gateway etc loading their computers with dvd codecs and i tunes. They don't ship a straight XP install and say "you can easily follow our website directions to install anything that is missing from your setup". 
If someone has previous exposure to Linux or Unix based systems then I don't think you'll need Automatix. But if your fresh from windows and you've never seen a Gnome desktop before, I'll say it again...Automatix is a must install.

---

### Post by Amorphous_Snake on 2006-04-09
Thanks Catlett.

I have installed Automatix and it is in the process of downloading all the updates.

I would also like to add a note that I noticed about Linux in general: You can't survive without internet. In Windows, you can install the OS and go on and on without the need to upgrade the system or download a program. But in Linux, it's the complete opposite.

I have a friend who did just like me; installed Ubuntu on his old PC. But he has a dial-up connection, which, for some reason, can't work with Ubuntu. Is there any chance that I can transfer the files that Automatix downloaded on my system so that he can benefit from them (MP3 play and all) without having to leave his PC on for a month?!

---

### Post by r4ik on 2006-04-09
[QUOTE=catlett]When someone leaves a post like that they are lost. They are having trouble doing basic things. A lot of guides act matter of factly about someone's ability to handle tar files etc. A new to Linux person doesn't have the faintest idea what the guide is talking about. I always direct people to Automatix because it gives someone a working PC right away. Noone knew to Linux is going to be able to do all of this to there system.  Ubuntu with Automatix installed has more capabilities than a Windows install. An Automatix enabled system will keep a new person around. They can do all the average things(some people may even get more because they might not have dvd codes on windows). Then they can learn to use Linux. A good number of people leave because they can't get their system comfigured. So they keep booting back into windows to watch a movie, go to a web site that uses flash,load their mp3 etc. Now they don't have to leave Ubuntu. And the more time they spend in Ubuntu the more they  will learn about their  Linux sytem. But to think someone who says they "can't do anything" can set up their system like Automatix, well I don't think any further reply is needed.
Automatix is similar to Dell and Gateway etc loading their computers with dvd codecs and i tunes. They don't ship a straight XP install and say "you can easily follow our website directions to install anything that is missing from your setup". 
If someone has previous exposure to Linux or Unix based systems then I don't think you'll need Automatix. But if your fresh from windows and you've never seen a Gnome desktop before, I'll say it again...Automatix is a must install.[/QUOTE]

The link,

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

Has Automatix included plus several howto's to get on the way if a person wants to start "doing things" on there own.
When a person can install Automatix he/she knows the way to the Terminal so it is a very usefull link to use in the future.
We disagree about Automatix beeing a must install no big deal just different opinions.

---

### Post by Amorphous_Snake on 2006-04-09
Thanks a lot guys. Now Ubuntu makes sense!!! I used Automatix to get lots of programs and audio/video codecs. Now I can run MP3s and XVID/DIVX files.

But, does you need to download and install all these programs again if I create a new user? I want to create a new user for my little brother.

Also, say Firefox got a new update. Will the update be available in Automatix at the same time it is available for individual download? And how can you update Automatix or include other programs in it?

---

### Post by catlett on 2006-04-09
> Has Automatix included plus several howto's to get on the way if a person wants to start "doing things" on there own.
When a person can install Automatix he/she knows the way to the Terminal so it is a very usefull link to use in the future.
We disagree about Automatix beeing a must install no big deal just different opinions.
I hope I didn't come off wrong. I love the fact that there are so many people who respond on these forums and interact. I like to debate and prove my point or be proven wrong. I hope my tone wasn't combative. If it was I apologise. It has taken me a long time to learn you can debate and not argue. You can compete and not fight. And you can disagree and not dislike. I respect your opinion very much and hope I didn't offend you at all.

Back to the post. He should be able to connect with dial up. But if he can't I don't think Automatix can work. Automatix (when it runs) goes on the internet and downloads all those programs and then install them. If he can't access the internet he'll have to do it manually. Pretty much you would have to download the packages he'll need (usually they are tar. files, these are like zip. files). Copy them to disk and then load them onto his system and install each program from it's tar file.
I have broadband so I don't personally know but I'm almost positive I've seen peopl post about being on dial up. Well at least you can have fun.

---

### Post by halitech on 2006-04-09
actually there is a way to use Automatrix on a computer with dialup or no internet but it requires having a friend with highspeed and a burner. check out this thread for more info:

[http://ubuntuforums.org/showthread.php?t=136955&page=3&highlight=automatrix+cd](http://ubuntuforums.org/showthread.php?t=136955&page=3&highlight=automatrix+cd)

you will need a working bit torrent client though to get it

---

### Post by r4ik on 2006-04-09
[QUOTE=catlett]I hope I didn't come off wrong. I love the fact that there are so many people who respond on these forums and interact. I like to debate and prove my point or be proven wrong. I hope my tone wasn't combative. If it was I apologise. It has taken me a long time to learn you can debate and not argue. You can compete and not fight. And you can disagree and not dislike. I respect your opinion very much and hope I didn't offend you at all.

Back to the post. He should be able to connect with dial up. But if he can't I don't think Automatix can work. Automatix (when it runs) goes on the internet and downloads all those programs and then install them. If he can't access the internet he'll have to do it manually. Pretty much you would have to download the packages he'll need (usually they are tar. files, these are like zip. files). Copy them to disk and then load them onto his system and install each program from it's tar file.
I have broadband so I don't personally know but I'm almost positive I've seen peopl post about being on dial up. Well at least you can have fun.[/QUOTE]

You did not offended me whatsoever so no need to apologise.
Important thing is that Amorphous Snake has his system up and running from what i read.
Let this be the end of this little inside thread discusion.
See you around :)

---

### Post by Amorphous_Snake on 2006-04-09
My Ubuntu now runs as good as my Windows XP! But can I only create folders in /home?

Also can anyone recommend a good defragmentation tool and also a checkdisk (scandisk) tool?

If I create a new user for my little brother, would he have all the programs I just downloaded from Automatix, or would I have to reinstall them?

---

### Post by Mustard on 2006-04-09
[QUOTE=Amorphous_Snake]My Ubuntu now runs as good as my Windows XP! But can I only create folders in /home?[/QUOTE]

Ubuntu is a true multi-user environment, so yes, it does restrict the users access to their own $HOME directory.  The first user (your account) is a superuser though, and as such can use the 'sudo' command to execute commands as an administrator that give them access to any part of the system.  When logged in as your user, you are able to access all the adminstrator menu choices simply by using your user password.

> Also can anyone recommend a good defragmentation tool and also a checkdisk (scandisk) tool?

Linux does a good job of keeping fragmentation low, with its ext3 filesystem, so its not necessary for fragmentation tool to be used on the drive.  The system is also set up to automatically test partitions after they have been mounted 30 times (without checks).  It will also do so if there is some type of unusual shutdown through power outage.  It is possible to manually check the filesystem (of an umounted partition) using the fsck command.  Generally this is done from a live CD, as fsck cannot be run on a mounted filesystem and your main filesystem is most certainaly mounted when you running Ubuntu.

> If I create a new user for my little brother, would he have all the programs I just downloaded from Automatix, or would I have to reinstall them?

Your little brother in most cases would have access to the same programs that you installed.  There are exceptions to the rule however, and it depends on what method you used to install an application (or in this case, what method Automatix used).    It is most likely that you would not create a superuser account (administrator account) for your little brother though, so he would not have access to commands and menus that are reserved for the administrator (yourself).


I've simplified some of these explanations for the purposes of keeping it short, but you can certainly find out more about these things as you learn bit and pieces about your system.

---

### Post by Amorphous_Snake on 2006-04-10
Thanks.

I only asked the above question (defragmentation and scandisk) because my system hang. I was using Firefox and then everything freezed. I had to press the reset button on my case.

---

