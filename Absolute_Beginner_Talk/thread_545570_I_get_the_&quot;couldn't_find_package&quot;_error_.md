---
title: "I get the &quot;couldn't find package&quot; error in Terminal all the time"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by dmber on 2007-09-07
And I think it's from not having the right repositories.  So I go in to Synaptic/Settings/Repositories/Ubuntu 6.06 LTS (Source)/Add and add the multiverse and universe, but i have to do that every time i open synaptic.  

why is that?  

is that affecting the "couldn't find package" error in the terminal?

i'm trying to install java 1.6 and i cannot figure out how.  i can't find it using synaptic and when i use "sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts" i get the error.

what's up with that?

thanks!

---

### Post by BrendanM on 2007-09-07
Try disabling the install CD as a repo. I've seen it look for packages on the CD instead of online for some reason. Obviously that won't work unless the CD is in the drive.

---

### Post by meborc on 2007-09-07
the synaptic is using a file /etc/apt/sources.list, so you can check out where is it looking for the packages...

in terminal
"gksudo gedit /etc/apt/sources.list &"

the gedit will open (after you insert password to the popup)

then put # infront of the line with cd, if it is not yet there... and remove # from lines starting with deb

then save/close...

in terminal
"sudo apt-get update"

and try to install again

---

### Post by dmber on 2007-09-07
well i tried to edit the sources.list so that i wouldn't have to enable the repositories every single time i tried to install something, but now i've screwed the up sources.list.  i didn't back it up.

does anyone have a copy of sources.list that i can just copy and paste into mine?

this seems ludicrous to me that i can't just click a button to always enable these two repositories?  why do i have to edit this stupid text file? 

really, it should not be this hard to install java.  this is so frustrating.

---

### Post by dmber on 2007-09-07
> **meborc said:**
> the synaptic is using a file /etc/apt/sources.list, so you can check out where is it looking for the packages...

in terminal
"gksudo gedit /etc/apt/sources.list &"

the gedit will open (after you insert password to the popup)

then put # infront of the line with cd, if it is not yet there... and remove # from lines starting with deb

then save/close...

in terminal
"sudo apt-get update"

and try to install again
i screwed up my sources.list file trying to do just that, since i don't know what debs and whatever are.  could you just post (or pm) me your sources.list text so i can copy it and paste it into mine?  i would really appreciate it.  if you wouldn't mind making it so the universe and multiverse repositories are always enable as well.

i really appreciate it.

---

### Post by meborc on 2007-09-07
go to [www.ubuntuguide.org](www.ubuntuguide.org) ... there is a section called "how to add extra repositories" ... there is a complete sources.list file there for feisty

EDIT: i'm using gibbon... so my sources.list will not help you

---

### Post by dmber on 2007-09-07
nevermind, i'm going to try to use this:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by dmber on 2007-09-07
i used source-o-matic and this is now my sources.list:

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse





after saving that, i tried install java again with the terminal and got the same "couldn't find package" error.  why is that?

---

### Post by p_quarles on 2007-09-07
What version of Ubuntu are you using?

---

### Post by o_fortuna on 2007-09-07
You might find it easier if you just fire up synaptic and do a name search for "jre" (without quotes). I'm not sure why you aren't seeing it. Be sure to type
```
sudo apt-get update
```
first.

Also, Ubuntu 7.04 (the latest version) makes these things (like adding repositories, and installing java) much easier. I would recommend using that version. In Feisty, all you have to do is install "ubuntu-restricted-extras" to install Java and Flash automatically.

---

### Post by dmber on 2007-09-07
why is this so hard?  seriously, i want to know.  there should be a check box to always enable these repositories.  i should not have to edit a text file.  i should not have to sudo anything.  this is ridiculous.  something that would take me less than a minute to do on either OS X or windows has now taken me more than 15 minutes and i am not any closer to getting java installed on ubuntu than i was when i started.  

i used source-o-matic to get me a sources.list file that would make it so i wouldn't have to enable multiverse and universe everytime and that did not work.  

to me, this is the number one reason ubuntu will never take off in the desktop market in its current iteration.  this is ridiculous.

/rant.

---

