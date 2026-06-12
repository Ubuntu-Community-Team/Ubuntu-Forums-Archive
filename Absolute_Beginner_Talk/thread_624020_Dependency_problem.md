---
title: "Dependency problem"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Diamond_73 on 2007-11-26
First i am really new to Ubuntu.I am a dial up user.

 Problem is that many apps that I downloaded display some dependency error.

 example,many apps request a kdelibs4c2a,and when I download it,it requests some other dependency.

 Some app requests libc6,when I try to install it,I got the message that NEWER version on (ubuntu 7.04) is allready installed ?!?

 I just don't know what to do.

 And when I try to install app for an custom live CD,(uck 2.0.0) problem is that conflicts with GRUB.

 Thanx to all of you for help!

---

### Post by erfahren on 2007-11-26
what apps are you downloading and from where?

give us a list of what apps you are trying to get (they may already be available in the Ubuntu repositories)

---

### Post by kelean on 2007-11-26
I believe the command you need is:

```
sudo apt-get -f install
```

---

### Post by Diamond_73 on 2007-11-27
> **kelean said:**
> I believe the command you need is:

```
sudo apt-get -f install
```

 I am afraid that there is a problem.I have lucent hardware modem.And it's a little bit tricky to use it in Ubuntu,actually I dont have internet in Linux,just in win.

 I have tried to install the following apps:

alsa-tools-gui_1.0.13-1_i386.deb
automatix2_1.1-4.12-7.04feisty_i386.deb
grub-gfxboot_0.97-5_i386.deb
kde-guidance_0.8.0-0ubuntu5_i386.deb
mpeglib_3.5.5-2_i386.deb
uck_2.0.0_all.deb
fuse-2.7.1.tar
k3b_1.0.3-0ubuntu3~feisty1_i386.deb...

 And so on and so on. I downloaded it from

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

 None worked for me because of dependency problem.

---

### Post by angryfirelord on 2007-11-27
If you moving deb packages from Windows to Linux, you have to not only download the package, but its dependencies as well. When you try to install a package, make note of what else has to be downloaded. For example, if I try to install package *foo* and it requires package *poop*, then I have to download the *poop* deb along with package *foo*.

---

### Post by Diamond_73 on 2007-11-27
Okay,but it seems like neverending story.

 One app requires some package,and that package requires something else.

 I don't know what to do about dependencies "lib6",and when I download it,I got the message that I allready have newer version.

 I downloaded libc6_2.3.6.ds1-13etch2_i386.deb.

---

### Post by ruibernardo on 2007-11-27
Hi Diamond_73,

