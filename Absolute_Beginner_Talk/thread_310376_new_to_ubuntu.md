---
title: "new to ubuntu"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by dysolve on 2006-12-01
Hello to all,
I have in the past tried about 10 or different versions of linux and I have never had much luck with any of them. But since the only non-freeware item I run on my PC is Winblows itself, i keep trying linux. But I am very close to giving up. I have always had hardware issues and this time it is no different. But I would like to give it all one more shot.
A few of my friends have told me to give ubuntu a try so I did. But My sound card only works sometimes and when I try to fix it I run in to problems. Also I have a few winblows programs I have to still run But i can not figure out how to get them to work.

When I first installed ubuntu I had no sound so I found the thread on alsa and I tried to follow that but my system would not let me run "make" or "configure", So I tried to install the "build-ess'" package only to find it was already install so I reinstalled it, with no change. For some reason I now have sound but only from the headphone port on the front of my PC, I do not have any input/output from the mic or line out. Does anybody have anyideas on why "configure" and make" are not working?

I need to run a few windows proggies so I installed wine but where the hell is it on my system and how do I use it?

any help would be great.

thanks in advance
David.

---

### Post by lingnoi on 2006-12-01
You have to install make..

```
sudo apt-get update
sudo apt-get make
```

---

### Post by CatKiller on 2006-12-01
Welcome to the community.

> **dysolve said:**
> I need to run a few windows proggies so I installed wine but where the hell is it on my system and how do I use it?

It doesn't matter where Wine is. In general, you'd use ```
wine *NameOfTheWindowsExecutable*.exe
``` You confugre it by using ```
winecfg
``` (The terminal is accessed through Applications -> Accessories -> Terminal)

---

### Post by CatKiller on 2006-12-01
> **dysolve said:**
> Does anybody have anyideas on why "configure" and make" are not working?

Knowing the error messages you get might help, as might knowing what you want to install. Won't help me, of course... I use [Synaptic]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by dysolve on 2006-12-01
thanks for the input so far i have done this before
sudo apt-get update
sudo apt-get make
but here is the results this time.

desktop:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 5B in 3s (2B/s)
reading package lists... Done
desktop:~$ sudo apt-get make
E: Invalid operation make
desktop:~$
so I am a little stumped.
thanks for the wine help... that solved that part of the problem thnx...
I checked in synaptic's and It is saying that make is installed along with makedepend and makedev

---

### Post by Bachstelze on 2006-12-01
the package you need is *build-essential* ;)

---

### Post by dysolve on 2006-12-01
Everything I have read tells me build ess is installed.. how do I check..
syanpics tells me its installed...

---

### Post by Bachstelze on 2006-12-01
If Synaptic tells you it is installed, it is installeD. What are you trying to build ?

---

### Post by CatKiller on 2006-12-01
> **dysolve said:**
> 
desktop:~$ sudo apt-get make
E: Invalid operation make


That would be ```
sudo apt-get **install** make
``` But make is included with build-essential:

```
sudo apt-get install build-essential
```

As HymnToLife says, if Synaptic says build-essential is installed, then make is installed. But make won't work unless you've done your **./configure** step properly. Did you read the link I posted?

---

### Post by dysolve on 2006-12-01
desktop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

thats what happens everytime i do apt-get install build-essential

i am tring to do the following

sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<enter driver name here e.g. via82xx> --with-oss=yes sudo make sudo make install

but the error is 

desktop:~$ sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=hda-intel --with-oss=yes
sudo: ./configure: command not found


 thanks again.

---

### Post by Bachstelze on 2006-12-01
You still haven't answered the question : what are you trying to build ?

---

### Post by dysolve on 2006-12-01
i am tring to update the alsa sound drivers on my system 

ALSA driver Compilation
as per post [http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+stops+working](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+stops+working)

If that does not answer the question please explain what you mean by build,

---

### Post by CatKiller on 2006-12-01
> **dysolve said:**
> 
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<enter driver name here e.g. via82xx> --with-oss=yes sudo make sudo make install