### Post by p_quarles on 2007-09-07
Yes, the package management software for Windows is certainly a lot better than APT.

:confused:

---

### Post by BrendanM on 2007-09-07
There is a checkbox. Open synaptic and go to "Repositories". Experienced Linux users have a bad habit of always telling people how to do things with the CLU because it's easier for them to just paste a list of commands into a forum window. The problem is that beginners aren't familiar/comfortable with the command line yet. I'd say 90% of the things you'll want to configure in Linux have a GUI available, but when you ask for help on a forum, you're often going to hear the CLI way.

---

### Post by o_fortuna on 2007-09-07
> **dmber said:**
> why is this so hard?  seriously, i want to know.  there should be a check box to always enable these repositories.  i should not have to edit a text file.  i should not have to sudo anything.  this is ridiculous.  something that would take me less than a minute to do on either OS X or windows has now taken me more than 15 minutes and i am not any closer to getting java installed on ubuntu than i was when i started.  

i used source-o-matic to get me a sources.list file that would make it so i wouldn't have to enable multiverse and universe everytime and that did not work.  

to me, this is the number one reason ubuntu will never take off in the desktop market in its current iteration.  this is ridiculous.

/rant.
Well, you aren't using the current iteration.... ubuntu 6.06 is a year and a half old. Like I said, in the latest version, those repositories are enabled, by default, and sun Java can be installed by opening Add/Remove and finding ubuntu-restricted-extras.

And again, you just need to update. [Java is there]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=jre&searchon=names&subword=1&version=dapper&release=all"), though it isn't the latest. You really should be using Ubuntu 7.04.

---

### Post by bapoumba on 2007-09-07
sun-java6-jre should be in the dapper-backports.

Edit:
[http://packages.ubuntu.com/dapper-backports/libs/sun-java6-jre]("http://packages.ubuntu.com/dapper-backports/libs/sun-java6-jre")

---

### Post by djchandler on 2007-09-07
If the guy's advice before mine didn't work, open Synaptic, got to Settings, Repositories, and then select the Third-Party Software tab. The tab could be just Add Repository. Or you could use Software Sources under Settings. Add
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
or 
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
or
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

depending on which version you are running. That should get your Java jivin', but I honestly don't remember how I did it under Dapper.
:guitar:
DJC

---

### Post by dmber on 2007-09-07
is there such a thing as an "upgrade" to 7.04 or do i have to do a fresh install?  the reason i ask is that i am currently running headless (VNC-ing in from my macbook) and i have no monitor/keyboard/mouse to use to reinstall.

i chose to go with 6.06 LTS because of the LTS.  i'm using a really old machine with a celeron processor, 512 RAm, etc, and i figured the older ubuntu would run better -- this is turning out to be an incorrect assumption, right?

should i just take the time to find a KVM i can use to reinstall 7.04?

thank you for being patient with me.

---

### Post by o_fortuna on 2007-09-07
512M ram should work fine with the most recent version, even on a Celeron. I don't know what other people's experiences are, but a newer version isn't necessarily (in fact, it probably isn't) any slower than the older version.

Also, you can upgrade, but it will take a very long time because you'll have to basically upgrade twice. To do it, run
```
gksudo update-manager -c
```
it should tell you that a new version (6.10) is available. The upgrade will take a long time, you'll have to restart, and when it's done, you should be able to open up update manager yet again and upgrade to 7.04.

Skipping versions (ie upgrading directly from 6.06 to 7.04) is possible but is not supported and definitely not recommended. If possible, a reinstall would be easier on bandwidth and would take significantly less time (two upgrades would probably take about an hour and a half to three hours, while a reinstall would take 30 minutes or so).

---

### Post by ORBiTrus on 2007-09-07
> **dmber said:**
> why is this so hard?  seriously, i want to know.  there should be a check box to always enable these repositories.  i should not have to edit a text file.  i should not have to sudo anything.  this is ridiculous.  something that would take me less than a minute to do on either OS X or windows has now taken me more than 15 minutes and i am not any closer to getting java installed on ubuntu than i was when i started.  

i used source-o-matic to get me a sources.list file that would make it so i wouldn't have to enable multiverse and universe everytime and that did not work.  

