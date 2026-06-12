---
title: "Dependency errors when trying to install Wine"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by bostock73 on 2007-12-08
Hey guys! finally made the switch to linux after much hesitation.
I got ubuntu up and running.
My main concern was how to run/install stuff; and this is why i'm here lol.

ok, so i've charged full steam ahead; trying to get some stuff installed and under my belt from the offset.

i dont understand ANY OF this terminal stuff, none of it.

the first thing i'm having problems with is beep media player.
it cant be found in the package manager.

i extracted it onto the desktop.
i went into terminal and typed /home/*name*/Desktop/beep-media-player.

it recognises the directory.. but.. now what?
I'm really sorry if you guys get annoyed at these types of post but i'm sure you can help me.

another thing is on the package manager i tried to download WINE.

I click the box for donwload on 'wine' but get this message -


"wine:
 Depends: binfmt-support (>=1.1.2) but it is not installable
 Depends: libaudio2  but it is not installable"



Any help please guys?
thankyou, and this linux is great!

---

### Post by wjp.reg on 2007-12-08
> **bostock73 said:**
> Hey guys! finally made the switch to linux after much hesitation.
I got ubuntu up and running.
My main concern was how to run/install stuff; and this is why i'm here lol.

ok, so i've charged full steam ahead; trying to get some stuff installed and under my belt from the offset.

i dont understand ANY OF this terminal stuff, none of it.

the first thing i'm having problems with is beep media player.
it cant be found in the package manager.

i extracted it onto the desktop.
i went into terminal and typed /home/*name*/Desktop/beep-media-player.

it recognises the directory.. but.. now what?
I'm really sorry if you guys get annoyed at these types of post but i'm sure you can help me.

another thing is on the package manager i tried to download WINE.

I click the box for donwload on 'wine' but get this message -


"wine:
 Depends: binfmt-support (>=1.1.2) but it is not installable
 Depends: libaudio2  but it is not installable"



Any help please guys?
thankyou, and this linux is great!

You can stay clear of problems by using Synaptic Package Manager to install/uninstall programs.  You don't download anything like you would in Windows unless you want to be  a hero or you already are a guru ;-)

If you are not finding packages you need to edit the /etc/apt/sources.list to include repositories and if none of this makes sense you need to do a whole lot more searching of the ubuntu forum site as this is all explained to those who help themselves :-)

Good Luck, and Welcome!!

---

### Post by SpacePilot on 2007-12-08
Regarding the bleep media player you have to read the documention. Start with the README or HOWTO_INSTALL or something in the files you downloaded.

To install wine you can just type

sudo apt-get install wine

---

### Post by bostock73 on 2007-12-08
to wjp, i would use synaptic package manager but beep isnt on there.
to space pilot i have read the documentation and im stuck in this one thing.

it says to navigate to the directory, so i type
/home/matt/Desktop/beep

when i press enter does that mean im in it?
cus it then asks me to 'type'... and it literally says 'type' /.configure.


but when i do that, it says no directory.

do i have to put the /.configure straight after the /home/matt bit?

i'm having this trouble with flash aswell.


'   1.  Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.'


see on 4, navigate to this terminal and TYPE? does it mean all together? like
/home/matt/Desktop/flash./FLASHPLAYER-INSTALLER

or after each other?

please help.

---

