---
title: "apt-get can't istall java?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by mouser13 on 2006-08-30
I've enabled all binary sources in the /etc/apt/sources.list and I've run "sudo apt-get update", but still it gives me "could not find package" when I try to instal the java plugin.
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-plugin

```

---

### Post by WalmartSniperLX on 2006-08-30
Make sure you're connected to all the software channels. Goto System/Properties/Software Manager  and check all the check boxes/items and click close. Then click reload. 

Then try again :D  and tell me if it works

---

### Post by Darrious on 2006-08-30
The same thing is happening to me. I'd just go to there website and download it.  [Java]("http://www.java.com/en/download/index.jsp")

---

### Post by WalmartSniperLX on 2006-08-30
You could try searching java in symnaptic package manager (or whatever its called) and see if its even in the repos. I dont really know cuz i havnt installed java yet.

---

### Post by mouser13 on 2006-08-30
All binary ones were checked already (I did that just after the installation). I just ran software update and also reloaded the package list in the synaptic Package Manager, but still I can't find that package there and I can't install it with apt-get. Here is my sources.list:
```
# deb-src http://bg.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://bg.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# deb-src http://bg.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted
# deb-src http://bg.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://bg.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://bg.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://download.skype.com/linux/repos/debian/ stable non-free
```
Maybe I should try adding Debian sources? But the packages must be somewhere in the Ubuntu distro I think.

PS I already installed the package manually by downloading it from Sun's site, but I still want to know what is the problem. If there is one package missing, there must be something wrong and maybe other packages missing, too. So I want to solve that.

---

### Post by Sef on 2006-08-30
Uncomment the deb-src lines.

---

### Post by telegramsam on 2006-08-30
Automatix has a couple of Java apps...along with some other super cool and necessary apps.

[www.getautomatix.com](www.getautomatix.com)

Check it out--I think you'll like it!

---

### Post by skymt on 2006-08-30
Yes, it's in the repos (multiverse, to be specific), and it is called sun-java5-plugin. Make sure you have multiverse enabled.

---

### Post by nrwilk on 2006-08-30
> **mouser13 said:**
> Maybe I should try adding Debian sources? But the packages must be somewhere in the Ubuntu distro I think.

Do not add debian sources.  This is supposed to be very dangerous for an ubuntu system.

I promise, all the java packages are in ubuntu's repositories.

You need to enable the universe and multiverse repositories to get them.

What I usually just do is copy and paste a suggested source.list into my sources.list file.  Remember to backup first before you do this, though.  To backup your sources.list file, just issue this command:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
``` 
A link to a recomended sources.list thread, stickied in the repository forum:
[http://ubuntuforums.org/showthread.php?t=236425](http://ubuntuforums.org/showthread.php?t=236425)

You can always find a good suggested sources.list stickied in the [repository forum]("http://ubuntuforums.org/forumdisplay.php?f=41").  I've always used the one there, and it's always worked flawlessly for me.


Also: I suggest you do NOT use automatix.  Not because it isn't good at doing what it does.  it is.  I suggest you don't use it because if you really want to learn to use Linux, you should do these things yourself.  Esspecially things as simple as installing java.

you want sun-java5-jre and sun-java5-plugin.  If you want to write java programs, you also want sun-java5-jdk.

---

### Post by mouser13 on 2006-08-30
Thank you everybody! I enabled the multiverse and everything worked (I didn't know that they are disabled by default). Thank you again for your help!

---

