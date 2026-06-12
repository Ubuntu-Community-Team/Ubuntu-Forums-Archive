---
title: "REALPLAYER11 install"
date: 2008-08-03
forum: Apple Hardware Users
---

### Post by bilbobagins on 2008-08-03
Hi in  trying to install Realplayer 11, all is well until the line.   sudo ./RealPlayer11GOLD.bin..  . this produces a syntax error
eg "(" any ideas I have used this before on my amd box and its ok but this G4 is a pain. and yes I have tried MPlayer got sound no vision and all I watch is the sky at night (sad but true)!!! this is from UBUNTU GUIDE hardy edition

---

### Post by motsteve on 2008-08-03
> **bilbobagins said:**
> Hi in  trying to install Realplayer 11, all is well until the line.   sudo ./RealPlayer11GOLD.bin..  . this produces a syntax error
eg "(" any ideas I have used this before on my amd box and its ok but this G4 is a pain. and yes I have tried MPlayer got sound no vision and all I watch is the sky at night (sad but true)!!! this is from UBUNTU GUIDE hardy edition

Don't get mad at me for asking, but did you make the file executable after you downloaded it?

Don't blame the G4.  We're lucky to have any support at all for PPC, even though loads of people are now on PS3's.

---

### Post by bilbobagins on 2008-08-04
Thanks for  your interest,yes i did using.  chmod 770 RealPlayer11GOLD.bin
 This is the full script as per Ubuntu guide and others  
 chmod 770 RealPlayer11GOLD.bin
  sudo ./RealPlayer11GOLD.bin
the problems come in the second line.the terminal reports back syntax error. 
I have used this before on my other pc which is an AMD dual core running 32bit addressing and no probs.I have even tried freshconfused: install ,so what is going wrong?
 a confuzed Bilbo!  :confused:

---

### Post by motsteve on 2008-08-04
I have Ubuntu running on a VM on iMac, but that is i386 and RealPlayer is installed so I think that is where I first ran the RealPlayer.bin file and it installed.  I also have OpenSuse running on my PPC and it has Realplayer installed, but I think that OpenSuse comes with that installed regardless of platform.  I normally run Debian on my PPC and when I go there and try to run the RealPlayer.bin file I get a really useful message of "can not run the binary file".  Ubuntu and Debian are very closely related although I believe Debian has been around forever.  I'll dig around on the Realnetworks site and see if I can find a clearly stated PPC binary file that will run on a PPC base.

---

### Post by brambles on 2008-08-05
Not sure what you've tried but 

