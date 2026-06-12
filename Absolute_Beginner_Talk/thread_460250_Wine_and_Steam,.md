---
title: "Wine and Steam,"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Comzee on 2007-05-31
Ok, I'm a nub when it comes Wine, I have never successfully used it. 
I downloaded Steam installer from [here]("http://www.steampowered.com/v/index.php?area=getsteamnow")

I downloaded it to /home/comzee/downloads/Steaminstall.msi

That I went into my console and type this.
```

Sudo Wine /home/comzee/downloads/Steaminstall.msi
```

It didn't work. I know you can get CSS running on Ubuntu, just don't know how to do it.

Any help on this would be great, thanks in advance.

---

### Post by raeb on 2007-05-31
What's not working about it?  Is there any error output from wine when you type that command?

Here's the guide I used to get steam running.  Make sure to follow step 2 and use the right repository for the latest version.

[http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/](http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/)


BTW, props to the Ichigo hollow avatar  :D

---

### Post by Comzee on 2007-05-31
I give up, it's to hard. I read the instructions and had a brain spasm.:(
I guess I'll just hold off on Ubuntu gaming.

---

### Post by Cheat King on 2007-05-31
There is a very good program called CrossOver... 

It comes with an option made for STEAM...

[http://linux.softpedia.com/get/Office/Office-Suites/CrossOver-Office-Standard-3883.shtml](http://linux.softpedia.com/get/Office/Office-Suites/CrossOver-Office-Standard-3883.shtml)

---

### Post by Hobo Joe on 2007-05-31
This is a very simple and very effective guide to getting it working in Linux.

[http://developer.valvesoftware.com/wiki/Steam_under_Linux](http://developer.valvesoftware.com/wiki/Steam_under_Linux)

---

### Post by PandaGoat on 2007-05-31
Woh woh!  You can not use wine normally, without arguments, when running a .msi.  Use 
```
wine msiexec /home/comzee/downloads/Steaminstall.msi
```

---

### Post by YokoZar on 2007-05-31
> **Comzee said:**
> I give up, it's to hard. I read the instructions and had a brain spasm.:(
I guess I'll just hold off on Ubuntu gaming.Don't worry, it's not your fault.  It really should be just as simple as pointing and clicking on the installer after you download it.  I'm doing what I can to fix this in the next Ubuntu release, though :)

---

### Post by Comzee on 2007-06-01
Ok I have a some questions.
Crossover seams like it could work but, when I try to open it it has an error, as follows > "gedit has not been able to detect the character coding. Please check that you are not trying to open a binary file. Select a character coding from the menu and try again."
I only have two character coding, "Current locale (UTF-8)" and "Western (ISO-8859-15)"
So whatever.

And everywhere I look it says something about  "Wine's "virtual" Windows drive." Do I have to create that. And once it is created where is it in my filesystem. 


And when I use this code.
```
wine msiexec /home/comzee/downloads/Steaminstall.msi
```

I get this
```
Usage:
  Install a product:
    msiexec {package|productcode} [property]
    msiexec /i {package|productcode} [property]
    msiexec /a package [property]
  Repair an installation:
    msiexec /f[p|o|e|d|c|a|u|m|s|v] {package|productcode}
  Uninstall a product:
    msiexec /x {package|productcode} [property]
  Advertise a product:
    msiexec /j[u|m] package [/t transform] [/g languageid]
    msiexec {u|m} package [/t transform] [/g languageid]
  Apply a patch:
    msiexec /p patchpackage [property]
    msiexec /p patchpackage /a package [property]
  Modifiers for above operations:
    msiexec /l[*][i|w|e|a|r|u|c|m|o|p|v|][+|!] logfile
    msiexec /q{|n|b|r|f|n+|b+|b-}
  Register a module:
    msiexec /y module
  Unregister a module:
    msiexec /z module
  Display usage and copyright:
    msiexec {/h|/?}
NOTE: Product code on commandline unimplemented as of yet

Copyright 2004 Vincent B&#65533;ron

```

WTF. 

Anyways, some help on this dumb questions would be great. Thanks for the help so far.

---

### Post by TomMK on 2007-06-01
When you want to run a .msi file with wine you must use this syntax:

wine msiexec /i /home/comzee/downloads/Steaminstall.msi

notice the **/i** - thats means you want to install it. The previous poster just forgot to include that.

---

### Post by Comzee on 2007-06-01
Ok, It worked. But once I installed steam all the words on the buttons where gone. I thought I knew Steam well enough to ignore it but, I accidentally exited it out. Now I can't find where it is. So how do I get back into it, and where is the Wine virtual windows drive.

Thanks for the coding to install it though, easer then I thought.

---

### Post by dfreer on 2007-06-01
> **Comzee said:**
> Ok, It worked. But once I installed steam all the words on the buttons where gone. I thought I knew Steam well enough to ignore it but, I accidentally exited it out. Now I can't find where it is. So how do I get back into it, and where is the Wine virtual windows drive.

Thanks for the coding to install it though, easer then I thought.

All the words are gone because you do not have the tahoma.ttf font saved to your windows virtual drive. So here's what I would do:
Do a search on google for tahoma.ttf OR go to a windows machine and grab it from C:\windows\fonts\
Save it to your linux machine (your desktop for example).
Make sure the permissions are correct with this command (you may need to change the location/filename):
```
sudo chmod a+r ~/Desktop/tahoma.ttf
```
Copy it into your virtual windows drive:
```
sudo cp -v ~/Desktop/tahoma.ttf ~/.wine/drive_c/windows/fonts/
```

To start steam up again, there should be a Wine menu in your Applications menu bar, OR you can start it this way if you installed it with all the default settings:
```
wine ~/.wine/drive_c/windows/program\ files/Steam/steam.exe
```

---

### Post by Comzee on 2007-06-01
Ok, I have duel boot on my PC so I just took the font from my Windows. I copied it to my virtual Wine drive into the fonts directory. This is where it went FUBAR. For some reason I don't have a Wine listing under my applications tab. So I ran the code you gave me   ```
wine ~/.wine/drive_c/windows/program\ files/Steam/steam.exe
```

And it did this, ```
wine: cannot find '/home/comzee/.wine/drive_c/windows/program files/Steam/steam.exe'
comzee@comzee-notebook:~$ wineserver: could not save registry branch to /home/comzee/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/comzee/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/comzee/.wine/user.reg : Permission denied

```

So then I went to the Wine drive and tried to start the executable from there and it gave me this error, >  Steam.exe (main exception): Cannot open blob archive file:
CMultiFieldBlob(mem-mapped file): Failed to open existing file, Win32 Error
5 "Access denied"

So I got the fonts but still need to know how to get back into steam.

I really appreciate you guys helping me, and thanks for the fix for the fonts.

---

### Post by justin whitaker on 2007-06-01
> **Comzee said:**
> Ok, I have duel boot on my PC so I just took the font from my Windows. I copied it to my virtual Wine drive into the fonts directory. This is where it went FUBAR. For some reason I don't have a Wine listing under my applications tab. So I ran the code you gave me   ```
wine ~/.wine/drive_c/windows/program\ files/Steam/steam.exe
```

And it did this, ```
wine: cannot find '/home/comzee/.wine/drive_c/windows/program files/Steam/steam.exe'
comzee@comzee-notebook:~$ wineserver: could not save registry branch to /home/comzee/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/comzee/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/comzee/.wine/user.reg : Permission denied

```

So then I went to the Wine drive and tried to start the executable from there and it gave me this error, 

So I got the fonts but still need to know how to get back into steam.

I really appreciate you guys helping me, and thanks for the fix for the fonts.

Sometimes when you copy from windows drives or partitions (and not all the time) Ubuntu copies them over as root, with root permissions. Try changing the permissions on the folder again, including all subfolders.

I've had this happen with external NTFS drives before...but it doesn't always happen. *shrug*

---

### Post by TomMK on 2007-06-01
didn't read the above post before replying...deleted

---

### Post by dfreer on 2007-06-01
> **Comzee said:**
> ```
wine: cannot find '/home/comzee/.wine/drive_c/windows/program files/Steam/steam.exe'
comzee@comzee-notebook:~$ wineserver: could not save registry branch to /home/comzee/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/comzee/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/comzee/.wine/user.reg : Permission denied

```


Hey, sorry things didn't go smoothly your first time :( The important thing to realize is that you *should* be able to get things running, steam works pretty well with wine, and you can always try from fresh again!

Also, forgot if it was mentioned. You will need to have 3D acceleration/direct rendering working in order to play steam games (or any other 3D game for that matter). You can check with this command:
```
glxinfo | grep rendering
```
It should say yes if it works.

So let's see if we can fix the problem. I would say, just to be safe, to reinstall wine and steam, so that we can start fresh. We could go through and diagnose things, you'll probably learn more, but I assume you're like me and just want to be able to frag a few people online really quick.

Go ahead and uninstall wine, and delete the virtual windows drive (make sure if you want to save anything in there to back it up first!):
```
sudo apt-get remove wine
sudo rm -Rv ~/.wine/
```

Clean out your apt-cache (apt-cache simply saves a local copy of every package you download, so that if you need to reinstall/install it uses the local copy), then download wine:
```
sudo apt-get clean
sudo apt-get install wine
```

Configure wine for the first time, making sure to set the audio tab and drive paths. also make sure the "Allow directx apps to prevent mouse from leaving the window" and "Let the linux window manager manage the windows", in the Graphics tab I think (doing this from memory, sorry!):
```
winecfg
```

Copy the tahoma.ttf file into your virtual windows drive, set the permissions and verify that the permissions are set right:
```
sudo cp -v ~/Desktop/tahoma.ttf ~/.wine/drive_c/windows/fonts/
sudo chmod u=rw,g=r,o=r -v ~/.wine/drive_c/windows/fonts/tahoma.ttf
ls -l ~/.wine/drive_c/windows/fonts/tahoma.ttf
```

Download the Gecko Web browser (so that steam store displays correctly, it seems every other release of Wine breaks gecko for me, so it may work for you it may not. If it doesn't, you can always download a newer/older version of wine and try it instead. NOTE: If you don't get gecko installed, you can still download and play steam games, so it doesn't matter much):
```
wine iexplore www.google.com
# If the above doesn't work try the below, or both!
wine iexplore http://www.google.com
```

Download the steam installer (You can download and install .MSI's with wine, from what I hear. However, I haven't installed an MSI successfully yet, so I just normally download the old SteamInstall.exe file) and install it:
```
cd ~/
wget -c http://steampowered.com/download/SteamInstall.exe
wine SteamInstall.exe
```

Tada! Steam should work. On both my AMD64 and 32-bit Ubuntu machines I can play Half-life, half-life 2, CS, CS:S, DoD, Brainbread and Zombie Panic!... haven't tried any others but they should all work!

Please let us know if this works, or if something goes wrong, I spent some time writing that and I wanna know if it works for ya!

---

### Post by daimaru on 2007-06-01
> **Comzee said:**
> Ok, I'm a nub when it comes Wine, I have never successfully used it. 
I downloaded Steam installer from [here]("http://www.steampowered.com/v/index.php?area=getsteamnow")

I downloaded it to /home/comzee/downloads/Steaminstall.msi

That I went into my console and type this.
```

Sudo Wine /home/comzee/downloads/Steaminstall.msi
```

It didn't work. I know you can get CSS running on Ubuntu, just don't know how to do it.

Any help on this would be great, thanks in advance.
i really cant see how counter strike source is going to really run (smoothly) on linux using wine... but if anyone has an answer to this plz do tell.

edit: just saw that your all trying to tell him how to get the install working using wine... is there a point ? i mean the most basic programs run slowly on wine so how's he supposed to play a game like css through steam using wine ?

---

### Post by aktiwers on 2007-06-01
Get the steam.exe file instead. I always use that one when installing Steam and I have no problem. I will attach it to this post. Though I have to go to winecfg and change to window mode Wine.
EDIT: I got CSS working fine using wine..  only small lags because of my old Video card.

---

### Post by dfreer on 2007-06-01
> **daimaru said:**
> i really cant see how counter strike source is going to really run (smoothly) on linux using wine... but if anyone has an answer to this plz do tell.

edit: just saw that your all trying to tell him how to get the install working using wine... is there a point ? i mean the most basic programs run slowly on wine so how's he supposed to play a game like css through steam using wine ?

hmm. what games/programs have you tried with wine? most importantly, **are your video card drivers installed correctly?**. Imagine trying to play a F.E.A.R. with the default windows drivers and you get the idea. Wine doesn't make programs run slowly, there might be a slight performance decrease (pixel shader 2.0 isn't supported, I don't think antialiasing works too well), but it is not an emulator, which means it should run as well (or in some cases, better) then windows,

Steam and counterstrike (yes, even source) run with wine. with my laptop's nvidia geforce 7400 I get around ~40 FPS in CS:S and Half-Life 2 (not that great, i understand, but it is decently smooth and definitely playable!). Half-life and countstrike 1.6 gets ~70-100 FPS.

not trying to flame or nothing, just stating that it is possible and not terribly hard (the main thing is having a virgin wine install and getting your video drivers installed correctly. If you would want to try I can help you get your games running as well, just post your specifics. of course wine is still beta and you should always check winehq app database to see if the game runs for anyone at all first.

> **aktiwers said:**
> Get the steam.exe file instead. I always use that one when installing Steam and I have no problem. I will attach it to this post. Though I have to go to winecfg and change to window mode Wine.
EDIT: I got CSS working fine using wine..  only small lags because of my old Video card.

yeah, in the short how to above it tells the OP to download the .exe from steampowered.com. either one works fine I guess.

---

### Post by Comzee on 2007-06-02
Wow, this Wine stuff is being really gay for me.
New topic. 

How do I install steam WITHOUT using Wine.

---

### Post by daimaru on 2007-06-02
> **dfreer said:**
> hmm. what games/programs have you tried with wine? most importantly, **are your video card drivers installed correctly?**. Imagine trying to play a F.E.A.R. with the default windows drivers and you get the idea. Wine doesn't make programs run slowly, there might be a slight performance decrease (pixel shader 2.0 isn't supported, I don't think antialiasing works too well), but it is not an emulator, which means it should run as well (or in some cases, better) then windows,

Steam and counterstrike (yes, even source) run with wine. with my laptop's nvidia geforce 7400 I get around ~40 FPS in CS:S and Half-Life 2 (not that great, i understand, but it is decently smooth and definitely playable!). Half-life and countstrike 1.6 gets ~70-100 FPS.

not trying to flame or nothing, just stating that it is possible and not terribly hard (the main thing is having a virgin wine install and getting your video drivers installed correctly. If you would want to try I can help you get your games running as well, just post your specifics. of course wine is still beta and you should always check winehq app database to see if the game runs for anyone at all first.



yeah, in the short how to above it tells the OP to download the .exe from steampowered.com. either one works fine I guess.


sure i want your help.
i didnt realize that it could work with wine because everything i tried with wine so far ran slowly . i installed wine and conterstrike source and i can start it and all but as i guessed (which does not mean that your wrong but that i probably have some driver issues) it runs real slow. 
hehe when on dust  i finally get to the tunnel the game is almost always over. i can see the other ppl moving away fast while i am stepping on the spot or something . its totaly unplayable.

so here are my specs
i got an sapphire radeon x800GTO (16pipes enabled) - enabled the restricted drivers through system menu. 
do i have to install the ati drivers manually would that change anything because when i started counterstrike steam told me that my hardware was not good enough for playing the game --- lalala must be wine related cause it works fine under windows. 
do i have to install an ati driver under wine? if so how because i tried dl the winxp (cause my wine is set to winxp) ati radeon driver from the website and tried installing it but i got a message saying that i need admistrative rights to install them .... hmmm how am i going to do that ? tried sudo which even before i did it i knew can t work cause it got nothing to do with the internals of wine so what can i do now ???

edit: well i have absolutely nothing configured under winecfg , which might be the problem but i dont know what to do. under applications i selected winxp ; under library nothing is selected same for the rest i guess except for sound which is set to OSS

---

### Post by daimaru on 2007-06-02
@comzee 
so i dont go off thread here. did you try the installer and instructions from [here]("http://developer.valvesoftware.com/wiki/Steam_under_Linux") ? i used that steam installer which is .exe by the way and it worked fine (copied thaoma font to the fonts directory 1st)

---

### Post by Quan_Chi on 2007-06-02
Quick question here.
I'm trying to install Steam with wine.
And I get to the point where I need to put the font in the ./wine/drive_c directory
But no such directory exists.
Ive already installed wine and all that as well.

Whats going on here?
I thought wine was supposed to create that directory when I first ran it.

What should I do

---

### Post by Comzee on 2007-06-02
No offence to the people who created Wine, but I hate it!
I try, and I try, and I try ,and I try, and I try, and I try, and I try, and it still won't work for me.

I checked my graphics card with Ubuntu, it says I have a 3D ready card, also with the new 7.04 upgrade to Ubuntu It auto detected my graphics card and gave me awsome drivers for it. So I would like to get CSS working sometime with Ubuntu, but whatever.


P.S. Sorry for my spelling, I've been up all night at a lan party.

---

### Post by dfreer on 2007-06-02
> **Comzee said:**
> No offence to the people who created Wine, but I hate it!
I try, and I try, and I try ,and I try, and I try, and I try, and I try, and it still won't work for me.

I checked my graphics card with Ubuntu, it says I have a 3D ready card, also with the new 7.04 upgrade to Ubuntu It auto detected my graphics card and gave me awsome drivers for it. So I would like to get CSS working sometime with Ubuntu, but whatever.


P.S. Sorry for my spelling, I've been up all night at a lan party.

It sucks that there is no native steam installer for linux, but alas. What you will probably want to do next is spend some $$$. 

Cedega installs steam pretty easily, although I always had slow startup times (spent like 3 mins waiting for the steam window to pop up). This of course may have changed with the new release (and from what I hear, pixel shader 2.0 is supported in the new release, so F.E.A.R. should work now :D ). However Cedega costs like $5 USD a month to use. :( 
EDIT:Cedega also has the best game installer/User Interface out of the three programs

Crossover Office with it's new release claims to run Steam and Games, although I never tried the new release myself, and never got Steam working on the old ones. Do some research, it may work great. Crossover Office costs $40 USD, but it's a one-time payment, you won't need to pay again (unlike cedega).

> **Quan_Chi said:**
> Quick question here.
I'm trying to install Steam with wine.
And I get to the point where I need to put the font in the ./wine/drive_c directory
But no such directory exists.
Ive already installed wine and all that as well.

Whats going on here?
I thought wine was supposed to create that directory when I first ran it.

What should I do

is ~/.wine there? try running winecfg first, that should create all the folders needed. if not, I guess you could try an uninstall/reinstall of wine. other than that, it could be a permissions issue, do an ls -l of your /home/$USER/ folder, to see if it is set drwxr_xr_x


> **daimaru said:**
> sure i want your help.
i didnt realize that it could work with wine because everything i tried with wine so far ran slowly . i installed wine and conterstrike source and i can start it and all but as i guessed (which does not mean that your wrong but that i probably have some driver issues) it runs real slow. 
hehe when on dust  i finally get to the tunnel the game is almost always over. i can see the other ppl moving away fast while i am stepping on the spot or something . its totaly unplayable.

so here are my specs
i got an sapphire radeon x800GTO (16pipes enabled) - enabled the restricted drivers through system menu. 
do i have to install the ati drivers manually would that change anything because when i started counterstrike steam told me that my hardware was not good enough for playing the game --- lalala must be wine related cause it works fine under windows. 
do i have to install an ati driver under wine? if so how because i tried dl the winxp (cause my wine is set to winxp) ati radeon driver from the website and tried installing it but i got a message saying that i need admistrative rights to install them .... hmmm how am i going to do that ? tried sudo which even before i did it i knew can t work cause it got nothing to do with the internals of wine so what can i do now ???

edit: well i have absolutely nothing configured under winecfg , which might be the problem but i dont know what to do. under applications i selected winxp ; under library nothing is selected same for the rest i guess except for sound which is set to OSS

Hmmm. ATI cards are notorious for not getting installed right, I don't know whether the restricted drivers manager has solved this or not. can you post the output of this command?
```
glxinfo
```

And also this one:
```
cat /etc/X11/xorg.conf
```

Basically, I'm just checking that 3D acceleration/direct rendering is turned on and the correct driver is being used with the first command, and the second command is if the correct driver isn't installed, to see if xorg.conf has the correct driver listed. Oftentimes, I've seen the fglrx driver being specified in xorg.conf, but the MESA driver being loaded (not good).

---

### Post by Quan_Chi on 2007-06-03
Hey thanks I found the folder!
I was looking in the wrong place :/

---

### Post by daimaru on 2007-06-04
@dfreer here's the output. still dont understand why my css is running so choppy.
do i need to install ati drivers inside wine?`if so i cant get them to install. no admin rights or something.

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO
OpenGL version string: 2.0.6334 (8.34.8)

```

```
glxinfo |grep "direct rendering"
direct rendering: Yes
```

xorg.conf 
```
Section "Device"
	Identifier	"ATI Technologies Inc R480 [Radeon X800 GTO (PCIE)]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

```

didnt want to take up all the space in this thread, but thats about what you need right?

---

### Post by dfreer on 2007-06-05
hmmm yeah, it looks like you got everything installed right. No, wine uses your system drivers, it basically just translates API calls from what I understand of it. An emulator would emulate the entire machine, drivers, chipsets, CPU etc. wine simply translates a windows call (say to draw a 3D square) to the appropriate linux call. That's my understanding of it, so bear with me. 
Regardless, you do not need to install any windows drivers using wine, and I don't you can at all.

Honestly I dunno why your CSS is running so choppy, you have your video card drivers installed right (restricted drivers manager FTW!) try fiddling with some of the display options within CS:S. I'm pretty sure your Radeon x800 would beat the **** out of my nvidia geforce 7400 any day, so you shouldn't have any choppiness.

I'm thinking it is either:
(1) the linux ATI drivers are just plain crap, and don't give the performance the windows ones do
(2) wine has issues with ATI in general
(3) issue with ATI drivers with 64-bit ubuntu
(4) issue with wine and 64-bit ubuntu

Like I said, most people's ATI cards get installed wrong and I assumed that might have been your problem, sorry.

---

### Post by daimaru on 2007-06-05
> **dfreer said:**
> 
I'm thinking it is either:
(1) the linux ATI drivers are just plain crap, and don't give the performance the windows ones do
(2) wine has issues with ATI in general
(3) issue with ATI drivers with 64-bit ubuntu
(4) issue with wine and 64-bit ubuntu


i agree yes ati drivers for linux probably are crap, but i will give it a shot building the ones from ati manually. since right now i just use the xorg-driver-fglrx ones, which work fine with beryl and everything i tried so far, but maybe that solves the problem. 
point 3 / 4 don't apply i used i386 ubuntu when i first tried it out. no difference.
i already know what i'll buy next, when crysis is released and i need a directx10 compatible card ill get a nvidia

---

### Post by fabertawe on 2007-06-05
Hi folks...

Just to add some info... I'm running wine 0.9.34 on 64bit Feisty and all the Source games run great (even Lost Coast). I was running on a GeForce 6800 which recently died. I'm currently running a 5700**LE** and CSS runs smooth (albeit with everything on low setting now). I have an 8600GT on order and I'm hoping the Nvidia 100* driver is up to speed for that.

One thing that may be of interest to dual booters is that if you install the read-write ntfs-3g driver (from the repo) you can simply make a sym link from 'Steam\SteamApps' on your windows partition and, in my case, save copying 17GB of data over, marvellous! ;)

EDIT: I've just found **[this link]("http://developer.valvesoftware.com/wiki/Steam_under_Linux")** on the Valve site stating...
"Creating a Symlink to SteamApps on a NTFS partition doesn't work either. Steam will start up, but your GCFs will get corrupted or - if you're lucky - Steam only assumes they are corrupted. So you won't get around having duplicate GCFs for Linux and Windows if you plan on using Steam with both operating systems and having NTFS partitions for Windows."
I've not had any problems yet myself and will continue to use the symlink method but let it be a warning to everyone!

Paul

---

### Post by daimaru on 2007-06-05
@dfreer
--------------
yeah found the problem ATI=****. i got css to run under 64bit now and it works better with the offical ati drivers, but its only kindof playable no real fun there its still to slow. did find this on winehq faq so heck that says it all.

> I have an ATi graphics card and I get bad performance, why?
Simple, ATi has very poor graphics card drivers (fglrx) that are slow and buggy. This means that taxing Windows games through Wine in Linux are not likely to work well, if at all. The only way to rectify this is either make ATi create decent drivers or to buy an nVidia graphics card.

and thats just what i will do ---> here i come Nvidia :)

---

### Post by dfreer on 2007-06-05
re: daimaru

Hmmm. I'll have to remember that. For some reason I looked at your system specs and saw the 64 thinking you were running 64-bit. I'm thinking you don't even need to buy a high-end nvidia card, if you don't have much money to spend. an 7*** series should work fine, although if you DO have the money... :D

---

### Post by fabertawe on 2007-06-06
> **fabertawe said:**
> EDIT: I've just found **[this link]("http://developer.valvesoftware.com/wiki/Steam_under_Linux")** on the Valve site stating...
"Creating a Symlink to SteamApps on a NTFS partition doesn't work either. Steam will start up, but your GCFs will get corrupted or - if you're lucky - Steam only assumes they are corrupted. So you won't get around having duplicate GCFs for Linux and Windows if you plan on using Steam with both operating systems and having NTFS partitions for Windows."
I've not had any problems yet myself and will continue to use the symlink method but let it be a warning to everyone!

Typical! I spoke too soon... using ntfs-3g and symlinking does indeed corrupt your GCFs ](*,) Oh well, saves anyone else the frustraton of finding out ;)

Paul

---

### Post by dfreer on 2007-06-06
You could have you GCFs located on a FAT32 partition that both windows and ubuntu can read/write to, however for most people this would involve repartioning and so is not a very good option.

---

### Post by fabertawe on 2007-06-06
> **dfreer said:**
> You could have you GCFs located on a FAT32 partition that both windows and ubuntu can read/write to, however for most people this would involve repartioning and so is not a very good option.

That's a good point actually, I'm re-thinking my partitioning strategy at the moment. Do you have any experience of FAT32 access speeds? Not that I would imagine it would impact much if I just have a partition for the 'SteamApps'.

Cheers ... Paul

---

### Post by dfreer on 2007-06-06
ummm I don't think it should be much different unless it gets fragmented. I know how to run some hard drive read tests, but i dunno about partition/filesystem reads.

The main thing is to watch that it doesn't get fragmented from the windows side.

---

### Post by benzs_s on 2007-06-11
```
$ wine SteamInstall.exe
wine: could not load L"c:\\windows\\system32\\SteamInstall.exe": Module not found
```

0_o

---

### Post by dfreer on 2007-06-11
You need to run that command pointing to wherever SteamInstall.exe is located. So if it is on your desktop, run:
```
wine ~/Desktop/SteamInstall.exe
```
If it is in your home folder:
```
wine ~/SteamInstall.exe
```

---

### Post by benzs_s on 2007-06-11
oh, that makes sense, thanks :)

---

### Post by BennBuntu on 2007-06-12
just on the off chance, anyone else having trouble connecting? Haven't used steam for a few weeks, now when I open up, singon says "failed to connect to steam server".

Only thing I've changed in Networking is installing apache. So I stopped that and samba, also tried manual port forwarding and even DMZ. No change

any ideas?

---

### Post by Comzee on 2007-06-18
So I'm trying to do this again. I need to know some stuff though.

My wine virtual drive has a lock on the folder, which makes it so I can't delete it or do anything with it. So how do I change the permissions on it so I can delete it and start over.




Thanks

---

### Post by atria on 2007-06-18
```
sudo rm -rf /home/user/.wine
```

will work fine

---

### Post by BennBuntu on 2007-06-18
also, if want to do it with nautilus, 

sudo nautilus

that launches the file browser as root, so you can change permissions

---

### Post by atria on 2007-06-18
Yep that'll work fine. If you want you can change the permissions using the console by using the commands chmod, chown or chgrp.

```
man chmod
```

---

### Post by Comzee on 2007-06-19
I tried this ```
sudo rm -rf /home/user/.wine
``` didn't work.

Then I started this ```
sudo nautilus
``` but .wine wasn't listed in the browser, WTF.

Then I did this ```
man chmod /home/Comzee/.wine
``` that didn't help me.

Nothing worked, sorry to be a noob here but, I can't get anything to work.

---

### Post by cookies on 2007-06-19
> **Comzee said:**
> I tried this ```
sudo rm -rf /home/user/.wine
``` didn't work.

Then I started this ```
sudo nautilus
``` but .wine wasn't listed in the browser, WTF.

Then I did this ```
man chmod /home/Comzee/.wine
``` that didn't help me.

Nothing worked, sorry to be a noob here but, I can't get anything to work.

. files are hidden. In Nautilus, go to View > Show Hidden Files

---

### Post by Comzee on 2007-06-19
I got steam to work and I'm downloading CSS as I type. :D :D :D :D

There is one thing that I would like to fix though, it's not that big of a problem.

I want the steam store to work but I can't get gecko to work.

I tried this code ```
sudo wine iexplore http://www.google.com
``` but that didn't work.

Is there any other way of installing it.


And thanks to everybody that posted in the thread to help me to get steam working.

---

### Post by Comzee on 2007-06-19
> **Comzee said:**
> Ok, It worked. But once I installed steam all the words on the buttons where gone. I thought I knew Steam well enough to ignore it but, I accidentally exited it out. Now I can't find where it is. So how do I get back into it, and where is the Wine virtual windows drive.

Thanks for the coding to install it though, easer then I thought.



Ok, I got Gecko Web browser to work but now I need to know how to install flash and windows streaming media player plugins into gecko.

That would be really great,

thanks in advance :D

---

### Post by dfreer on 2007-06-19
How did you get gecko working? For me it installs, but none of the webpages actually load, leaving the Steam store blank. 
I don't think it is currently possible to install flash and windows streaming media player into gecko, especially windows streaming media player (which would require windows media player). IE4Linux can handle flash, but I don't know of a way to intergrate it with wine/steam. It runs in its own wine enviroment.

---

### Post by fabertawe on 2007-06-19
Check out **[section 6.1]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wine")**, worked for me with Steam.

Paul

---

### Post by diablofatt on 2007-06-19
Ive got steam up and running.. but it tells me I dont have the diskspace to install CSS. What gives my brother? 

Any solution besides the suicide solution?

---

### Post by dfreer on 2007-06-19
what's your disk usage like?
```
df -h
```

---

### Post by Comzee on 2007-06-19
Well, steam is being gay. Every time I try to load steam up, I get a "blob main exception archive error" I know how to fix that, but then the next time I tried to load it up this happened, "Steam is currently already running" when of course it isn't. The one time I did play it, I set all my graphics options to low and set my resolution to the lowest setting. I got 4 fps on the video stress test:(.

I think Wine isn't the way to go for steam.

---

### Post by dfreer on 2007-06-19
I never get more the 10 fps on the stress test, but in actual gameplay i get around ~70 FPS for CS 1.6, and ~40 for CS:S. 

Your alternatives to wine is dual-booting or cedega, although I doubt you will experience any increase in fps in cedega :(

---

### Post by Comzee on 2007-06-19
> **dfreer said:**
> I never get more the 10 fps on the stress test, but in actual gameplay i get around ~70 FPS for CS 1.6, and ~40 for CS:S. 

Your alternatives to wine is dual-booting or cedega, although I doubt you will experience any increase in fps in cedega :(

I do have dual-boot, I currently have windows XP and Ubuntu. 
I just want to get to the point where Ubuntu can take over as my main OS.

---

### Post by dfreer on 2007-06-20
So do I :) at the rate that wine is moving, hopefully it will work better. There might be some optimizing you can try, have you changed the directx level from 9 to 8 or so? this will increase FPS at the cost of graphics.

---

### Post by Comzee on 2007-06-22
> **dfreer said:**
> So do I :) at the rate that wine is moving, hopefully it will work better. There might be some optimizing you can try, have you changed the directx level from 9 to 8 or so? this will increase FPS at the cost of graphics.

So I fixed all the problems Wine was having with Steam. The sad thing is, I can't play CSS because I only get     4 fps in game. I've tried different kinds if drivers too, none of them helped. It's just because I have a really shitty graphics's card (Xpress 200M) coupled with the game emulating through Wine, not a good combo. Unless the Valve corporation comes out with a Linux version of Steam, I'll never be able to play it on Ubuntu :(.

---

### Post by fabertawe on 2007-06-25
Anyone else have a problem with CSS and jerky BOT player movement? I only have this problem in CSS (despite frame rates averaging about 60-70) which is the odd thing. Sometimes there's a small scrollbar on screen too! I'm using Wine 0.9.37. I'll try *.39 when it's available as a x86_64 deb. I've verified the cache from Steam.

Paul

---

### Post by cody50 on 2007-06-30
for some reason webcontent doesnt show up in my steam window for the store. Anyone know what to do to make that show up? everything else works perfectly

---

### Post by dfreer on 2007-06-30
> **cody50 said:**
> for some reason webcontent doesnt show up in my steam window for the store. Anyone know what to do to make that show up? everything else works perfectly

Try typing this command into terminal:
```
wine iexplore www.google.com
```
It should try to download and install the gecko engine, which is basically a slimmed down firefox from what I understand, and it will then use it to display webpages. If this works, you should see google's search engine. If it doesn't show anything (about 50/50 chance in my experience), you can try a different version of wine (seems like it breaks with every other new release, then they fix it again, then it breaks, etc etc).
Anyways, that is basically the reason why steam store doesn't work. You can also try the mozcontrol plugin that was used before wine implemented gecko, although it never worked that great either.

---

### Post by cody50 on 2007-06-30
Thanks for the help! 

However, I tried it and it just stays on the white window so i guess it failed.
I'm on wine-0.9.37 and havent gone to the latest one because I heard that .38 doesnt work well with steam.

---

### Post by dfreer on 2007-06-30
> **cody50 said:**
> Thanks for the help! 

However, I tried it and it just stays on the white window so i guess it failed.
I'm on wine-0.9.37 and havent gone to the latest one because I heard that .38 doesnt work well with steam.

Latest is 9.40 as of today I believe ;) check winehq for the latest and greatest, or add the winehq repository.

---

### Post by cody50 on 2007-06-30
well, my how things fly in the FOSS community. i love it. off to get some new wine.

---

### Post by cody50 on 2007-06-30
darn, .40 didnt fix the problem and seemed to introduce others. back to .37 for me.

---

### Post by dfreer on 2007-07-01
EDIT: Is it just me, or has all mention of wine 9.40 disappeared of winehq's site? and the appdb is down... wtf? [http://winehq.org](http://winehq.org) also redirects to this simple html page, but [http://www.winehq.org](http://www.winehq.org) works fine:
```
<html><body><h1>It works!</h1></body></html>
```



When you tried 9.40, did you try it with a fresh install of wine? The way I would go about it would be to move the ~/.wine folder that has all of your games somewhere other than ~/.wine, and install whatever version of wine you wish to try with these commands:
```
sudo apt-get remove --purge wine
sudo dpkg -i wine_9.XX_*.deb #whatever the name/version of wine you downloaded
```
From there, run winecfg to create a new ~/.wine, and then immediately try
```
wine iexplore
```
If it doesn't work, try another wine version, repeat process until you find one that works and steam games work fine for you too. Kinda crummy, but if you need steam store it is a solution.

---

### Post by cody50 on 2007-07-01
yeah I was having trouble with steam in that I couldnt move the window and it was taking alot of cpu so I deleted the steam folder in my wine C drive and reinstalled that with wine .37 now it appears to be working fine. I think I can live without the store for now, that way I won't spend all my money! haha. thanks though for the info in case i try to get it working in the future.

---

### Post by giambrone on 2007-08-16
Thanks so much for the tut. on page 2. I've spent hours with the cmultifieldblob error so I just simply took your advice and did a clean install. FIXED!

Matt :KS

---

### Post by b52doc on 2007-08-17
Q: Steam crashes at 26% of the update with a &#8220;Sharing violation&#8221;

Run the following command in the console (substitute the path to steam executables with your path)

    *wine SteamTmp.exe SelfUpdate &#8220;C:\Program Files\Steam\Steam.exe&#8221; 14

      killall wine
      killall wine-preloader
      killall wineserver
      wineboot

I run the command, but I dont know where or how to find my executables :(

UPDATE: I fixed the problem by installing wine from the .exe file and not the MSI file. Updated smoothly :)

---

### Post by semijoyful on 2007-08-27
I have been spilling over all of this great information about wine and steam, but I ran into an error that doesn't seem to be mentioned in these threads.  I could be wrong.  Here's the error I get in the terminal upn trying to run Steam:

root@NinjaBox:~# wine Steam.exewine: could not load L"c:\\windows\\system32\\Steam.exe": Module not found
root@NinjaBox:~# 

I installed the latest wine, followed instructions on loading the Tahoma true type, and I even ran through the setup process with Steam.

2 additional problems is that I don't know where wine is in ubuntu.
and I don't know how to confirm if I actually copied the font over in the directory.
I'm a long-time Windows user that wants to give Linux a try.  I am running Feisty Fawn on a dual boot, Pentium 4 HT with Nvidia card, Xpress motherboard w/ onboard ATI.

Can someone help me with this stuff?  Thanks in advanced!

Cheers,
Semijoyful

---

### Post by mysticmatrix on 2007-08-27
> **Comzee said:**
> Ok I have a some questions.
Crossover seams like it could work but, when I try to open it it has an error, as follows > "gedit has not been able to detect the character coding. Please check that you are not trying to open a binary file. Select a character coding from the menu and try again."
I only have two character coding, "Current locale (UTF-8)" and "Western (ISO-8859-15)"
So whatever.

Anyways, some help on this dumb questions would be great. Thanks for the help so far.

You have downloaded a .sh file. If you have looked on their website seriously, the code to install would be
```

sh <file name of installer>
```

---

### Post by dfreer on 2007-08-27
> **semijoyful said:**
> 
[....]

**root**@NinjaBox:~# wine Steam.exewine: could not load L"c:\\windows\\system32\\Steam.exe": Module not found
**root**@NinjaBox:~# 

[....]

2 additional problems is that I don't know where wine is in ubuntu.
and I don't know how to confirm if I actually copied the font over in the directory.


Firstly, your virtual windows directory in wine is located in a hidden folder called .wine, located in your home folder. So the font should be placed at ~/.wine/drive_c/windows/fonts/
Second, the error you ran into above is most likely due to the fact that you are not telling wine where Steam.exe is located, and so it then searches it's own system33 folder for it. Since it isn't located there, it brings back an error saying the file cannot be found.

You should specify the path to Steam.exe, in most cases it is located at ~/.wine/drive_c/program\ files/steam/Steam.exe
As always, using the "tab complete" feature in the shell, and escaping whitespaces in filenames is recommended.

On a side note, you shouldn't be running wine as root :( Hope this helps!

---

### Post by semijoyful on 2007-08-27
Thanks for the information, dfreer!  I'll go ahead and look into all that you have said.  I totally said (duh!) when you mentioned the fact that the folder was hidden.  Now, it makes sense why I couldn't find it.  I'll post the progress.

Thanks, again!

Semijoyful

---

### Post by semijoyful on 2007-08-28
It worked!  Thanks again&#61514;  Of course, I have another question.
I followed the instructions on Linux-Gamers.net on how to install steam and then half life 2.  However, I am running into trouble with installing HL2.  Here’s the trouble:

I have Half Life 2 on DVD.  So the device is cdrom.  The code that I inserted in the terminal was this:

```
wine msiexec /i /path/to/HL2/steam.msi
```

I’m assuming that path/to/HL2/ is suppose to be changed, so I tried the following:

```
wine msiexec /i /media/cdrom/to/HL2/steam.msi
```

It didn’t work, needless to say.  Also, when I look at the contents of the HL2 DVD there’s no file called steam.msi.  I know I must be missing something.  Any help would be appreciated.

BTW, HL2 is actually one of several Valve games on the Christmas bundle CD.

Thanks!

semijoyful

---

### Post by dfreer on 2007-08-31
Once again, use the <Tab> complete feature in terminal, and the command ```
ls -l
```. I seriously doubt the path is ```
/media/cdrom/**to**/HL2/steam.msi
```.

Start with this command:
```
cd /media/cdrom/
```
and then list the files/folders therein:
```
ls -l
```
It will generally have a install.exe, steam.exe, steam.msi, or some sort of install file. It may very well be located in a folder called HL2/, in that case cd to it, and then check the contents in that folder. I do not know where it is located, because I bought HL2 through steam and I don't have the DVD ;)

Anyways, if you prefer you could explore the contents of your DVD using the GUI, and determine the correct filename from there.

---

