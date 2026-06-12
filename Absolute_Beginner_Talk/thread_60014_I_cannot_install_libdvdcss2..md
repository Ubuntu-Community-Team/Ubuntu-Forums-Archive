---
title: "I cannot install libdvdcss2."
date: 2005-08-26
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2005-08-26
Been trying to install libdvdcss2 with no luck

I've tried everthing from UbuntuGuide.org but nothing. Played around with my source.list file and still no luck.

when I try to apt-get install it, I get this message:

Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

can someone please help me?

---

### Post by frodon on 2005-08-26
You should post here your source.list file if you want someone to help you, because the problem could come from this file.```
sudo gedit /etc/apt/sources.list
```

---

### Post by Lord Illidan on 2005-08-26
Try using Synaptic... search for libdvdcss

---

### Post by ROUBOS on 2005-08-26
I tried Synaptic... could not find it.. :(

Here is my source.list file:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted

deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

#########AMD64
## amd64 users repository
deb [http://tamir.nooms.de/ubuntu/](http://tamir.nooms.de/ubuntu/) hoary main universe multiverse restricted

## CVS snapshots packages
deb [http://tamir.nooms.de/ubuntu/](http://tamir.nooms.de/ubuntu/) cvs main universe multiverse restricted

## amd64 packages testers repository
deb [http://tamir.nooms.de/ubuntu/](http://tamir.nooms.de/ubuntu/) tests main universe multiverse restricted
##############

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by frodon on 2005-08-26
try add the hoary multiverse repository
```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
```
BE CAREFUL WITH [BACKPORT](http://www.ubuntuforums.org/showthread.php?t=45047&highlight=backport)  !!!!!!!!!!!!!! use it only if you are looking for a specific software or version, I recommend you to comment the backport repository lines (the 2 last lines of your file).

---

### Post by Lord Illidan on 2005-08-26
You are using AMD 64 bit? That might be the source of the problem... Why not try and compile libdvdcss?

I would give u the link but the site is down at the moment...

---

### Post by ROUBOS on 2005-08-26
Edited the source.list file as mentioned, I updated.. then tried to install again.

No luck....

I should try the AMD64 forum then... maybe that's my problem..

---

### Post by Tinuz on 2005-08-26
I have an AMD64 and downloaded it here:[ftp://ftp.nerim.net/debian-marillat/pool/main/libd/libdvdcss/](ftp://ftp.nerim.net/debian-marillat/pool/main/libd/libdvdcss/)
(Please, i would have hosted it myself, but gftp has a will of its own(wants to go local for no reason))

simply pick the A64 package and do a dpkg -i on it.

---

### Post by gez on 2005-08-31
I get exactly the same message when trying to install "libdvdcss2", I don't have an AMD64 though, so maybe that's not the problem. It's clearly not mine.

---

### Post by Kyral on 2005-08-31
[QUOTE=frodon]try add the hoary multiverse repository
```
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary multiverse
```
BE CAREFUL WITH [BACKPORT]("http://www.ubuntuforums.org/showthread.php?t=45047&highlight=backport") !!!!!!!!!!!!!! use it only if you are looking for a specific software or version, I recommend you to comment the backport repository lines (the 2 last lines of your file).[/QUOTE]

*SMACK* Nothing wrong with the backports! Its official now :P

---

### Post by frodon on 2005-08-31
[QUOTE=Kyral]*SMACK* Nothing wrong with the backports! Its official now :P[/QUOTE]
what recently changed in backports ?

---

### Post by Steve1961 on 2005-09-05
I have an AMD 64 set up and I used a script, that should already be on your system, to install libdvdcss2.  You'll need to install build-essential, fakeroot, debhelper and the linux headers for your version of Ubuntu.  Then type:

cd /usr/share/doc/libdvdread3/examples
sudo ./install-css.sh

You get a warning that this is experimental and a prompt to make sure you have the essential packages installed first.  You then have the option to continue or abort.  I decided to run it, and it churned out lots of stuff in the terminal.  But once It had finished DVDs played straight away.

---

### Post by filemanager on 2005-09-07
[QUOTE=Steve1961]I have an AMD 64 set up and I used a script, that should already be on your system, to install libdvdcss2.  You'll need to install build-essential, fakeroot, debhelper and the linux headers for your version of Ubuntu.  Then type:

cd /usr/share/doc/libdvdread3/examples
sudo ./install-css.sh

You get a warning that this is experimental and a prompt to make sure you have the essential packages installed first.  You then have the option to continue or abort.  I decided to run it, and it churned out lots of stuff in the terminal.  But once It had finished DVDs played straight away.[/QUOTE]
 Thank you!! It worked perfectly on my system :)

---

### Post by Steve1961 on 2005-09-07
Glad it worked for you too.

---

### Post by linewb on 2005-11-13
i've tried this and other manual techniques and always get the same message:

dpkg: status database area is locked by another process

any suggestions?

---

### Post by frodon on 2005-11-13
You can't run an install script if you have another process which handle installs opened.
So you got this message, i think, because you're trying to run an install script in a terminal while you have synaptic opened. Maybe i'm wrong but i got this message always in this case

---

### Post by linewb on 2005-11-13
thanks a lot.  got it installed.  vlc player still doesn't work, though.  i don't think it's detecting a dvd in the drive.  it detects and plays cds, but not dvds.  this seems to be a pretty common problem, but i can't find a solution that works.  any help?

---

### Post by frodon on 2005-11-13
Try the totem-xine package, if you have libdvdcss2 installed it should work.

---

### Post by linewb on 2005-11-13
Thanks, frodon.  i appreciate your help.  unfortunately i've installed xine and it says there is no input plugin for /dvd and can't read /dev/dvd.  anyone resolved this?

---

### Post by frodon on 2005-11-14
I think you have a problem with your libdvdcss2 installation, i never had problems reading dvd or installing libdvdcss2.
However you could try to install libdvdcss2 using this way : [http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs)

---

### Post by linewb on 2005-11-14
thanks again, frodon.  it must be something to do with the codes, because both players have no problem recognizing audio cds.  i ran into some errors when following the instructions pointed to by your (very helpful) link.  when i ran the install in the terminal i got the following message:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libdvdcss2: Depends: libc6 (>= 2.3.4-1) but 2.3.2.ds1-20ubuntu14 is to be inst alled
  sun-j2re1.5: Depends: libasound2 (> 1.0.9) but 1.0.8-1 is to be installed
               Depends: libc6 (>= 2.3.4-1) but 2.3.2.ds1-20ubuntu14 is to be ins talled
E: Broken packages


then i went into synaptic and tried to mark what was available for upgrade (only possible choice other than removal and complete removal) and got this:

libdvdcss2-dev:
  Depends: libdvdcss2 (=1.2.9-1ubuntu2) but 1.2.8-1 is to be installed

and:

libdvdcss2:
  Depends: libc6 (>=2.3.4-1) but 2.3.2.ds1-20ubuntu14 is to be installed

since we're on the absolute beginner forum, i guess i don't have to tell you i have little idea what that means.  anyone out there got some suggestions?

---

### Post by ecobuntu on 2005-11-14
[QUOTE=linewb]i've tried this and other manual techniques and always get the same message:

dpkg: status database area is locked by another process

any suggestions?[/QUOTE]

Make sure you only running one incident of apt-get

---

### Post by frodon on 2005-11-15
Ok, i will look for other ways to do that because libc6 is a really important library, and uninstalling libc6 (before its upgrade) will delete a lot of packages.
I wonder why libdvdcss needs libc6 2.3.4-1 and not a previous version.

EDIT : you should post in the HOWTO, because there's there some users who follow this way without problems.

---

### Post by linewb on 2005-11-15
nevermind.  i think i know the problem with the above.  i've followed instructions for a breezy update when i'm running on hoary.  i'm thinking i've probably messed up several things and may just have to reinstall and start fresh.  there's nothing on the system right now i can't lose.  any reason i shouldn't?

---

### Post by frodon on 2005-11-16
If you just want to install breezy a simple update will work really well, here is how to do it : [https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28breezy%29](https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28breezy%29)

---

