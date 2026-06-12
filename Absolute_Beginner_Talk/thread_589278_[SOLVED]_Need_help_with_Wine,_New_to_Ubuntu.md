---
title: "[SOLVED] Need help with Wine, New to Ubuntu"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by MikeBrown on 2007-10-24
i have a slight problem with installing wine, and I understand if this post is seen as annoying since I am a complete Ubuntu newbie (just installed less than 24 hours ago). No prior Linux experience, have been using windows all my computing life and got tired of that whole mess. 
Now that all of that is aside, here is my problem:
I want to install wine so that I can finally play the orange box, since I have owned that for going on two weeks and have not been able to use it. I somehow luckily stumbled my way through the terminal coding, and now wine shows up in the Synaptic package manager, but if i click to install wine, i get this: 
"
wine:
 Depends: binfmt-support (>=1.1.2) but it is not installable
 Depends: ia32-libs (>=1.6) but it is not installable
 Depends: lib32asound2 (>1.0.14) but it is not installable
 Depends: libc6-i386 (>=2.6-1) but it is not installable
"

If someone could please help me out, that would be great. I am VERY new to Linux and Ubuntu so please be gentle!

EDIT: AMD Athlon 64 3200+ Processor, 1 gig RAM

---

### Post by Partyboi2 on 2007-10-24
A easier way to install is to go to Applications -Add/remove Do a search for wine, then click on  Wine Windows Emulator, then Apply. :)

---

### Post by Maestro23 on 2007-10-24
Might need to enable Universe and Multiverse repositories.  Go to:

System>> Admin>> Software Sources

Check Universe and Multiverse.

Once that is done, try and install wine again again from the Repositories.

---

### Post by zolimoka on 2007-10-24
Check this out:

[http://wiki.winehq.org/WineOn64bit#head-eb4de1da767e6e648d77c004566a71d0307cb737](http://wiki.winehq.org/WineOn64bit#head-eb4de1da767e6e648d77c004566a71d0307cb737)

---

### Post by MikeBrown on 2007-10-24
Stupid question: is there not a Universe and Multiverse repository built for Gutsy? i think this may be possible since the OS is less than a week old. If this is so, then maybe I can stop searching for a while. None of the options work, and I have been to wiki.winehq.org but still come away confused as ever. I do appreciate the help from all though!

---

### Post by Maestro23 on 2007-10-24
> **MikeBrown said:**
> Stupid question: is there not a Universe and Multiverse repository built for Gutsy? i think this may be possible since the OS is less than a week old. If this is so, then maybe I can stop searching for a while. None of the options work, and I have been to wiki.winehq.org but still come away confused as ever. I do appreciate the help from all though!

Gutsy has all its repos.  There's a problem on your end.  In a termial, type the following and past the output here:

> cat /etc/apt/sources.list

---

### Post by MikeBrown on 2007-10-25
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main universe

---

### Post by MikeBrown on 2007-10-25
Update: I've tried to switch to a new server (instead of downloading updates from the Ubuntu main server, I switched it to the North America server). I also tried typing the "sudo apt-get install wine and got this message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support ia32-libs lib32asound2 lib32gcc1 lib32ncurses5 lib32stdc++6
  lib32z1 libc6-i386
Suggested packages:
  libasound2-plugins msttcorefonts
The following NEW packages will be installed:
  binfmt-support ia32-libs lib32asound2 lib32gcc1 lib32ncurses5 lib32stdc++6
  lib32z1 libc6-i386 wine
0 upgraded, 9 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
Need to get 0B/45.1MB of archives.
After unpacking 140MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up tzdata (2007h-0ubuntu0.7.10) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

I really don't know why I keep getting errors. I'm not going to give up on Ubuntu, but at this rate I won't be able to play the Orange Box unless I kick Ubuntu over to my laptop and go back to using just Windows on my main "box". I would like to just kick Windows to the curb, but this is getting kind of frustrating!

---

### Post by Partyboi2 on 2007-10-25
You could replace your /etc/apt/source.list with a new one
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
Or
Press ALT+F2 ant into open dialog type gksudo gedit /etc/sources.list
Then try to remove the # sign on the repos lines marked with #  "because it failed to verify" then retry to update and upgrade.

eg.  # deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
          deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
So remove the #
Then save it.

---

### Post by MikeBrown on 2007-10-25
Ok, tried both processes, and i have the generated source file. I have tried copy and pasting the generated source into the file, but it says that i cannot save the read only file. also i have tried to do the alt + F2 option which only brings up a blank file! I have very little knowledge about command prompts in linux, so i am basically learning this all as i go, with unsuccessful results so far.

---

### Post by Partyboi2 on 2007-10-25
opps there was a typo in my last post.
try alt+F2 then type gksudo gedit /etc/apt/sources.list

Yes you can overide the current source.list but you might want to back up your old source.list 
```
 sudo cp /etc/apt/sources.list file /home/<your-username>/sources.backup 
```

---

### Post by MikeBrown on 2007-10-25
[This]("http://wiki.winehq.org/WineOn64bit#head-eb4de1da767e6e648d77c004566a71d0307cb737") seemed to work until it returned this message: 
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can you help me make sense of this?

---

### Post by moffa on 2007-10-25
> **MikeBrown said:**
> [This]("http://wiki.winehq.org/WineOn64bit#head-eb4de1da767e6e648d77c004566a71d0307cb737") seemed to work until it returned this message: 
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can you help me make sense of this?

When you were installing tzdata an error occurred.  The are several ways you can try to fix it.  Try
```
 sudo apt-get install -f 
```
and/or
```
 sudo dpkg --configure -a 
```

---

### Post by MikeBrown on 2007-10-25
both options returned the following:

"Errors were encountered while processing:
 tzdata"

---

### Post by Partyboi2 on 2007-10-25
you could try changing time zones <System> <Administration> <Time and Date> 
From what I have read people that have had problems with tzdata have changed there time zone then
```
sudo apt-get install -f 
```

---

### Post by MikeBrown on 2007-10-25
thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you !!!!!!!!! Finally it's working! My "updates" from the main bar finally told me my system was up to date, and wine and the wine-dev are under the "installed" tab in the synaptic package manager! Hopefully now everything will start working! Thanks again, your help was much appreciated!

---

### Post by Partyboi2 on 2007-10-26
Awesome! \\:D/

---

