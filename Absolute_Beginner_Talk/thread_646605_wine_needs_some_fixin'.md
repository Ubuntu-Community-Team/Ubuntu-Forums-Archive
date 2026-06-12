---
title: "wine needs some fixin'"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Camillejansen on 2007-12-21
hi everybody,

i just installed wine and i ran into a problem. for example, i download the COD Modern Warfare game demo, ran the install (which ran quite good, accept for the fact that i need to install directx 9.0 and that wont download/install properly, anyone has a solution for that?),

but when i select Call Of Duty Moder Warfare demo in Apps> Wine, my cursor shows my computer is "thinking" and than its stops and nothing happens, and my normal apps continue doing their thing. how can i make wine work the way i want?

grtz.

---

### Post by CatKiller on 2007-12-21
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9425](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9425)

---

### Post by Camillejansen on 2007-12-21
yeah, well i didnt understand one bit of this site... seriously guys, im not such a good computeruser. i like linux, but if i dont get it to work properly im going back to my old os. so please can someone give me a better explanation of how to configure Wine to run every windows-installed program i download? because lots of programs i download dont want to start the installation (they abort).

help me out here

---

### Post by bobbocanfly on 2007-12-21
Because of Microsofts secrecy about Windows, Wine is built by guessing. This means that a lot of software (especially complex/large software like games or games using proprietary engines) will not work.

The only way to get all Windows applications to work is either:

1 - Reinstall windows over the top of Ubuntu
2 - Dual boot both Windows and Linux
3 - Run Windows in a virtual machine (You would need a VERY good computer to run games in a VM though)

Good luck.

---

### Post by PeterJS on 2007-12-21
> **Camillejansen said:**
> So please can someone give me a better explanation of how to configure Wine to run every windows-installed program i download?

Sorry chief, can't give you something that doesn't exist. The fact that wine works as well as it does it is pretty impressive, but it's not magic. Wine just doesn't work that well, windows and linux were designed in very different ways, the fact that anything runs under wine is a testament to how clever the wine devs are.

> **bobbocanfly said:**
> Because of Microsofts secrecy about Windows, Wine is built by guessing. This means that a lot of software (especially complex/large software like games or games using proprietary engines) will not work.

+1.

From looking at the app DB it looks like it was a pretty involved bit of fighting with wine environment variables to get it working. Looks like you're best bet is to just ride it out for a couple versions until it works with closer to default configuration. It leaves a sour taste in my mouth to suggest it, but you might want to look at Cedega,  they over market themselves a bit, but are dedicated to gaming, and include hacks and patches to get specific games working even if it breaks other things, where wine tries to do things right.

---

### Post by anewguy on 2007-12-21
According to the website linked in Cat Killer's 1st reply, it will work if you follow the postings under the "IT WORKS!" title.

The first step they ask you to do is download a patch for wine.  All you have to do is click on it and let it download.  You then need to install it, which if you click on the links under that posting will get you those instructions.  If those instructions are too difficult, I will TRY to simplify it here, though there really isn't a lot that can be made easier.  I've highlighted/modified things in red - these are the steps you need to take.


RE: IT WORKS !!!!
by christian on Friday November 30th 2007, 13:45
Hi,

if you already installed a version with ,rpm or .deb then
you do do not have to uninstall it.

Just configure the pathce wine that it installs to a seperate directory.

All steps:

tar -xzf "patchwine.tar.gz"
then cd into the new directory
then
./configure --prefix="Pathwhereyouwantinstsallit" (i use /usr/local/wineforcod4 )

[COLOR="Red"]The above steps are doing 3 things:  decompacting the download into a new directory, having you change your default to that directory, then running a configuration script to tell the next step how you want some things.  These things will require you to be in a terminal window.  Click "Applications" on the top bar, then move your mouse down to "Accessories" then over and down to "Terminal" and click.  This will open a terminal window for you - some times people will tell you to put things in at the command line - this is what they mean.

Now do the following in order, one at a time:

type:
tar -xzf ~/Desktop/wine.tar.gz     <-- press enter then wait for it to finish

type:
cd wine    <-- press enter

type:
./configure --prefix=/usr/local/wineforcod4  <-- press enter then wait for it to finish


[/COLOR]

then make depend && make

then as root

make install

[COLOR="Red"]These 2 steps build up the dependencies needed and then build the new patched version.  Again, while in a terminal window:

type:
make depend && make  <- press enter then wait for it to finish

type:
sudo make install  <- press enter then wait for it to finish

[/COLOR]

Then everytime you want to use the patched version of wine instead of the normal version:

export PATH="pathwhereyouinstalledwine"/bin:$PATH

For my environment you would do:

./configure --prefix=/usr/local/wineforcod4
make depend && make

then as root: make install

then before you start cod4:

export PATH=/usr/local/wineforcod4/bin:$PATH

(then your patched wine version will be used instead of the normal one)

then go to the cod4 installation directory and do:

wine iw3sp.exe