### Post by mali2297 on 2007-12-08
You can install Flash from Synaptic, see here
[http://ubuntuforums.org/showthread.php?t=634078?post=#5](http://ubuntuforums.org/showthread.php?t=634078?post=#5)

If you get problems with the install, see post #6 in the same thread.

---

### Post by wjp.reg on 2007-12-08
> to wjp, i would use synaptic package manager but beep isnt on there.
to space pilot i have read the documentation and im stuck in this one thing.

it can be found in the archive.ubuntu universe repositories.  Do you have this enabled in your sources.list?

---

### Post by mali2297 on 2007-12-08
> **wjp.reg said:**
> it can be found in the archive.ubuntu universe repositories.  Do you have this enabled in your sources.list?

This can also be done in Synaptic. Look in the menu Settings->Repositories.

---

### Post by bostock73 on 2007-12-09
ok, i got flash installed but still having problems with wine.

when i mark wine to download i get the error 'binfmt-support' to be installed,

i mark it, and then i get the error 'wine:
 Depends: libaudio2  but it is not installable'

???

---

### Post by bostock73 on 2007-12-09
i tried to install wine from the terminal.
got an error.
this is the whole text


matt@Gareth:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  wine: Depends: libaudio2 but it is not installable
E: Broken packages


what now?

---

### Post by bostock73 on 2007-12-09
so ive got ubuntu, and i am a complete newbie.
I've had it about 2 weeks now and havent been able to install ANYTHING.
i installed flash, but thats becuase in the folder there was an install icon; i clicked it and it installed.

I seriously want wine but the following program is winding me up to the point where i think linux is just too much hassle and simply for people who have way too much time on their hands (no offence; just frustrated)


i go to synaptic package manager, search 'wine'
i mark it and immediately after get this dialogue box

'binfmt-support' to be installed.

i then click mark.
then i get the bloody error thats causing me problems.

an error box comes up saying 

'wine:
 Depends: libaudio2  but it is not installable'

what the hell?


the SAME EXACT thing when trying to download vlc media player.

i mark the first dialogue box then i get an error box saying

'vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libsdl-image1.2 (>=1.2.5) but it is not installable
 Depends: ttf-dejavu  but it is not installable'.


this is ANNOYING!!!!!!!!!!!!!!!!!!!!

Im using ubuntu 7.10

i HAVE EVERY repository box clicked becuase people have told me to check different ones.

help please!

also look at my similar thread at
[http://ubuntuforums.org/showthread.php?t=635342](http://ubuntuforums.org/showthread.php?t=635342)

---

### Post by mcduck on 2007-12-09
Open a terminal and run the following commands (and post their output here):
```

sudo apt-get update
cat /etc/apt/sources.list
```

(Just in  case you didn't know it yet, you can copy&paste from a terminal by selecting the text you want to copy and then using middle-click to paste it, so you don't need to type all that text by hand)

---

### Post by CaptainInsaneO on 2007-12-09
I've found that installing things through terminal using apt is actually much easier and effective. I hardly ever use Add/Remove unless I'm looking for information on applications.

So, do this for Wine:

```
sudo apt-get install wine
```

And this for vlc

```
sudo apt-get install vlc
```

---

### Post by bostock73 on 2007-12-09
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties

---

### Post by jordanmthomas on 2007-12-09
You've got most things NOT enabled.
FIrst, put a # at the start of the cd-rom line (line #1)
Take the # off the beginning of each line that starts like
```
# deb htt.....
```
then
```
sudo apt-get update
```

---

### Post by CaptainInsaneO on 2007-12-09
And add an # before the first line.

---

### Post by skymera on 2007-12-09
from what i see you only have 4 sources its using.

take the # away from all lines that begin with deb

---

### Post by jordanmthomas on 2007-12-09
By the way, to edit the file:
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by CaptainInsaneO on 2007-12-09
Nice sig, jordan. :lolflag:

---

### Post by jordanmthomas on 2007-12-09
> **CaptainInsaneO said:**
> Nice sig, jordan. :lolflag:
Thanks, I saw it on a poster and it blew my mind.
Oh, and I just noticed it's similar to yours.
:lolflag:

---

### Post by BIGPutso on 2007-12-09
Im going to go ahead and recomend that you use automatix because i have got to tell you once you install it you won't have to mess with ubuntu much other than the eye-candy.

---

### Post by jordanmthomas on 2007-12-09
> **BIGPutso said:**
> Im going to go ahead and recomend that you use automatix because i have got to tell you once you install it you won't have to mess with ubuntu much other than the eye-candy.

There's really no need for automatix anymore.  Everything it does can be achieved without any hassle.

---

### Post by Sef on 2007-12-09
> Im going to go ahead and recomend that you use automatix because i have got to tell you once you install it you won't have to mess with ubuntu much other than the eye-candy.

Automatix may cause your system to be reinstalled.


As for getting all the repositories, the easiest way to get them is 

1) Applications > Add/Remove

2) Set the top right box to 'All Available Applications.'

---

### Post by mcduck on 2007-12-09
Yeah, you definitely don't have all the repositories enabled, propably because you didn't have a working internet connection during the install. Edit the file so it looks like this, save, and then run 'sudo apt-get update'. After that installing programs should work correctly:
```
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted
#deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
```

---

### Post by oldos2er on 2007-12-09
A couple things: first, open up System, Administration, Software Sources, and under the Ubuntu Software tab, make sure each box is checked (underneath 'Downloadable from the Internet').

 Then, open Synaptic Package Manager, under the Edit menu, click 'Fix Broken Packages.' Once that's done, hit 'Reload.'

---

### Post by daradib on 2007-12-09
You can also go to System -> Administration -> Software Sources. Check the boxes next to main, universe, multiverse, restricted (these names will be in parentheses). Then go to the Updates tab, and check gutsy-security and gutsy-updates (again, these names will be in parentheses) if not done so already.

---

### Post by ssh on 2007-12-13
thanks daradib, it worked like charm after following your instructions....

---