I've not had to compile my own sound drivers - I think it's quite rare to need to do so.

Are you aware that this should be three commands?

[LIST]
[*]sudo ./configure --somestuff
[*]sudo make
[*]sudo make install
[/LIST]

---

### Post by dysolve on 2006-12-01
I am aware that that is three commands so I pasted them one at a time, but if i just copy and paste sudo ./configure  the system reply is sudo: ./configure, command not found.

that leads me to think that ./configure is not installed but build ess is installed so I have no idea.
thanks again for all the help.

---

### Post by CatKiller on 2006-12-01
So you've downloaded something? Then you've untarred it? Then you've gone into the directory you've just made that has the stuff in? (cd *WhateverTheDirectoryIsCalled*) And you were replacing the *<enter driver name here e.g. via82xx>* with the name of the driver? These are things that I would imagine could go wrong, having not done this particular procedure myself. Seriously, did you read the link I posted?

Before a program can be installed (**sudo make install**) - which is the step that puts the files in places they can be run from, first those files need to be made as binary files from the source code (the compiling step). The instructions for the compiler to do this (**make**) are contained in a **Makefile**. Some developers make all the assumptions to for the computer to compile themselves, and so provide their own Makefile. Otherwise, they will provide a script (**configure**) to check the environment of your computer, and so generate the Makefile appropriately. Running this script by using the command **./configure** will generate the Makefile used by the command **make**.

Of course, not all installations are the same. Those three instructions, [LIST=1]
[*]./configure
[*]make
[*]sudo make install
[/LIST] are those that you would use in general. But by convention, the developers would include two files in the source package, called README and INSTALL, that will have more detailed instructions for their particular project.

---

### Post by dysolve on 2006-12-01
I have been reading to link you gave to me. Thanks. i uninstalled and reinstalled build-ess that way but still not differance. Maybe I am just doing some thing wrong. is the a something that i can ./configure that you know will work? at least that way I can test to see if the command is working.

---

### Post by CatKiller on 2006-12-02
The page you're following for instructions says > If you are here, then either your soundcard driver could not be loaded with modprobe, or you want to compile the drivers yourself from scratch. Good luck to you! but you yourself say > For some reason I now have sound but only from the headphone port on the front of my PC - implying that your driver and kernel modules are already installed, since you get sound at all. I think this whole building from source thing is a red herring for you. But, as I say, I could be mistaken

You also haven't really said if you are following the instructions properly. I am somewhat out of my depth on this one, mind, since I've not had to do anything like this myself.

---

### Post by dysolve on 2006-12-02
lets just forget about the sound thing for a little while, I am getting myself *&^%%^&% so maybe I need to do this one thing at a time. 
How do I check to see if ./configure is working on my system?

---

### Post by 3rdalbum on 2006-12-02
./configure is a script that is distributed with each program that can be compiled - it's not a system program.

Have you unextracted the .tar.gz file that you downloaded? If not, do that first.

When the .tar.gz (it might be .tgz or .tar.bz2 or something like that) is extracted, its contents will be in a folder somewhere. Drag the folder directly into your home directory.

Let's assume that the folder is called "my-drivers-1.0.1". You would then enter a terminal and type "cd my-drivers-1.0.1". This tells the terminal that you want to enter the "my-drivers-1.0.1" directory. Obviously, use the name of the real folder on your computer.

When this is done, then you can type:

```

./configure
make
sudo make install

```

(If this just sounds like gobbldigook to you, trust me - it's not as difficult as it sounds, and you'll be happily bashing away at the terminal before you know it.)

---

### Post by CatKiller on 2006-12-02
> **dysolve said:**
> How do I check to see if ./configure is working on my system?

"configure" isn't something that exists independently of a program that you are trying to install. If it exists, it will be part of the source package you are trying to compile. It's just a script used by the developers of that program to set up the compiler appropriately.

The **./** means "this directory", so **./configure** means "run the script called 'configure' that is in this directory". This script normally checks for things, like the processor you are using, the existence of a compiler, and so on.

---