[COLOR="Red"]The above 5 statements are telling you how to run the program each time you want to run it.  Again, these are run from a terminal window:

type:
export PATH=/usr/local/wineforcod4/bin:$PATH  <-- press enter

type:
cd xxxxx   (where xxxxx is the name of the folder that cod4 installed to) <- press enter

type:
wine iw3sp.exe  <- press enter


[/COLOR]


Have fun,
Christian


(end of info from the posting)


I hope this helps you out for COD4.  If not, it may be above your current LInux abilities.:) 

EDIT:  Beyond that, there is no given way to make wine work with any windows program.  Wine is meant as a way to run must-have apps for which there is currently no Linux equivalent (not same title, just something that will do the same work).  Wine is far, far, far from perfect and even further away as the end-all means to run a Windows application in Linux.  Linux and Windows are fundamentally very, very different, built upon very different core phyllosophies (sorry about the spelling).  I'm not referring to free versus non-free in this instance, I'm talking about the very basics for which the operating system was designed.  this makes it extremely difficult to make all but the most basic of applications run in wine.  So, if you want something you can run all of your Windows programs in, consistently, and without some problem along the way, you would be better off sticking to Windows.

EDIT_EDIT:  Corrected a couple of typos on the commands

---

### Post by disturbedite on 2007-12-21
just a tip about the directx requirement...
don't install directx with wine.  wine has its own dll's (directx dll's in this case) and if you install directx it will overwrite wine's dll's.  this will screw things up.

---

### Post by PeterJS on 2007-12-21
> **disturbedite said:**
> just a tip about the directx requirement...
don't install directx with wine.  wine has its own dll's (directx dll's in this case) and if you install directx it will overwrite wine's dll's.  this will screw things up.


Further more DX9 hasn't been implemented yet, so there's no way to get that to work so you're going to have to put up with DX8 graphics. On the upside the low quality textures usually save a bundle on RAM usage.

---

### Post by bodhi.zazen on 2007-12-21
Wine is NOT a drop in replacement for Windows, nor is it for new users.

IMO wine is in alpha.

If you want to use wine 

1. The best source of information is the wine web page.

2. Wine often involves post-install configuration.

3. If you are following a how to you need to use the matching version of wine and operating system. What works in one version of wine often will not work in other versions.

See here of additional information : [http://gaming.gwos.org/news.php](http://gaming.gwos.org/news.php)

---

### Post by kajillin on 2007-12-21
Directx9 WILL NOT work in linux, if you want to game then you need to use OpenGL. If the game does not support OpenGL then your screwed. 

Linux isnt for people who like to do things the easy way, so if this is you..... then you are wasting your time even coming here.

---

### Post by PeterJS on 2007-12-21
> **kajillin said:**
> Directx9 WILL NOT work in linux,
Yep
> 
 if you want to game then you need to use OpenGL. If the game does not support OpenGL then your screwed. This isn't strictly true. Wine has a DX8 layer. So if a game supports DX8 wine can translate the DX8 instructions into openGL instructions.

> 
Linux isnt for people who like to do things the easy way, so if this is you..... then you are wasting your time even coming here.Lots of things are easy under linux, just take a look at the package manager. Window's has nothing on apt, or anything like it. Or compiz, it'll give you the most bang for your back for eye candy not on a mac, even then it wins on a cost basis :) Gaming just isn't what linux does well.

---

### Post by kajillin on 2007-12-21
> **PeterJS said:**
> 
This isn't strictly true. Wine has a DX8 layer. So if a game supports DX8 wine can translate the DX8 instructions into openGL instructions.
cool didnt know that, but COD4:MW will not run under Dx8

---

### Post by CatKiller on 2007-12-21
> **kajillin said:**
> Directx9 WILL NOT work in linux, if you want to game then you need to use OpenGL. If the game does not support OpenGL then your screwed. 

Linux isnt for people who like to do things the easy way, so if this is you..... then you are wasting your time even coming here.

I pretty much disagree with everything you said. Sorry and all. I was playing Max Payne just the other day, which is entirely DirectX, using Wine's built-in DirectX compatibility layer. Linux is vastly easier in many many respects, and Windows has absolutely nothing to offer a new computer user over Ubuntu. 

> **PeterJS said:**
> Gaming just isn't what linux does well.

I'm afraid I disagree with this, too. Linux-native games like Unreal Tournament, Return to Castle Wolfenstein, or Quake, run much better for me under Linux than they ever did for me under Windows.

---

### Post by disturbedite on 2007-12-21
> **PeterJS said:**
> Further more DX9 hasn't been implemented yet, so there's no way to get that to work so you're going to have to put up with DX8 graphics. On the upside the low quality textures usually save a bundle on RAM usage.
thats not entirely true.  some parts/features of dx9 have been implemented, but its not complete, obviously.

i read a page on the wine wiki that lists the implementation of the different directx versions in wine, but i can't seem to find it again, unfortunately...

---

