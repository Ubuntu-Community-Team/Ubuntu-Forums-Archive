---
title: "Setup woes from a Linux newb..."
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by MrSeth on 2007-02-17
Okay, long story here, but I'll do my best to keep it to the point.

I'm an utter newb to Linux, but after repeated XP crashes, I decided "enough". I pulled out a spare hard drive, hooked it up to my POS everything's-integrated-to-heck-and-back HP, and installed Ubuntu. It went off without a hitch, much to my delight... unfortunately, I did this at 3 AM, and I botched something up when I created my user account. It wouldn't let me log in. 

No problem, right? I figured a reinstallation would be easy enough to do. And it was... except for the fact that whilst the first hard drive, which had XP installed on it, was plugged in, it wouldn't let me overwrite the Linux install I'd already done. So I unplugged it, not realizing that it would overwrite the GRUB boot loader as well - eliminating my dual-boot option. 9_9;; What's more annoying, I can't even plug in that hard drive, as when I do the GRUB boot loader doesn't work properly. It's pretty obvious that it's reading the Windows drive as "drive one", what it thinks it should be booting Ubuntu from, and the Ubuntu drive as a secondary drive.

So anyway, I need two things to get up and running with Ubuntu:

1) Proper command lines for GRUB to boot WinXP off my first drive and Ubuntu off my second one - I would kinda like to keep WXP around for my parents, who also use my compy.

2) My internet access is... null and void right now. I rely on a D-Link WUA-2340 wireless USB dongle to access my network, and Ubuntu doesn't recognize it. I downloaded ndiswrapper in hopes of getting it to work, but the instructions are over my head - again, the newb factor working its way in. 

Any help you could give me would be appreciated greatly.

---

### Post by Denn1s on 2007-02-17
as for ur first problem, i think u will need to reintall grub, wich is very easy, just follow this instructions:
[http://ubuntuforums.org/archive/index.php/t-24113.html]("http://ubuntuforums.org/archive/index.php/t-24113.html")

---

### Post by old_geekster on 2007-02-17
You say with the XP hard drive connected, it won't let you install Linux.  Well, you should connect both of them, enter the BIOS, and set the "Boot Order"  to boot first to the CD/DVD ROM.  Then, reboot.  This will eliminate the hard drives from the equation.  Make sure that your CD/DVD is in the drive.

I am a newbie with only about two month's experience, but I have installed Ubuntu Edgy Eft 6.10 at least 11 times in the past two weeks.  This either makes me an expert or stupid. :confused:   If you can't fix it one way, simply do a complete new install.  This is my trouble-shooting method.

You must have both drives connected, because GRUB installs on the first sector of the drive with Windows on it.

Good luck!

p.s. We will be here if you have more questions.

---

### Post by sunexplodes on 2007-02-17
The ndiswrapper thing is a lot easier than it looks.

I have a d-link usb connection too, and it works really well. Here's a brief instruction:

1) Make sure ndiswrapper and ndiswrapper-common are installed

2) put your wireless driver CD in and use the terminal to navigate to the folder that actually contains the windows drivers.

3) use the terminal to install the INF files in that directory with the command 
```
ndiswrapper -i yourdriver.inf

```
for instance, MY config has the files NetA5AGU.inf and athfmwdl.inf, so my install would look like

```
ndiswrapper -i NetA5AGU.inf
ndiswrapper -i athfmwdl.inf
```

4) once you've done that, type 
```
ndiswrapper -l
```
which should list installed drivers, if it says "driver installed, hardware present", you're in the clear.

5) type
```
ndiswrapper -m
modprobe ndiswrapper
```

Then reboot, and you'll be in okay shape, more than likely.

---

### Post by MrSeth on 2007-02-17
Suddenly, it becomes clear that my problem wasn't the fact I was tired.

