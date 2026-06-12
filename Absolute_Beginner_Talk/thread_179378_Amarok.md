---
title: "Amarok"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-05-19
I've tried to compile Amarok : "amarok-1.4.0a(2).tar.bz2" but when I type ./configure into the terminal I get the following error message. Any Ideas greatly  appreciated!!!

oliver@ubuntu:~$ cd Desktop/amarok-1.4.0/
oliver@ubuntu:~/Desktop/amarok-1.4.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... not found
configure: error: The important program kde-config was not found!
Please check whether you installed KDE correctly.

---

### Post by Harleen on 2006-05-19
You need to install the KDE development files for this to work.
Installing the package  "kde-devel" and all its dependant packages should give you the needed files.

---

### Post by S{yndrom}e on 2006-05-19
im not familiar with KDE but u could try

sudo apt-get install kde-config

then try cinfguring it again or u can just

sudo apt-get install amarok

---

### Post by S{yndrom}e on 2006-05-19
yea what he said =P

---

### Post by macdo on 2006-05-19
[http://kubuntu.org/packages/amarok-14/pool-dapper/amarok_1.4.0-0ubuntu1_i386.deb]("http://kubuntu.org/packages/amarok-14/pool-dapper/amarok_1.4.0a-0ubuntu1_i386.deb")

That will let you download the deb. 
Then, from the directory you downloaded it to, run ```
sudo dpkg -i amarok_1.4.0a-0ubuntu1_i386.deb
```
If you're using an AMD64, rplace i386 by amd64, and if you're on a PowerPC, then you need to replace i386 by powerpc.

Have fun.
Read this first, though: [http://kubuntu.org/announcements/amarok-1.4.php]("http://kubuntu.org/announcements/amarok-1.4.php")
That basically says that Amarok 1.4 is not recommended for Breezy...

---

### Post by S{yndrom}e on 2006-05-19
shouldn't he wget [http://kubuntu.org/packages/amarok-14/pool-dapper/amarok_1.4.0a-0ubuntu1_amd64.deb](http://kubuntu.org/packages/amarok-14/pool-dapper/amarok_1.4.0a-0ubuntu1_amd64.deb)
if he has an amd first?

---

### Post by macdo on 2006-05-19
[QUOTE=S{yndrom}e]shouldn't he wget [http://kubuntu.org/packages/amarok-14/pool-dapper/amarok_1.4.0a-0ubuntu1_amd64.deb](http://kubuntu.org/packages/amarok-14/pool-dapper/amarok_1.4.0a-0ubuntu1_amd64.deb)
if he has an amd first?[/QUOTE]

I don't use wget, but that would I presume work :-)
I now see that my post was perhaps not as clear as it should have been. 

**tartarian:** if yo have an amd64 or a powerpc, you need to replace 1386 by amd64 or powerpc in both the link and the command.

So for an AMD64: 	[http://kubuntu.org/packages/amarok-14/pool-dapper/amarok_1.4.0-0ubuntu1_amd64.deb](http://kubuntu.org/packages/amarok-14/pool-dapper/amarok_1.4.0-0ubuntu1_amd64.deb)
sudo dpkg -i amarok_1.4.0a-0ubuntu1_amd64.deb

For a powerpc: 
[http://kubuntu.org/packages/amarok-14/pool-dapper/amarok_1.4.0-0ubuntu1_powerpc.deb](http://kubuntu.org/packages/amarok-14/pool-dapper/amarok_1.4.0-0ubuntu1_powerpc.deb)
sudo dpkg -i amarok_1.4.0a-0ubuntu1_powerpc.deb

---

### Post by tartarian on 2006-05-20
Ok, I downloaded each file because I'm not sure what they all are! Amd64? 
Anyway.... Each of them brings up an error message.
amd64: Wrong architecture 'amd64'
powerpc: wrong architecture 'powerpc'
i386: dependancy is not satisfiable: amarok-engines|amarok-engine
Im running Ubuntu kerenl 2.6.20-15-386

Please help.

---

### Post by macdo on 2006-05-20
If you don't know, then it's probably i386

Are you running a Mac?

---

### Post by S{yndrom}e on 2006-05-20
or in terminal type:

uname -a

and paste the results here

---

### Post by tartarian on 2006-05-20
No i'm not running a mac. 
When uname -a is typed into the terminal I get the following reply:
Linux Ubuntu 2.6.15-20-386 #1 PREEMPT Tue Apr 4 17:48:51 UTC 2006 i686 GNU/Linux
Thanks Guys!

---

### Post by macdo on 2006-05-20
OK: i386 is what you need.
Have fun!

---

### Post by tartarian on 2006-05-20
Ok. Thanks! 
I downloaded the .deb file "amarok_1.4.0a-0ubuntu1_i386.deb" and double clicked it. 
The package installer came back with the following message - Error: Dependancy is not satisfiable amarok-engines|amarok-engine

Where am I going wrong?!

---

### Post by Jussi Kukkonen on 2006-05-20
If you still intend to build from source: amaroK has a lot of dependencies... You might have to spend a while trying to find out all of them. If you want to take a shortcut, do a:
```
sudo apt-get build-dep amarok
```
That'll install build-dependencies for the amarok version currently in repositories. There might be additional ones for 1.4, but you'll have most of what you need.

> I downloaded the .deb file "amarok_1.4.0a-0ubuntu1_i386.deb" and double clicked it. The package installer came back with the following message - Error: Dependancy is not satisfiable amarok-engines|amarok-engine
The amarok-engine package in the repositories is probably not the one amarok 1.4 demands. Are you trying to install on Breezy? Installing a Dapper-package on Breezy is not guaranteed to work -- in fact in the case of rapidly evolving software such as amaroK, it's pretty much guaranteed to fail.

---

### Post by S{yndrom}e on 2006-05-20
my my i never had to do all this. All i did was sudo-apt get install amarok and everything worked fine lol

---

### Post by Jussi Kukkonen on 2006-05-20
S{yndrom}e, he's trying to install amaroK 1.4.
The one currently in dapper is 1.3.9. Breezy version is 1.3.1

---

### Post by S{yndrom}e on 2006-05-20
really that much of a difference?

but oh i see what you mean.

---

### Post by tartarian on 2006-05-20
Nothing seems to go right for me!!! lol. 
Are you all saying that I;m making things hard for myself? I'll do the easyiest way please! 
I would do the sudo-apt get thingy but I dont have an internet connection Darn.

---

### Post by S{yndrom}e on 2006-05-20
hmm how could you have downloaded the files without being connected to the internet? Oh well anyway you *were* making it super harder on yourslef

try typing this into the terminal

sudo apt-get install amarok

Sure you'll get a version a bit behind, but it is still pretty up-to-date.

---

### Post by tartarian on 2006-05-20
I have another computer running Windows that I download, copy to my pen and then transfer to my Ubuntu machine. Is there anyway I can do that???

---

### Post by S{yndrom}e on 2006-05-20
so what you are telling me is that you don't have internet connection on ubuntu?

---

### Post by Jussi Kukkonen on 2006-05-20
Ok, the .debs are the way to go then -- forget about compiling from source. Unfortunately  Ubuntu package management really kind of needs a connection, so even installing from debs is not that easy.

As general advice, you need to get the correct version of the software for your OS, you can use packages.ubuntu.com to find out what the versions are:  
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=amarok&searchon=names&subword=0&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=amarok&searchon=names&subword=0&version=all&release=all)
That's a search for amarok - select your OS, and you'll end up at the page where yoou can download the package (by selecting your architecture: i386) -- the problem is that on that same page you can see the dependencies (all of the red dots...). There's a lot of them, and you'll need them *and their dependencies*, and you can't tell which ones you already have...

The only easy solutions I can think of:
 * use another ubuntu machine that you can use to install amarok (by apt-get) and copy the downloaded .debs to your machine...
 * get a Kubuntu installation CD (for the same ubuntu version) and use it as a apt-get source, it probably includes amarok (I'm not 100% sure of this).

---

### Post by Jussi Kukkonen on 2006-05-20
I just got it! 
do a 
```
sudo apt-get install amarok
```
This won't work of course, but it should do the dependency checking for you: find the part where it says **"The following NEW packages will be installed"** -- that's the list of packages you'll have to get from packages.ubuntu.com and install with dpkg.

---

### Post by S{yndrom}e on 2006-05-20
wow all that for some music player.

---

### Post by tartarian on 2006-05-20
So you're all telling me that I really need an internet connection? If i dont it's going to take me a long time. God I hate wireless internet "connections"

Thankyou for all your help guys. I'll work on my internet connection problems beofre I tackle this one.

---

### Post by S{yndrom}e on 2006-05-20
Yes sudo apt-get and Synaptic are the best installers in the world. So yea you need an internet connection pretty much =P. 

I've seen some guides on how to get internet connection up and running. Mabey you could try some.

---

### Post by tartarian on 2006-05-20
Well..... Some of you may be pleased to hear this, some of you may not be! 

I have managed to get a temporary internet connection, but when I type sudo apt-get install amarok I get the following error:

Errhttp://gb.archive.ubuntu.com dapper/main libavahi-qt3-1 0.6.9-2ubuntu5
  404 Not Found [IP: 85.133.25.8 80]
Errhttp://gb.archive.ubuntu.com dapper/main kdelibs-bin 4:3.5.2-0ubuntu1
  404 Not Found [IP: 85.133.25.8 80]
Errhttp://gb.archive.ubuntu.com dapper/main kdelibs-data 4:3.5.2-0ubuntu1
  404 Not Found [IP: 85.133.25.8 80]
Errhttp://gb.archive.ubuntu.com dapper/main kdelibs4c2a 4:3.5.2-0ubuntu1
  404 Not Found [IP: 85.133.25.8 80]
Errhttp://gb.archive.ubuntu.com dapper/main libxine-main1 1.1.1+ubuntu2-6
  404 Not Found [IP: 85.133.25.8 80]
Errhttp://gb.archive.ubuntu.com dapper/main amarok-xine 2:1.3.9-0ubuntu2
  404 Not Found [IP: 85.133.25.8 80]
Errhttp://gb.archive.ubuntu.com dapper/main amarok 2:1.3.9-0ubuntu2
  404 Not Found [IP: 85.133.25.8 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.9-2ubuntu5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.9-2ubuntu5_i386.deb)  404 Not Found [IP: 85.133.25.8 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-bin_3.5.2-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-bin_3.5.2-0ubuntu1_i386.deb)  404 Not Found [IP: 85.133.25.8 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.2-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.2-0ubuntu1_all.deb)  404 Not Found [IP: 85.133.25.8 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2a_3.5.2-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2a_3.5.2-0ubuntu1_i386.deb)  404 Not Found [IP: 85.133.25.8 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine-main1_1.1.1+ubuntu2-6_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine-main1_1.1.1+ubuntu2-6_i386.deb)  404 Not Found [IP: 85.133.25.8 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-xine_1.3.9-0ubuntu2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-xine_1.3.9-0ubuntu2_i386.deb)  404 Not Found [IP: 85.133.25.8 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.3.9-0ubuntu2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.3.9-0ubuntu2_i386.deb)  404 Not Found [IP: 85.133.25.8 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Suggestions? And thanks guys.... you all make Ubuntu workable for me!

---

### Post by Jussi Kukkonen on 2006-05-20
Those lines are there just because there's no internet connection... The ones I'm talking about will be output before these error messages.

**Edit: I didn't read your message, sorry.** Do what the message suggests, run 
```
sudo apt-get update
```
and then try again. That command updates your (ancient) package list, after it apt-get should find the correct (updated) packages.

---

### Post by tartarian on 2006-05-20
There is an internet connection tho! Im on the internet on my ubuntu machine now but its still outputting that. 

This is the full output that I get when I type sudo apt-get install amarok:

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  amarok-xine kdelibs-bin kdelibs-data kdelibs4c2a libavahi-qt3-1
  libxine-main1
Suggested packages:
  konqueror www-browser ruby python-qt3 libqt0-ruby1.8
Recommended packages:
  kdemultimedia-kio-plugins perl-suid libxine-extracodecs
The following NEW packages will be installed
  amarok amarok-xine kdelibs-bin kdelibs-data kdelibs4c2a libavahi-qt3-1
  libxine-main1
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.0MB of archives.
After unpacking 81.9MB of additional disk space will be used.
Do you want to continue [Y/n]?
Errhttp://gb.archive.ubuntu.com dapper/main libavahi-qt3-1 0.6.9-2ubuntu5
  404 Not Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper/main kdelibs-bin 4:3.5.2-0ubuntu1
  404 Not Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper/main kdelibs-data 4:3.5.2-0ubuntu1
  404 Not Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper/main kdelibs4c2a 4:3.5.2-0ubuntu1
  404 Not Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper/main libxine-main1 1.1.1+ubuntu2-6
  404 Not Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper/main amarok-xine 2:1.3.9-0ubuntu2
  404 Not Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper/main amarok 2:1.3.9-0ubuntu2
  404 Not Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.9-2ubuntu5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.9-2ubuntu5_i386.deb)  404 Not Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-bin_3.5.2-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-bin_3.5.2-0ubuntu1_i386.deb)  404 Not Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.2-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.2-0ubuntu1_all.deb)  404 Not Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2a_3.5.2-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2a_3.5.2-0ubuntu1_i386.deb)  404 Not Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine-main1_1.1.1+ubuntu2-6_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine-main1_1.1.1+ubuntu2-6_i386.deb)  404 Not Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-xine_1.3.9-0ubuntu2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-xine_1.3.9-0ubuntu2_i386.deb)  404 Not Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.3.9-0ubuntu2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.3.9-0ubuntu2_i386.deb)  404 Not Found [IP: 85.133.25.7 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by S{yndrom}e on 2006-05-20
i guess i can't talk you in to using the defualt music player till you get your internet fixed :P

---

### Post by Jussi Kukkonen on 2006-05-20
In case you missed my edit to my last post:
You need to run ```
sudo apt-get update
``` before installing.

---

### Post by tartarian on 2006-05-20
Thanks Jussi Kukkonen, you were right, I did miss your last post! Sorry!

Yay, thanks everyone so much, I now have Amarok up and running. 

Last thing, I promise.... :p ..... Amarok has located all of my music fine, but when I click on a track to play it immediatley says playlist finished. I think I might need to download a package? Something i read whilst trawling the web, but I couldn't find a download that resembled what I think I need?
Am I right? Do I need to download a package? Could someone point me in the right direction please?

THANKYOU SO MUCH!!!!!

---

### Post by macdo on 2006-05-20
I take it you're playing mp3s... 
Go to [https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats") and follow the instructions.
Basically, for legal reaons Ubuntu comes with no copyrighted codecs - and that includes mp3.

---

### Post by tartarian on 2006-05-20
Yes, I tried that downloaded the "sudo aptitude install gstreamer0.8-mad" but it made no difference. Could that be because it says "xine" Settings>Configure Amarok>Engine>Sound System? I dont know. :(

---

### Post by Harleen on 2006-05-20
Your previous error messages indicate, that you are usind dapper, so you have to install gstreamer0.10-plugins-ugly instead of gstreamer0.8-mad.

Tricky thing those multimedia-things in Ubuntu...

---

### Post by uantuzri on 2006-05-20
I saw this thread and I think it's the appropriate one. I'm trying to compile from source the amarok 1.4 and I get this error:
```
checking for X... configure: error: Can't find X includes. Please check your ins tallation and add the correct paths!
```

I already have the 1.3.9 version, but I would like to have the 1.4., so apt-get install amarok is useless. Any clue on what's wrong? I'm running Dapper with xgl (it might be related with the error).

Thanks

---

### Post by macdo on 2006-05-20
Add this to your sources.list:

deb [http://kubuntu.org/packages/amarok-14](http://kubuntu.org/packages/amarok-14) dapper main

Then run apt-get update and apt-get upgrade.

---

### Post by Harleen on 2006-05-20
If you have read the whole thread, then you should have noticed, that amarok is a real beast to compile. Do you really want to compile it for yourself or would you also accept precompiles binaries:

[http://archive.kubuntu.de/ubuntu/pool/dapper/main/i386/amarok_1.4.0a-0kubuntu1_i386.deb](http://archive.kubuntu.de/ubuntu/pool/dapper/main/i386/amarok_1.4.0a-0kubuntu1_i386.deb)
[http://archive.kubuntu.de/ubuntu/pool/dapper/main/i386/amarok-xine_1.4.0a-0kubuntu1_i386.deb](http://archive.kubuntu.de/ubuntu/pool/dapper/main/i386/amarok-xine_1.4.0a-0kubuntu1_i386.deb)

Edit: The packages mentioned by macdo seem "more official" than mine, so I recommend using his method.

---

### Post by macdo on 2006-05-20
Your packages and mine are exactly the same (kubuntu.org and kubuntu.de are mirrors, I think) - the only difference is that you suggest getting them directly, whereas I suggest editing the sources.list, and letting apt-get do the grunt work. 
It doesn't really matter which way you go; although with my version, you should get updates as they come out. In practice, I'm not sure that will be the case (Ubuntu Breezy still has Firefox 1.O.7 in the reps...)

---

### Post by tartarian on 2006-05-21
I've added the line to Synaptic Package Manager but when I click reload it spews up the following:
W: GPG error: [http://kubuntu.org](http://kubuntu.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088

Then When I do sudo apt-get update  I get he following:
**sudo apt-get upgrade:** W: GPG error: [http://kubuntu.org](http://kubuntu.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: You may want to run apt-get update to correct these problems

---

### Post by uantuzri on 2006-05-21
Thankyou Harleen and macdo.

I was trying to compile it with some modifications I did on the code to get rid of the auto score so that I could write the score instead and avoid it changing, but I read on the changelog that this is already done in the package! No comple needed.

Anyway, do you have any idea of what could be wrong?

PS: I didn't realise this thread was on the absolute beginner talk forum, I searched and I saw amarok... :-k

---

### Post by Rojay on 2006-05-27
ok i had amarok 1.3 but i wanted 1.4 because it had a plug-in that downloaded lyrics (1.3 downloaded from lyrc.ar.com which is crap but this plugin downloads from lyricspedia.org)
so i edited the source.list to add "deb [http://kubuntu.org/packages/amarok-14](http://kubuntu.org/packages/amarok-14) dapper main"
and i upgraded&updated apt-get
so now i can find amarok 1.4 in the packages list but it gives me this error > amarok:
 Depends: amarok-engines but it is not going to be installed or
	amarok-engine
 Depends: kdelibs4c2a (>=4:3.5.2) but it is not installable
 Depends: libexscalibar1 but it is not going to be installed
  Depends: libgcc1 (>=1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
  Depends: libglib2.0-0 (>=2.10.0) but 2.8.3-0ubuntu1 is to be installed
 Depends: libgpod0  but it is not installable
 Depends: libmysqlclient15off (>=5.0.19-1) but it is not installable
  Depends: libqt3-mt (>=3:3.3.6) but 3:3.3.4-8ubuntu5 is to be installed
  Depends: libsqlite3-0 (>=3.2.8) but 3.2.1-1 is to be installed
  Depends: libstdc++6 (>=4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
 Depends: libtag1c2a (>=1.4) but it is not installable
 Depends: libtunepimp2c2a (>=0.3.0) but it is not installable
 Depends: libvisual0.2 (>=0.2.0) but it is not installable

and then i dont know how to update these packages or where i can find thier updates
so does anyone know what can i do ?

---

### Post by tartarian on 2006-05-27
I dont know if this is what you're talking about but I added 

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper multiverse

to my sources list and I found all the packages I needed there.

---

### Post by Jussi Kukkonen on 2006-05-27
[QUOTE=tartarian]I dont know if this is what you're talking about but I added 

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper multiverse

to my sources list and I found all the packages I needed there.[/QUOTE]
Rojay, Tartarian: **Think** before you do this, if you're running Breezy! You're mixing packages from two different distros now. Not the safest thing to do...

---

### Post by tartarian on 2006-05-27
Well I'm not running Breezy, Im running Dapper. 

And Rojay didn't specify breezy/dapper, and seeing as though he said he was currently downloading from "deb [http://kubuntu.org/packages/amarok-14](http://kubuntu.org/packages/amarok-14) dapper main" I presumed he was also running dapper

---

### Post by Jussi Kukkonen on 2006-05-28
Ok. The library versions Rojay lists suggest that he has breezy installed.

---

### Post by tartarian on 2006-05-28
Oh, how did you find work that out?? I just saw the word dapper and jumped to a conclusion.

---

