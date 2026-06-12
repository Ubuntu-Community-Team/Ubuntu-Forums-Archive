---
title: "Problem(s) with Linux Lite and Firefox 31.0"
date: 2014-08-06
forum: Any Other OS
---

### Post by cobradabest on 2014-08-06
I'm having a few issues with Linux Lite, I am new to Linux, but wanted to give it a try beecause I heard the lightweight Linux distros can "revive" old PCs, lke the laptop I'm currently using. and that linux lite was made fr beginners, so I tried it, and I love it! It's **far** faster than Windows 7, and more stable! However I have a few issues with it right now, but this is the only forum I could find that covers Linux/Ubuntu issues, so I decided to try for a fix in the off topic forums. I think linux L:ite is a deriverative of Ubuntu anyway (All programs and (to an extent) solutions for Ubuntu that I've tried worked on Linux lite) so I think I'm okay, but I'm playhing it safe.

Anyway, the first, and most important issue I've been having is the keyboard layout, since I live in Scotland, and we use the English UK keyboard layout, but the default for Linux lite is US, so I change it to UK, but whenever I reboot it, it revert back, and when I got to options to change it back, it says it's set to UK... So how do I fix it? How do I make the change perminent?

Also, when I use Firefox and try to watch Youtube videos it runs fine at 360p and 480p, but when I try to watch a video in HD, it slows right down, and constantly skips to try and catch up with the audio (which works fine, by the way).

I've been looking around the web for solutions to these problems, and Both problems seem to be common for Ubuntu OSes, and since Linux Lite is derived from Ubuntu, I thought that makes sense. Some programs Ubuntu has doesn't appear on Lite, but all the terminal commands I've tried have been recognised no problem, so it might be better to use Terminal solutions.

So what do I do to fix these problems?

---

### Post by ibjsb4 on 2014-08-07
A quick search tells me that LinuxLite is xfce, which in ubuntu language is Xubuntu.  So for your keyboard, this may work:

