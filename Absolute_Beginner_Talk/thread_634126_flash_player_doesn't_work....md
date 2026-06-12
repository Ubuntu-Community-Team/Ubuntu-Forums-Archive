---
title: "flash player doesn't work..."
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-12-07
i reinstalled ubuntu and after the installation of usual software... 
and then while using firefox i was asked to install the missing plugin...adobe flah player.
although (i think) all the installation process was fine i saw no flah player.
i tried also through the terminal.package.. the same.
the output in the ending was...:
"... 
2900K .......... .......... .......... .......... .......... 99%   72.35 KB/s
2950K .......... ....                                       100%   50.25 KB/s

15:15:50 (117.72 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
"
what's wrong?

---

### Post by Joeb454 on 2007-12-07
I have a similar problem...I installed adobe flash player, firefox and apt both told me that it was installed, yet still no joy (tried a random viseo on youtube)

Installed gnash, and lo and behold, I can watch the videos...though i'd rather have adobe flash, because gnash isn't brilliant...don't get me wrong, it works, but it isn't brilliant.

---

### Post by taurus on 2007-12-07
Shutdown firefox.  Then, from a terminal, install flash plugin as

```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```
Open firefox again and see if it detects flash plugin now.

---

### Post by Joeb454 on 2007-12-07
Not sure about OP, but that never worked from me...got the same result ("this page needs additional plugins...")

---

### Post by bravejamriot on 2007-12-07
when i type in sudo apt-get install flashplugin-nonfree

I get this back. what am I doing wrong?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree

---

### Post by someoneouthere on 2007-12-07
did it still asking for the missing plug in...

---

### Post by someoneouthere on 2007-12-07
on previeus installs it worked just fine...

---

### Post by Joeb454 on 2007-12-07
did you try ```
sudo apt-get update
``` **before** you tried installing?

---

### Post by someoneouthere on 2007-12-07
yes i did both

---

### Post by taurus on 2007-12-07
> **bravejamriot said:**
> when i type in sudo apt-get install flashplugin-nonfree

I get this back. what am I doing wrong?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree

> **someoneouthere said:**
> did it still asking for the missing plug in...

Which release are you running and can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by someoneouthere on 2007-12-07
here it is: "
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
"

---

### Post by bravejamriot on 2007-12-07
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by taurus on 2007-12-07
> **bravejamriot said:**
> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line to comment out the cdrom.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and run

```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by someoneouthere on 2007-12-07
as an absolut begginer i ask: is this somekind of a buf fix?

---

### Post by bravejamriot on 2007-12-07
It ran a lot of stuff but then gave me this at the end. Flash still didnt work.

11:23:08 (340.14 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

---

### Post by bravejamriot on 2007-12-07
I tried this again:
 sudo apt-get install flashplugin-nonfree

Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

but firefox is still saying it is missing the plug in. Is there something I need to do with firefox to get it to recognize the plug in?

---

### Post by Vadi on 2007-12-07
That's weird.

Try doing sudo apt-get install ubuntu-restricted-extras. That installs the usual things like flash, java and such.

---

### Post by bravejamriot on 2007-12-07
hmmm.... it said it installed 41 things, but still firefox says the plug in is missing

---

### Post by Vadi on 2007-12-07
Are you on the 64bit version of ubuntu?

---

### Post by SunnyRabbiera on 2007-12-07
> **Vadi said:**
> Are you on the 64bit version of ubuntu?

thats what I was going to ask, great minds think alike I gess

---

### Post by bravejamriot on 2007-12-07
I'm not entirely sure. How do I check that?

---

### Post by wolfen69 on 2007-12-07
it seems that there is a problem right now with flash.(in ubuntu restricted extras) alot of people are reporting that flash no longer works in firefox and opera. it didnt work for me on 3 different computers. it has always worked before. i have filed a bug report and hopefully this will be fixed soon.

i installed gnash (in synaptic) and got youtube to work in firefox. that's all i know at this point.

---

### Post by FuturePilot on 2007-12-07
The problem is, that the flashplugin-nonfree package contains an MD5sum for the r48 version of Flash. Now that Adobe has released a new version, it's downloading the newer version and the MD5sum doesn't match. So it fails.

---

### Post by Vadi on 2007-12-07
Oh yeah. Well, there are instructions on installing flash by hand, but I wouldn't recommend it to a newbie. Get gnash instead for now.

---

### Post by bravejamriot on 2007-12-07
today is not my day. I installed Gnash using the Add/Remove. Now it doesnt tell me that I am missing the plug in, but where the video would be is just blank.

---

### Post by daradib on 2007-12-08
This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by daradib on 2007-12-10
For more information on this bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

### Post by waspbr on 2007-12-11
great stuff, thanks for the fix, I wasn't too happy about gnash, it sorta slowed down my firefox

cheers

---

### Post by oleschmitt on 2007-12-14
This (.deb) worked for me too.
Thanks a lot.

---

### Post by ingram on 2007-12-14
This post is a great  example of why I say that Ubuntu has the best tech support there is. Ever try to get an answer to a windows problem ? 

Ask in this forum and it is a race to who can answer the question first. :guitar:

---

### Post by philinux on 2007-12-14
Ok so I installed my flash before Dec4 therefore Mines ok cos all it did was update. But if anybody did a fresh install of flash after this date it fails. Is this correct.

---

### Post by Sef on 2007-12-14
> Ok so I installed my flash before Dec4 therefore Mines ok cos all it did was update. But if anybody did a fresh install of flash after this date it fails. Is this correct.

That is correct.

---

### Post by daradib on 2007-12-15
> **ingram said:**
> This post is a great  example of why I say that Ubuntu has the best tech support there is. Ever try to get an answer to a windows problem ? 

Ask in this forum and it is a race to who can answer the question first. :guitar:

Yes, it sure is a race. Sometimes, two people respond (with maybe even the same answer) because they don't realize a post has been made.

> **ingram said:**
> Ever try to get an answer to a windows problem ? 

You sure don't get multiple response from different people nor explanations most of the time. Waste of money is all I hear.

---

### Post by wsonar on 2007-12-19
Tried the fix on page 3 removed non free and installed bug fix still dosen't work on the most important sites myspace nothing works video's or music even the yahoo ads shows but krappy...please when will this be fixed

It's still using GNASH I tried to change the prefered application under firefox preferences but don't have any other plugin options

---

### Post by macogw on 2007-12-19
> **Vadi said:**
> Oh yeah. Well, there are instructions on installing flash by hand, but I wouldn't recommend it to a newbie. Get gnash instead for now.

Why?  It's pretty simple.  (Copying this from my blog)
```
cd ~/Desktop
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar xf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux/
sudo ./flashplayer-installer
```
Now copy this down into gedit or something because it'll tell you to close the web browser. When it asks for the install path for the browser: [list]
[*]If it's Firefox 2, put /usr/lib/firefox 
[*]If it's Firefox 3 and you're fully updated, put /usr/lib/firefox-3.0-3.0b1
[*]If you're using Konqueror with KDE3, it'll be /usr/lib/kde3 but it'll probably tell you that's not a valid place to put it because it doesn't have a plugins directory and a components directory, so then it'll assume Opera, won't find that, and will assume Netscape, and won't find that. You can trick it into thinking it's installing in Firefox by doing 
```
sudo mkdir /usr/lib/kde3/components/
```[/list]

I don't know where Opera and Konqueror for KDE4 put their stuff, so I don't know where those would be, but I'm guessing KDE4's Konqueror would be in /usr/lib/kde4 based on KDE3's and Opera's is probably /usr/lib/opera but I don't have those installed to check.


EDIT: oh ok...a deb was posted.  nevermind.

---

### Post by wsonar on 2007-12-19
yea I tried the deb and it didn't work I now lost sound in all my application I did take the recommended updates that where pushed down today including the kernel update that required a reboot I'm not sure if I lost my sound after that or after the install of the flash package...either way now I got more problems

---

### Post by macogw on 2007-12-19
> **wsonar said:**
> yea I tried the deb and it didn't work I now lost sound in all my application I did take the recommended updates that where pushed down today including the kernel update that required a reboot I'm not sure if I lost my sound after that or after the install of the flash package...either way now I got more problems

It was the kernel update.  The kernel has the drivers.  When you boot, you can use the arrow keys to pick the previous version of the kernel.  You can do
```

gksu gedit /boot/grub/menu.lst
```
and set the line near the top that says > default 0 to say > default 1 if you don't have anything marked "Recovery mode" when you boot up or > default 2 if you do (you probably do....that's default setup).

Try installing Flash like I just posted.

---

### Post by wsonar on 2007-12-19
Weird just a reboot fixed the sound.....I Will try the Manuel flash install..thanks

---

### Post by wsonar on 2007-12-19
Quick easy painless I just had to change the 8 to 9  for the install_flash_player_9_linux guess theres a new ver but hey I can hear my music and see my video's now what more can I ask for.......


Thanks a bunch that was like instantaneous response.  Manuel installs always seem to work better for some reason

---

### Post by macogw on 2007-12-19
> **wsonar said:**
> Quick easy painless I just had to change the 8 to 9  for the install_flash_player_9_linux guess theres a new ver but hey I can hear my music and see my video's now what more can I ask for.......


Thanks a bunch that was like instantaneous response.  Manuel installs always seem to work better for some reason

Nope, I just can't type.

---

### Post by Pechorin on 2008-01-09
I am having exactly the same problems as stated in this thread. Flash Player 9 is allegedly installed but still not working. The manual install however is not working for me. After following the steps provided by macogw, I get this:

>sudo ./flashplayer-installer 

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

The post by daradib refered 64-bits to this page:

[http://bugs.launchpad.net/ubuntu/+so...0.115.0ubuntu2]("http://bugs.launchpad.net/ubuntu/+so...0.115.0ubuntu2")

but the links there are broken. 

I managed to find the binary somewhere else, but I couldn't figure out how to install it (yes, I'm very newbee). 

I downloaded: flashplugin-nonfree_9.0.115.0ubuntu2.tar.gz from here:

[http://mirror.linux.org.mt/mirror/ubuntu-packages/pool/multiverse/f/flashplugin-nonfree/]("http://mirror.linux.org.mt/mirror/ubuntu-packages/pool/multiverse/f/flashplugin-nonfree/")


Greatly apprechiate any further help you can give me. I'm struggling with my new hp tx1000 laptop using Gutsy. Nothing seemes to be working out of the box. And I do mean nothing.

---

### Post by ubuntu-freak on 2008-01-09
The flash plugin is broken in the repo for now that's why.

Download it here [http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466")

Save it to your home folder, then open the terminal and paste this: 

sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb

Hopefully you will be watching youtube after that :)

Nathan
 
Edit: Just realised I posted a duplicated workaround. Ah well...:)

---

### Post by bryncoles on 2008-01-10
actually.... im a fellow 'n00b', having the same problems with flash. this duplicate work-around seems interesting, but i cant try it as i cant save to the home directory, as im apparently not the owner of my laptop! (i guess this is s security thing). 

is there a way i can either get permission to save to the home directory (i currently save everything to the desktop and then file it away later), or tell sudo to install from the file on the desktop....?

thanking in anticipation.... ;-)

*edit*

actually, ive had a success with flash videos by installing the 'mplayer' firefox plugin (which div x's website recommended for viewing their content). 

Pechorin, if you click applications, add/remove and search for 'mplayer' you should have the hit for the firefox plug in. try installing that and restarting your browser. hopefully that'll help you view some (if not all) flash videos you need. 

if (like me) you're using the no script add on for firefox, you might also have to at least temporarily give permission for the site you're trying to view to run java.

you might need to activate the universe or multiverse repositories in synaptics manager though (can a more experienced user please confirm this for me?)

i hope you (and i) get things working soon, so you can enjoy the linuxy goodness!

---

### Post by ubuntu-freak on 2008-01-10
MPlayer plugin doesn't play flash videos. 
 
Here is a link that might help you with that permissions problem.
 
[http://ubuntujourney.blogspot.com/2006/12/i-changed-permission-of-home-folder.html](http://ubuntujourney.blogspot.com/2006/12/i-changed-permission-of-home-folder.html)
 
Navigate to your desktop with the terminal 
 
cd /home/username/Desktop
 
Use sudo if you have to. Or press alt+f2 and type gksu nautilus. That gives you admin status in nautilus.
 
So hopefully now you can try those commands posted earlier.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-10
If anyone is having problems streaming from BBC, stage6 (divx.com), yahoo movies and wherever else, I posted a guide recently and tried to make it as simple as possible for nu ubuntus :)
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Also, if you're a UK taxpayer like me you should email the BBC and complain as they are a public service and should offer open source streaming formats. It's a requirement really due to nature of the BBC.
 
Nathan

---

### Post by bryncoles on 2008-01-10
ah! i have got everything working now!

thats ace, thank you!

---

### Post by strik9 on 2008-01-28
> **reassuringlyoffensive said:**
> The flash plugin is broken in the repo for now that's why.

Download it here [http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466")

Save it to your home folder, then open the terminal and paste this: 

sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb

Hopefully you will be watching youtube after that :)

Nathan
 
Edit: Just realised I posted a duplicated workaround. Ah well...:)

just wanted to say thanks ive been trying for a week to get flash to work and thanks to you it does now =]

---

### Post by Amstell on 2008-01-28
the best way to install flash right.

Installing Flash

   1. download adobe flash by hand
   2. extract libflash.so
   3. cut and paste the .so to /usr/lib/firefox/plugins/


```
      sudo nautilus /usr/lib/firefox/plugins/
```

   4. make sure the .so is readable by everybody
   5. restart firefox

good luck

---

### Post by ubuntu-freak on 2008-01-28
> **strik9 said:**
> just wanted to say thanks ive been trying for a week to get flash to work and thanks to you it does now =]

 
No problem!
 
If you want to get everything internet, multimedia and video related working, try my easy how-to
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Man can't survive on flash alone. :-)
 
Nathan

---

