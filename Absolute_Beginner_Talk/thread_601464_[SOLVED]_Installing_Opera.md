---
title: "[SOLVED] Installing Opera"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Bheegerji on 2007-11-03
Just loaded Ubuntu 7.10 onto my system. I'd like to install Opera browser. 
I downloaded the .deb package from Opera site and double clicked on it. I get an error message like this

**[COLOR="Red"]Error: Dependency is not satisfiable: libqt3-mt[/COLOR]**

So, before posting to this forum I checked some to get a solution. Every post seemed to be quite complicated to me as I'm a newbie. There was one post which I could understand and it required me to type some the command sudo dpkg -i opera_9.24-20071015.6-shared-qt_en_i386.deb into Terminal sudo and then entered my password. I got the following error.

dpkg: error processing opera_9.24-20071015.6-shared-qt_en_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera_9.24-20071015.6-shared-qt_en_i386.deb

Again I searched in forum and [found one case]("http://ubuntuforums.org/showthread.php?t=131608") similar to mine. I moved the setup file to my Home folder and then entered the command again. This time I got another message.

Selecting previously deselected package opera.
(Reading database ... 88932 files and directories currently installed.)
Unpacking opera (from opera_9.24-20071015.6-shared-qt_en_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3-mt (>= 3.3.4); however:
  Package libqt3-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera


Please help me install Opera.

---

### Post by SOULRiDER on 2007-11-03
Do this:
```
sudo aptitude remove opera
sudo aptitude install libqt3-mt
```

And then install opera like you had done before.

Good luck!!

---

### Post by PmDematagoda on 2007-11-03
Try:-

```
sudo apt-get install libqt3-mt
```

and try installing Opera again.

---

### Post by Iceni on 2007-11-03
Simply install the libqt3-mt package - go terminal:

```
sudo apt-get install libqt3-mt
```

Then install opera either via the terminal-based "dpkg" or just click it in gnome.

---

### Post by Maestro23 on 2007-11-03
> **Bheegerji said:**
> Just loaded Ubuntu 7.10 onto my system. I'd like to install Opera browser. 
I downloaded the .deb package from Opera site and double clicked on it. I get an error message like this

**[COLOR="Red"]Error: Dependency is not satisfiable: libqt3-mt[/COLOR]**

So, before posting to this forum I checked some to get a solution. Every post seemed to be quite complicated to me as I'm a newbie. There was one post which I could understand and it required me to type some the command sudo dpkg -i opera_9.24-20071015.6-shared-qt_en_i386.deb into Terminal sudo and then entered my password. I got the following error.

dpkg: error processing opera_9.24-20071015.6-shared-qt_en_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera_9.24-20071015.6-shared-qt_en_i386.deb

Again I searched in forum and [found one case]("http://ubuntuforums.org/showthread.php?t=131608") similar to mine. I moved the setup file to my Home folder and then entered the command again. This time I got another message.

Selecting previously deselected package opera.
(Reading database ... 88932 files and directories currently installed.)
Unpacking opera (from opera_9.24-20071015.6-shared-qt_en_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3-mt (>= 3.3.4); however:
  Package libqt3-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera


Please help me install Opera.

1st: Install libqt3-mt

> sudo apt-get install libqt3-mt

2nd: Install your opera .deb:

> sudo dpgk -i packagename.deb

---

### Post by taurus on 2007-11-03
You can get opera from the repos.  Make sure you have included all of them.

System -> Administration -> Synaptic Package Manager -> Settings -> Repositories

Make sure you have a check mark on all of them in Ubuntu Software & Third-Party Software.  Then, Close it and click Reload.  Now, Search for opera again.

---

### Post by PmDematagoda on 2007-11-03
5 posts in a time span of 3 minutes, very nice:D. And all having the same concept.:)

---

### Post by Maestro23 on 2007-11-03
> **PmDematagoda said:**
> 5 posts in a time span of 3 minutes, very nice:D. And all having the same concept.:)

Rain down info on the heads of the new people. :guitar:

---

### Post by PmDematagoda on 2007-11-03
> **Maestro23 said:**
> Rain down info on the heads of the new people. :guitar:

It's raining posts right now:D.

---

### Post by SunnyRabbiera on 2007-11-03
usually with gdebi the dependency is resolved... but its an easy fix in any case.

---

### Post by SOULRiDER on 2007-11-03
Yup!
I think the version fromt he Opera site might be more updated, besides they also have deb packages for the betas.

---

### Post by PmDematagoda on 2007-11-03
Yes, but you are most likely to stay updated if you use repos instead of downloading and installing the .deb from the site.

---

### Post by Bheegerji on 2007-11-03
Installed Opera. 

Thanks for the rain of posts.

---

### Post by PmDematagoda on 2007-11-03
> **Bheegerji said:**
> 

Thanks for the rain of posts.

Well, it is getting close to winter.;)

---

### Post by tparkin on 2008-03-02
> **taurus said:**
> You can get opera from the repos.  Make sure you have included all of them.

System -> Administration -> Synaptic Package Manager -> Settings -> Repositories

Make sure you have a check mark on all of them in Ubuntu Software & Third-Party Software.  Then, Close it and click Reload.  Now, Search for opera again.

I registered just to thank you.  Your solution helped me get Opera installed.  Thanks!

---

### Post by flipp_ok on 2008-03-09
> **tparkin said:**
> I registered just to thank you.  Your solution helped me get Opera installed.  Thanks!


I also registered to say thanks. I had tried other options I had found through online searches but none of them worked. I didn't get any useful results last night so I filed this bug report: [https://bugs.launchpad.net/ubuntu/+bug/200030](https://bugs.launchpad.net/ubuntu/+bug/200030) Now I no longer need help. Installing from the repositories did the trick. It is so nice to have the browser I am most familiar with available while using Ubuntu.  So once again a Ubuntu noob says Thanks!

---