[http://askubuntu.com/questions/471849/change-keyboard-layout-permanently-in-xubuntu-14-04](http://askubuntu.com/questions/471849/change-keyboard-layout-permanently-in-xubuntu-14-04)

more hits here

[https://www.google.com/search?client=ubuntu&channel=fs&q=Change+keyboard+layout+permanently+in+Xubuntu&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=Change+keyboard+layout+permanently+in+Xubuntu&ie=utf-8&oe=utf-8)

For your video, go to the manufacture site and see if any linux drivers are available.

Good luck :)

---

### Post by cobradabest on 2014-08-10
> **ibjsb4 said:**
> A quick search tells me that LinuxLite is xfce, which in ubuntu language is Xubuntu.  So for your keyboard, this may work:

[http://askubuntu.com/questions/471849/change-keyboard-layout-permanently-in-xubuntu-14-04](http://askubuntu.com/questions/471849/change-keyboard-layout-permanently-in-xubuntu-14-04)
Okay, I managed to do method 1 and I haven't got any errors and everything seemed to do what it was supposed to, but I'll have to reboot to see if it did anything, I'll get back to you next time I turn off and turn my PC back on.

EDIT: It worked! Thanks! That's one problem solved!

> **ibjsb4 said:**
> For your video, go to the manufacture site and see if any linux drivers are available.

Good luck :)
Okay, I have an AMD E-300, but there doesn't seem to be any Linux drivers for it... So what do I do now? Is there anything I can do?

EDIT: This is another question/issue entirely, but I'm having a big problem right now, whenever I try to run system update or "Install/Remove Software" (or whatever the Ubuntu/Xubuntu equivalent is), I get this error:

"E: Type 'deb-src-src' is not known on line 75 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."

How do I fix it?

---

### Post by ibjsb4 on 2014-08-10
> "E: Type 'deb-src-src' is not known on line 75 in source list /etc/apt/sources.list

Ok, something is wrong with the sources list.  No big deal in *buntu, but your running something different.

You got a screen that looks something like this?
[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)
Just uncheck sources list, that should solved the problem.

I would really consider moving over to a *buntu distro to get better support.

---

### Post by cobradabest on 2014-08-10
> **ibjsb4 said:**
> Ok, something is wrong with the sources list.  No big deal in *buntu, but your running something different.

You got a screen that looks something like this?
[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

Just uncheck sources list, that should solved the problem.

Nope, I'm not getting that. where would I get that to that window/screen or the Xubuntu equivalent? Sorry, I'm new to Linux/Ubuntu. 

I'm going to assume that I have to go through my OS's program manager, which in this case I think is the "Synaptic Package Manager". When I access that, I get the exact same error!

[IMG]https://photos-5.dropbox.com/t/0/AAAVZIj8P2x5rcvG1LxOKLYAqnHSDpLdKjAhnhJFIpTL-Q/12/139373329/png/32x32/3/_/1/2/Screenshot%20-%2008102014%20-%2008%3A08%3A45%20PM.png/u3FErw00Le1Blw-gy2WrplbuTx0PhqfyuYjxGIGWYME?size=800x600[/IMG]

> **ibjsb4 said:**
> I would really consider moving over to a *buntu distro to get better support.
Yeah, you're probably right, but I'm using Linux Lite for now because it's a lightweight OS. I'm using an old laptop right now, and Windows 7 on it is very slow and crashes a lot, Linux Lite is much faster and it has yet to crash on me! (I hope I don't jynx that...) It's also supposedly designed for those moving from Windows to Linux for the first time. 

I'm considering using another Ubuntu Distro when I build a new PC, but until then, I'm sticking with Linux Lite. I would imagine since it's based on Xubuntu LTS, I think fixes for Xubuntu can be used with LL, so I imagine I could in theory get as much support as if I used an official distro.

---

### Post by ibjsb4 on 2014-08-11
That screen is located in synaptic pm.  Go to the synaptic tool bar and Settings>Repositories.  Then like I said, uncheck Source Code and then reload.  If synaptic will not let you do this, then it will be necessary to manually edit your sources list.  So in this case, please post the output of this command (from the terminal).
```
cat /etc/apt/sources.list
```

---

### Post by cobradabest on 2014-08-11
Okay, here:
```
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner

## Linux Lite Repository
deb [http://repo.linuxliteos.com/linuxlite/](http://repo.linuxliteos.com/linuxlite/) beryl main
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb-src-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
# deb-src-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
# deb-src-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner

## Linux Lite Repository
deb-src [http://repo.linuxliteos.com/linuxlite/](http://repo.linuxliteos.com/linuxlite/) beryl main
```

---

### Post by ibjsb4 on 2014-08-11
You need to open up your text editor and comment out (#) all lines that start with

deb-src-src

example

#deb-src-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted 

Terminal code to open up your text editor:
```
gksudo **nameoftexteditor** /etc/apt/sources.list
```
Where nameoftexteditor is whatever one linuxlite comes with.

But first, lets make a backup:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```

And then update after you edit:
```
sudo apt-get update
```

---

### Post by cobradabest on 2014-08-11
It works! Thank you so much!

I have one more minor issue, if that's okay. I downloaded ePSXe 1.9.0 (PS1 Emulator) for Linux,, but nothing happens when I click on the executable, nothing happens. I've had a look around online, and this seems to be a common issue for Xubuntu, but I didn't find any solutions. Do you know how I can get it working?

---

### Post by ibjsb4 on 2014-08-11
> **cobradabest said:**
> It works! Thank you so much!

I have one more minor issue, if that's okay. I downloaded ePSXe (1.9.0) for Linux,, but nothing happens when I click on the executable, nothing happens. I've had a look around online, and this seems to be a common issue for Xubuntu, but I didn't find any solutions. Do you know how I can get it working?

Welcome :)

Give me your download link for this ePSXe.

---

### Post by cobradabest on 2014-08-11
Okay, here: [http://www.epsxe.com/download.php](http://www.epsxe.com/download.php)

---

### Post by ibjsb4 on 2014-08-11
Ok, I will load it up later today and play with it.  Later :)

---

### Post by ibjsb4 on 2014-08-12
Ok, I gave it a try and no luck, but I'm not a gammer.  Maybe start a new thread in Gamming, see if you can get some help there.

Good luck

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by cobradabest on 2014-08-12
Okay, thanks for all of your help!

---