to me, this is the number one reason ubuntu will never take off in the desktop market in its current iteration.  this is ridiculous.

/rant.

It's that was because that's the Debian way.  Yippee-kay-yay.  Look, this is the way it is: no one gives a **** if Linux/Ubuntu "take off" (aka reach critical mass) on the desktop.  We just care about writing code and making it better.  Linux is the evolution of a pod - it really is evolution perfected; the good code survives, the bad code fails to reproduce.  Sometimes good code has no chance, but over time, an extremely complex and well-formed beast emerges.

And believe me, this is better than what used to be.  In 99% of cases, it's better than Windows.  Sure, everyone knows that Linux is not the model of a good commercial software platform base.  But that really can't be fixed right now.  And it propably never can be; none of the developers really wants it to be, and the model of open source encourages fragmentation and a moving target, thus it never can be.  See, if Linux is evolving, trying to stick commercial software on it is like a symbiote trying to evolve alongside the host at the same pace.  Well, most commercial symbiotes can't.  They haven't evolved far enough yet.

> **dmber said:**
> is there such a thing as an "upgrade" to 7.04 or do i have to do a fresh install?  the reason i ask is that i am currently running headless (VNC-ing in from my macbook) and i have no monitor/keyboard/mouse to use to reinstall.

i chose to go with 6.06 LTS because of the LTS.  i'm using a really old machine with a celeron processor, 512 RAm, etc, and i figured the older ubuntu would run better -- this is turning out to be an incorrect assumption, right?

should i just take the time to find a KVM i can use to reinstall 7.04?

thank you for being patient with me.

Hah!  You call that old?  That machine is a speed demon.  Ubuntu is just bloated.  My workstation for my current job is a Athlon XP 1600+ with 256MB RAM and a 6.4GB HDD.  It runs, concurrently, 10 file manager instances, 1 web browser with 30-40 tabs open, a 200MB MySQL database, Apache (6 processes), a word processor, a spreadsheet, 5+ instances of a text editor, a newsreader, a feed aggregator, and finally my email program.  And it STILL has 64MB free!

For the record, it's running GoboLinux with all-KDE apps.  The fast CPU is just so I can compile stuff...


But, more to the point, you are right.  6.06 is better on older computers.  You will find that 7.07 uses 256MB on a fresh boot.  That's a lot of RAM for not much running, but hey, it's the price of easy bluetooth et al.  Unfortunately, since, as mentioned above, Linux is an evolving organism, for a user without experience newer is better.  At least it's less than Vista.

---

### Post by dmber on 2007-09-08
> **o_fortuna said:**
> 512M ram should work fine with the most recent version, even on a Celeron. I don't know what other people's experiences are, but a newer version isn't necessarily (in fact, it probably isn't) any slower than the older version.

Also, you can upgrade, but it will take a very long time because you'll have to basically upgrade twice. To do it, run
```
gksudo update-manager -c
```
it should tell you that a new version (6.10) is available. The upgrade will take a long time, you'll have to restart, and when it's done, you should be able to open up update manager yet again and upgrade to 7.04.

Skipping versions (ie upgrading directly from 6.06 to 7.04) is possible but is not supported and definitely not recommended. If possible, a reinstall would be easier on bandwidth and would take significantly less time (two upgrades would probably take about an hour and a half to three hours, while a reinstall would take 30 minutes or so).
will my "preferences" such as remote desktop and user auto-login stay?  i ask because if they don't i won't be able to access ubuntu (i have no monitor, keyboard, or mouse)

if the preferences stay, i will just update as long as the only difference is that it takes longer (i've got all weekend).

thanks again.

---

### Post by o_fortuna on 2007-09-08
> **dmber said:**
> will my "preferences" such as remote desktop and user auto-login stay?  i ask because if they don't i won't be able to access ubuntu (i have no monitor, keyboard, or mouse)

if the preferences stay, i will just update as long as the only difference is that it takes longer (i've got all weekend).

thanks again.
Updating won't delete any preferences. There may be some times when it says that some package distributes and "updated version" of a config file. You may want to ignore those; other than that, upgrades won't touch your settings.

---