I just ran the user setup for Ubuntu (at the terminal, "sudo oem-config-prepare"), rebooted, and set up my user account. I put down my real name for my "full name", my first name for my "user name", and 1111 for a password - no caps, no nothing - and when I attempted to log in it told me that I had the wrong username or password. Worse, I can't log in as the basic "sudo" or "oem" logins.

Anyone have any bright ideas? `Cause I'm all ears here.

Oh - and to the guys who answered my questions...

denn1s - Thanks, that looks like it'll help when I get it reloaded properly.

old_geekster - Hey, I'm a Linux newb, not a computing newb! It runs the installer program, it just won't give me the option to use the drive that Linux is installed on... at ALL... unless I unplug the WinXP drive, thus rendering the slave drive Ubuntu is installed on the only hard drive in the computer.

sunexplodes - Well, my problem was really just getting ndiswrapper installed in the first place... the "make" commands didn't work for me. Is there something not included with the base Ubuntu installation I'm missing?

---

### Post by sunexplodes on 2007-02-17
Yeah, you should be able to get ndiswrapper from the install cd. You should be able to use Synaptic or apt-get to do it, and failing that, you can probably navigate to the deb file on the installation cd, should be in pool/n, or some variation of that.

Another thing, if MAKE didn't work, you probably need the build-essential package, which is likely also on the cd.

---

### Post by MrSeth on 2007-02-17
Okay, I'm going down to run the install... again. Where would the build-package be on the CD, and how do I install it? Keep in mind this is the x86 installer, not the live-CD.

---

### Post by maniacmusician on 2007-02-17
you don't need to compile it (all that "make" stuff). If you want to install ndiswrapper, go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and search for ndiswrapper. You need the package called ndiswrapper-common. put that on your linux computer, double click it to install.

however it feels like ndiswrapper is the least of your worries....how are you doing stuff on the linux box if you can't even log in? which is a really odd problem by the way. I've never even heard of that happening.

---

### Post by MrSeth on 2007-02-17
Frankly, I'm not right now. When I first install it, I can get in under the "oem" or "sudo" usernames - the automatically created, temporary user accounts. As soon as I try to create my new account, it essentially locks me out. This time I'm just going to keep the oem/sudo accounts for the time being... I can't really think of a reason not to, come to think of it.

---

### Post by sunexplodes on 2007-02-17
1) Why are you using the OEM install? You should give the regular Text Install, it lets you set up your own username/pass during the install process.

2) The Ubuntu CD should have a directory like /pool/main, in which there are folders labeled a, b, c, etc.. which contain various deb packages. ndiswrapper would be in the folder labeled "n", and build-essential would theoretically be in "b". I don't have a cd handy, so i'm not 100% sure of the paths, but you should be able to figure it out without much trouble.  But anyway, just use the ndiswrapper deb file on the cd, you don't need to build it from source.

---

### Post by MrSeth on 2007-02-17
Okay, update: I now have a WORKING username/install (by setting it up again, using no numbers or uppercase letters in either). That's the good news. 

ndiswrapper is still giving me problems. I just installed it via the package suggested above - thanks again, Maniacmusician - but when I use the "ndiswrapper -i whateveritis.inf", I get an error message about no version of ndiswrapper being found!

Is there a specific file I have to write the drivers into? And if so, how the heck do I access it? When I tried to go into filesystem (which, I'm assuming, is the C: drive) I found that I couldn't so much as make my own new folder. Perhaps I'm missing something in the preferences?

---

### Post by sunexplodes on 2007-02-17
okay, what version of ndiswrapper did you install?

if i recall correctly, there are two packages that need to be installed. you should have:

ndiswrapper-common
ndiswrapper-utils(-1.1, or -1.8 depending on your version of ubuntu)

---

### Post by sunexplodes on 2007-02-17
> **MrSeth said:**
> Okay, update: I now have a WORKING username/install (by setting it up again, using no numbers or uppercase letters in either). That's the good news. 

ndiswrapper is still giving me problems. I just installed it via the package suggested above - thanks again, Maniacmusician - but when I use the "ndiswrapper -i whateveritis.inf", I get an error message about no version of ndiswrapper being found!

Is there a specific file I have to write the drivers into? And if so, how the heck do I access it? When I tried to go into filesystem (which, I'm assuming, is the C: drive) I found that I couldn't so much as make my own new folder. Perhaps I'm missing something in the preferences?

no, the problem of no ndiswrapper being installed is one i've encountered before, it's got nothing to do with the drivers themselves.

---

### Post by maniacmusician on 2007-02-18
as sunexplodes said on the previous page, do not use the OEM install. You need the regular "text install" to get everything working the way it should be. the OEM install is likely what's causing all your problems. Redo it with the regular text install, and all your read/write issues should be fixed. After that, use ndiswrapper to install the driver.

From what it says on the ndiswrapper website about your usb device, you need to go the d-link website and download the driver from there. After extracting all the files, you need to use the NetA5AGU.inf file. This is according to someone else who used ndiswrapper with the same card, and according to them, that's what made it work.

I got that info from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) and doing a search for "WUA-2340" on that page.

edit: also, as sunexplodes pointed out, you need two packages from package.ubuntu.com, my bad. As he/she said, you need the following:
ndiswrapper-common
ndiswrapper-utils(-1.1, or -1.8 depending on your version of ubuntu)

so make sure you have them both. 

PS: and don't do any more OEM installs! ;)

---

### Post by MrSeth on 2007-02-18
If I need to reinstall, I'll do it that way. >___>; I'm in no rush to do that again, especially since I just got it to start working.

Now, I got the ndiswrapper-commons installed, I downloaded the ndiswrapper-utils, and I'm back to square one - no idea how to set them up. Apparantly that's the package I got earlier that required the "make" command that wasn't working. x_x;;

---

### Post by MrSeth on 2007-02-18
Update: build-package finally installed, make command worked, ndiswrapper installed successfully, hardware and driver both work...

...but I can't get iwlist/iwconfig to set up my wireless network. Going from the ndiswrapper installation wiki, I put in "iwlist wlan0 scan" - the result was an error message stating that the interface doesn't support scanning. So I went for the next command, "iwconfig wlan0 essid ESSID". The result was an error that said "SET failed on device wlan0; operation not permitted". 

Now, this might be linked to why I can't create folders... when I went into permissions (on the File System preferences) it said I can't change permissions because I'm "not the owner". Am I missing something here?

---

### Post by maniacmusician on 2007-02-19
perhaps the OEM user has permissions?

as a quickfix, you could try adding yourself to the "OEM" group, but if i were you, I'd just go with a clean install and do away with all that OEM crap. 

oh, and to use iwconfig, you need to have administrator priveleges. Put sudo in front of the command to do that.

"sudo iwconfig wlan0 essid ESSID"

It'll ask for your password. Type it in (it wont show up on the screen for security reasons, but it'll still be inputing it), hit enter, and it should set the essid for you.

---

### Post by MrSeth on 2007-02-21
After many... many attempts to install ndiswrapper unsuccessfully, I realized the problem lay in the inability to create files anywhere in the filesystem. Without the "owner rights", I couldn't to jack-diddly-squat. And the installer, presumably severely glitchy, wouldn't give me those rights... 

So, thoroughly disgusted with the base build of Ubuntu, I decided to try Kubuntu. Installed it without a hitch last night, and it erased most of my problems. The only one I've got right now is the fact that it doesn't have Debian or the build package preloaded into it, so I've gotta get those downloaded off the other comp I'm using now and transferred over... I already have ndiswrapper on disk.

So now, thanks to all of your expert advice on getting Ubuntu running, all I really need are two things. One, a list of packages I should download and install to get Kubuntu at maximum efficacy. I seem to need the build-package, as I tried running "make install" etc. for ndiswrapper and nothing happened... anything else I should look for? 

And two, how in Foglio's name do you expand screen rez past 1024x768? I typically run 1200x900.

---