[http://forms.helixcommunity.org/helix/builds/?category=realplay-current](http://forms.helixcommunity.org/helix/builds/?category=realplay-current)

choose your ppc binary

When downloaded, chmod +x bin file and sudo ./real...blah.bin

Used to work for me, but that was when I had iBook

Cheers

---

### Post by loboc on 2008-08-05
Realplayer in linux is just the helixplayer with different icons you might try copying the plugins and codecs that result from the installation for use with the helix player which is apt-get install-able

---

### Post by motsteve on 2008-08-05
> **brambles said:**
> Not sure what you've tried but 

[http://forms.helixcommunity.org/helix/builds/?category=realplay-current](http://forms.helixcommunity.org/helix/builds/?category=realplay-current)

choose your ppc binary

When downloaded, chmod +x bin file and sudo ./real...blah.bin

Used to work for me, but that was when I had iBook

Cheers

I went here and it looks like a really good site to have available for all the platforms.  Thanks for putting it up here on the forum.  PPC has not been updated in a while (7/24) so I have to keep looking for it, but at least now I have a starting point.  

Thanks again.

---

### Post by oswaldkelso on 2008-08-05
[https://wiki.ubuntu.com/PowerPCFAQ#head-4c512dc1fe442052d2bb368afeb4f8add9f83d71](https://wiki.ubuntu.com/PowerPCFAQ#head-4c512dc1fe442052d2bb368afeb4f8add9f83d71)

I don't think Realplayer 11 works but 10 works fine and you can setup xine to play the Realplayer stuff by default.

If you just want to watch the sky at night just down load it from iplayer (yes it can be made to work on linux  ppc )

---

### Post by motsteve on 2008-08-05
> **oswaldkelso said:**
> [https://wiki.ubuntu.com/PowerPCFAQ#head-4c512dc1fe442052d2bb368afeb4f8add9f83d71](https://wiki.ubuntu.com/PowerPCFAQ#head-4c512dc1fe442052d2bb368afeb4f8add9f83d71)

I don't think Realplayer 11 works but 10 works fine and you can setup xine to play the Realplayer stuff by default.

If you just want to watch the sky at night just down load it from iplayer (yes it can be made to work on linux  ppc )

As soon as I get an answer (on another thread in this forum) on my partitioning of my hard drive to install Ubuntu, I'll be able to try out Realplayer there, but right now I'm trying to install it in Debian because it's the closest distro I have to Ubuntu running. I'm having a problem of no development libs installed on my ppc. None of the bin files play.  I've been looking around for the development repository for ppc, but so far I've gotten no where.  I think once I get all the lib's installed, then the suggested download files will start to work.

---

### Post by oswaldkelso on 2008-08-05
I just followed the link I gave you. It worked in Debian Etch and after I upgraded to Lenny/Testing............ 

I just installed it and am listening to bbc Radio1 as I type. You need to change libstdc++5-3.3-dev to a later version. I installed  libstdc++6-4.2-dev 

Yon may need the debian-mutimedia repos in your sources.list?

deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) lenny main 
deb-src [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) lenny main 

debian867:/home/ok# apt-get install libstdc++5 libstdc++5-3.3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++5-3.3-dev
debian867:/home/ok# apt-cache search libstdc 
lib64stdc++6 - The GNU Standard C++ Library v3 (64bit)
lib64stdc++6-4.1-dbg - The GNU Standard C++ Library v3 (debugging files)
lib64stdc++6-4.2-dbg - The GNU Standard C++ Library v3 (debugging files)
lib64stdc++6-4.3-dbg - The GNU Standard C++ Library v3 (debugging files)
libgmp3-dev - Multiprecision arithmetic library developers tools
libstdc++5 - The GNU Standard C++ Library v3
libstdc++6 - The GNU Standard C++ Library v3
libstdc++6-4.1-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.1-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-4.1-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-4.1-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-4.2-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.2-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-4.2-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-4.2-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-4.3-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.3-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-4.3-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-4.3-pic - The GNU Standard C++ Library v3 (shared library subset kit)
debian867:/home/ok# apt-get install libstdc++5 libstdc++6-4.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
T
The following extra packages will be installed:
  cpp-4.2 g++-4.2 gcc-4.2
Suggested packages:
  gcc-4.2-locales g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  gcc-4.2-multilib libmudflap0-4.2-dev libgcc1-dbg libgomp1-dbg
  libmudflap0-dbg libstdc++6-4.2-doc
The following NEW packages will be installed
  cpp-4.2 g++-4.2 gcc-4.2 libstdc++5 libstdc++6-4.2-dev
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 7828kB of archives.
After this operation, 25.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://ftp.uk.debian.org](http://ftp.uk.debian.org) lenny/main cpp-4.2 4.2.4-3 [2749kB]
Get: 2 [http://ftp.uk.debian.org](http://ftp.uk.debian.org) lenny/main gcc-4.2 4.2.4-3 [444kB]                         
Get: 3 [http://ftp.uk.debian.org](http://ftp.uk.debian.org) lenny/main libstdc++6-4.2-dev 4.2.4-3 [1260kB]             
Get: 4 [http://ftp.uk.debian.org](http://ftp.uk.debian.org) lenny/main g++-4.2 4.2.4-3 [3081kB]                        
Get: 5 [http://ftp.uk.debian.org](http://ftp.uk.debian.org) lenny/main libstdc++5 1:3.3.6-18 [295kB]                   
Fetched 7828kB in 1min10s (111kB/s)                                                        
Selecting previously deselected package cpp-4.2.
(Reading database ... 116593 files and directories currently installed.)
Unpacking cpp-4.2 (from .../cpp-4.2_4.2.4-3_powerpc.deb) ...
Selecting previously deselected package gcc-4.2.
Unpacking gcc-4.2 (from .../gcc-4.2_4.2.4-3_powerpc.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.4-3_powerpc.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.4-3_powerpc.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-18_powerpc.deb) ...
Setting up cpp-4.2 (4.2.4-3) ...
Setting up gcc-4.2 (4.2.4-3) ...
Setting up libstdc++5 (1:3.3.6-18) ...
Setting up libstdc++6-4.2-dev (4.2.4-3) ...
Setting up g++-4.2 (4.2.4-3) ...
debian867:/home/ok# cd Desktop/
debian867:/home/ok/Desktop# chmod +x realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin
debian867:/home/ok/Desktop# ./realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin
Extracting files for RealPlayer installation........................

Welcome to the RealPlayer (10.0.5.756) Setup for UNIX
Setup will help you get RealPlayer running on your computer.
Press [Enter] to continue...


Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/ok/Desktop/RealPlayer]: /opt/RealPlayer
You have selected the following RealPlayer configuration:

Destination:            /opt/RealPlayer

Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: F

Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: .y.
enter the prefix for symbolic links [/usr]: .............................
Setting up realplay symlinks in /usr...
configuring icons...
configuring document icons...
configuring pixmaps...
configuring locale...
configuring desktop...
configuring applications...
configuring GNOME mime types...
Configuring realplay script...

RealPlayer installation is complete.
Cleaning up installation files...
Done.

debian867:/home/ok/Desktop# realplay

I'm running Epiphany-browser so have when it cant find the plugin just select play in external player it just launched totem.

edit no need for  multi-media repo

---

### Post by motsteve on 2008-08-05
Got the Realplayer 10.5 going, thanks.  I am not brave enough to try Lenny yet.  I'll just stick with Etch for a while.  It took me quite some time to get Etch happy.  I am going to try to update my sources.list though.  Thanks for the help.  I hope Bilbo is all installed now, afterall, it was he who started this thread. :)

Now to get my drive partitioned for Ubuntu.....

---

### Post by bilbobagins on 2008-08-16
Thanks to you all . Sorry not replied earlier but have had brain box trouble and they are trying some different medication so im a bit involved with that and not PPC on Ubuntu at present doing a fresh download of 8.04
have fc8 on the old girl at moment but I really want Ubuntu.
                       Thanks to all    Bilbo  :guitar:

---

### Post by ubuntubrian on 2008-08-19
I haven't had any luck running realplayer 10, it always starts and then freezes on my TiBook. Cna I really get version 11 or 10.5 or even 10 to run?
Where are the recent versions?
Thanks

---

