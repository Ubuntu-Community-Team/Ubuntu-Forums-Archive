---
title: "Need help with Wine."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by tarchy on 2007-05-15
I have absoloutly no idea how to use Wine, I have no idea what to download, what the hell am I supposed to do :P

I just want to install Steam (steampowered.com) and a few other programs that only work with windows. :( 

Any suggestions?

---

### Post by tarchy on 2007-05-15
Hehe am I really that helpless?

---

### Post by tarchy on 2007-05-15
I have downloaded this;
[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449)

I really have no idea what to do next...please help

---

### Post by Nythain on 2007-05-15
to install wine in ubuntu
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
just follow those directions
to use first in terminal type
winecfg
to set it up, it will create the directories it needs and whatnot
to use it
in terminal
wine /path/to/the.exe

---

### Post by tarchy on 2007-05-15
How do I open terminal?

---

### Post by Dr Small on 2007-05-15
Check out this site:
[http://psychocats.net/ubuntu/wine](http://psychocats.net/ubuntu/wine)

Dr Small

---

### Post by tarchy on 2007-05-15
Thanks. But I still need to know how to open terminial :(

---

### Post by lebe0024 on 2007-05-15
Tarchy, the terminal is how you type commands into your system. It's not always necessary to install things via the terminal, but many of these "howtos" useterminal  commands because it's quicker and easier to explain.  The "terminal" is under applications->accessories. You use it so often, I would probably drag and drop it onto your toolbar.

---

### Post by lebe0024 on 2007-05-15
I'm a huge newbie and I just installed wine last night so i can help you.  

First follow Nythain's instructions, and install wine using the instructions from wine's website.  The difference between using wine's version and Dr. Small's version is this: Using the wine instructions you will be installing it and automatically updating it directly from wine.  Using Dr. Smalls instructions, you will be installing it and updating it through ubuntu's official repositories - which I believe will only update critical security errors.  Using the wine repositories, you will always have the latest version of wine, which is good because they fix a lot of bugs.

Also, I followed these instructions to install steam and counter strike source:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

---

### Post by adamklempner on 2007-05-15
In case Wine doesn't work out so well for you, Codeweavers.com sells a commercialized version of Wine called CrossOver Office that has a nice graphical interface.  I think it costs $40, but it was a lot easier for me than getting everything to work with Wine.  I needed MS Office and MathCad to run, and CrossOver did a nice job of it.  I think they are providing a free, fully functional trial version to see if it does what you need.

It is one of the few commercial products for Linux that I think is worth the money.

---

### Post by Jordy_U on 2007-05-15
I am just successfully installing wine on 7.04
first you must have Internet connection from your Ubuntu 7.04,
then go to this page
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

the follow this instructions:

Adding the WineHQ APT Repository:
First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Feisty (7.04):
sudo wget [http://wine.budgetdedicated.com/apt/....d/feisty.list](http://wine.budgetdedicated.com/apt/....d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

Hope this help
:)

---

### Post by tarchy on 2007-05-15
Thank you so much for your help everyone, I think I get it now :).

Lebe, thanks for the link to install CS: S since I really needed that :D

---

### Post by tarchy on 2007-05-15
I am having real trouble with installing CS 1.6..

It says to do this; > nstead of using binaries, you may compile the latest source yourself. You may use WineCVS to compile Wine from CVS.

[http://winecvs.linux-gamers.net/](http://winecvs.linux-gamers.net/)

Needed apps, packages, libraries:
wget, fontconfig, freetype2, freetype2-devel, bison, flex, libjpeg, libjpeg-devel, libpng, libpng-devel, zlib, zlib-devel, xorg-x11-devel (resp. XFree86-devel), Mesa (resp. xorg-x11-Mesa, XFree86-Mesa), Mesa-devel (resp. xorg-x11-Mesa-devel, XFree86-Mesa-devel), freeglut, freeglut-devel

Debian or Ubuntu users can just use:
apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev

but I get this error: > : Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


I also have NO idea what this means > Change to the location where the WineCVS.sh is lying and start it with:

sh WineCVS.sh and I don't know how to change the location of anything..

Please help! :(

Change to the location where the WineCVS.sh is lying and start it with:

sh WineCVS.sh[/

---

### Post by lebe0024 on 2007-05-15
Dont install Wine from CVS.  Install wine from the directions on winehp.org : [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Then, use the directions from linux-gamers.net, but skip the "install wine" section of the tutorial.

---

### Post by tarchy on 2007-05-15
tarchy@tarchy-desktop:~$ wine msiexec /i SteamInstall.msi
err:msi:copy_package_to_temp failed to copy package L"SteamInstall.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002!
tarchy@tarchy-desktop:~$ wine

---

### Post by Hobo Joe on 2007-05-15
First, get WINE installed.
Then you need to download the Steam installer to your desktop. 
Then, open the terminal, and type:
```

cd Desktop

```
Then type:
```

wine SteamInstall.exe

```

Make sure you have the tahoma font installed, or you won't be able to see any text in Steam. To do this you need to first:
Click the first link on [this]("http://www.google.com/search?q=filetype%3Attf+inurl%3Atahoma") page.
Then hit alt+F2, and type:
```

gksudo nautilus

```
Then paste the font file to the "usr/share/wine/font"

That should be it. Tell me if you have any problems.

---

### Post by tarchy on 2007-05-15
Thank you so much for the help. I have one more problem that you may be able to help me with. When I try to past the font into the folder it says I do not have permission. I am the root admin of the computer and have no idea why this is happening :P

---

### Post by Hobo Joe on 2007-05-15
Yeah, that's why you need to open it as sudo.
Press alt+F2, then type in:
```

gksudo nautilus

```
That will give you root permission as long as you leave that window open, once you close it, root permission will be locked again.

---

### Post by brharri1 on 2007-05-27
Can anyone confirm for me that the wine repository is down? I can't connect to it.

---