like angryfirelord said, you need to download all the dependencies that a package requires to be installed. You can see which they are in [http://packages.ubuntu.com/](http://packages.ubuntu.com/). This can be a pain. 

As you do have a dialup connection, you could try to get the list of packages you need from Synaptic, on the menu "File" > "Create script to download packages", download them from another place and then install the packages with "dpkg -i". There is an option in synaptic to add downloaded packages, but it doesn't seems to be working.

Or you could try to use [http://nonetdebs.homeip.net](http://nonetdebs.homeip.net). I'm setting up this website for cases like yours.

In a brief resume, you will need:[INDENT] **1**. An email account to activate your account in nonetdebs website;
**2**. Upload the file /var/lib/dpkg/status from your ubuntu box (more or less 1MB, but can be bigger. copy it to USB memory to upload it from a Windows box or other connected computer).
**3**. Select the repositories you want (main, restricted, universe, multiverse, etc), locale and release version of your Ubuntu (Feisty, Gutsy or other).
**4**. Edit you account and type the packages you want in the "Install" tab.
[/INDENT]You will get a list of all the deb packages files and all their dependencies you need to download and you still don't have installed on your ubuntu box.

Check this [post]("http://ubuntuforums.org/showpost.php?p=3742162&postcount=11") to see how to begin to use it (see the all thread for more info about how it works).

Good luck.

---

### Post by Bartender on 2007-12-01
Yeah, diamond, I've played with the packages website some.  Most will not download with all the necessary dependencies included.  Some will work as a download.  Like gnome-ppp, for instance.
Is it possible to get your PC hooked up to someone's broadband for a few hours?  Get all the programs you need, then dial-up won't seem as bad.  Some of the updates are still gonna be ugly...

---

### Post by Diamond_73 on 2007-12-01
thanx epimeteo.
I will try your site thanx.

@bartender
Problem is that I don't know how much dependecies to dl.And wich dependency to DL.I have place to dl.

 btw,anyone knows,how to install gnome-colorscheme_0.3.91-1_i386.deb and agave_0.4.0-1diego0_i386.deb ?

 I am so confused,dependencies are libgconfmm-2.6-1c2_2.18.0-0ubuntu1_i386.deb,and libgconfmm-2.4 1 rc2,but I can't find the second dependence ??

---

### Post by SunnyRabbiera on 2007-12-01
> **Diamond_73 said:**
> Okay,but it seems like neverending story.

 One app requires some package,and that package requires something else.

 I don't know what to do about dependencies "lib6",and when I download it,I got the message that I allready have newer version.

 I downloaded libc6_2.3.6.ds1-13etch2_i386.deb.

well there is part of the reason you are having issues, etch and ubuntu are two entirely different things.
you see Ubuntu is based on debian, but it uses different dependencies and such.
you should use packages with the word ubuntu on them.
if you got thrown off somewhere i can understand, knowing the difference between debian and ubuntu are pretty tough to the newcommer.
if you really need ubuntu apps from the repository and have a slow connection try here:
[the package library of ubuntu]("http://packages.ubuntu.com/")
'
the thing is that the way that ubuntu installs things you have to take note on what it depends on, I know this is frustrating for a windows user... heck I encountered something similar to your issue when I first used linux.
just take notes on what depends on what and see how things go, its not easy at first but once you get the initial bumps out of the road its all good sailing if you give it a chance.

---

### Post by ruibernardo on 2007-12-01
> **SunnyRabbiera said:**
> the thing is that the way that ubuntu installs things you have to take note on what it depends on, I know this is frustrating for a windows user... heck I encountered something similar to your issue when I first used linux.
just take notes on what depends on what and see how things go, its not easy at first but once you get the initial bumps out of the road its all good sailing if you give it a chance.
That is exactly what nonetdebs website does. 

When the user uploads his status file, the packages listed are only the ones that aren't installed on the system, saving the time and trouble of taking note and downloading all dependencies (some of them are already installed and it really hard to keep track of ALL the dependencies of some packages - most of them really).

---

### Post by Diamond_73 on 2007-12-01
thanx guys you are very helpfull to me.

 Sorry for offtopic,but I have to ask,what this means 

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Dependency again ?

---

### Post by Bartender on 2007-12-01
> **Diamond_73 said:**
> @bartender
Problem is that I don't know how much dependecies to dl.And wich dependency to DL.I have place to dl.

If you can move the PC to a place with broadband, just use the Add/Remove Programs or Synaptic (don't try to run both at once) to get some of your programs from the repositories.  Both of the above programs know which dependencies to download/install.  If, as Sunny is suggesting, you're already trying weird things like installing packages from other Linux OS'es you're on your own...

---

### Post by ruibernardo on 2007-12-01
> **Diamond_73 said:**
> 
See `config.log' for more details.

Dependency again ?
Check the config.log file to see what the error was. If the error was because you don't have the package "build-essential" installed, you must install it. This package should be on your "Alternate CD" (text mode install CD). If you installed from a "Desktop CD" (LiveCD) you have to install that package from the repositories.

If you can't move your computer to a broadband connection because it is not a laptop, but you have an internet connection from school, college, work, library, cybercafé, etc, with a browser (any O.S., Windows included), copy the file /var/lib/dpkg/status (size around 1MB) to a USB memory and upload it to [http://nonetdebs.homeip.net](http://nonetdebs.homeip.net).

After creating an account and set it up like described [here]("http://ubuntuforums.org/showpost.php?p=3742162&postcount=11"), you can download the packages you want and all their dependencies you still don't have on the offlne computer and copy them to the USB memory. 

Then you just have to install them with APTonCD or "sudo dpkg -i *.deb && sudo apt-get install -f" on the offline computer.

Good luck.

---

### Post by Bartender on 2007-12-01
Hi, epimeteo -
Thanks for the link to nonetdebs.  I'll have to scratch my head a little bit and see if I can follow it.  Funny how there are all kinds of interesting projects out there that a person wouldn't know about unless someone such as yourself pointed them out!

---

