---
title: "Opera"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by Duccio on 2006-10-24
Hi. I'm under Dapper, AMD64, Desktop, and for a number of reasons, included but not limited to having a 32bit browser to install Flash smoothly, I am trying to install Opera. I downloaded opera_9.02-20060919.6-shared-qt_en_i386.deb from [opera.com]("http://www.opera.com/") and installed the package with --force-architecture, but when I go to Applications -> Internet and select Opera, nothing happens: Opera doesn't open at all. Typing opera in the terminal returns:
```
duccio@duccio-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.02-20060919.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
```
Googling returned some similar threads/mails, but I couldn't fix the problem myself anyway: [the wiki](https://help.ubuntu.com/community/OperaBrowser) itself mentions the problem but it's kinda different, the workaround given is *correct the Java path under Tools -> Preferences -> Advanced Tab -> Content -> Java options* but I guess this has to be done into Opera, that doesn't load at all.

I searched for "libqt" into Synaptic but couldn't find anything named exactly "libqt-mt", there are several similar names and I already have installed libqt3-mt.

sudo apt-get -f install returns:
```
duccio@duccio-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Anybody have an idea of how I could solve this?

---

### Post by funkyade on 2006-10-24
Install Opera from the Ubuntu repositories not from the Opera site. You may need to enable multiverse and universe in your sources.list to do so...

A 32bit app needs a chroot setup for it to run under 64bit I think.

hth

---

### Post by DarkOx on 2006-10-24
You can fix the java thing from the command line. Open up a terminal, and type:

> sudo update-alternatives --config java

It should give you something like:

> 
Selection       Alternative
-----------------------------------------------
      1            /usr/bin/gij-wrapper-4.1
      2            /usr/lib/jvm/java-gcj/jre/bin/java
*     3            /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
 +    4            /usr/lib/j2se/1.4/bin/java

Press enter to keep the default[*], or type selection number:


Simply put in the number you want (probably something similar to /usr/lib/jvm/java-1.5.0-sun/jre/bin/java .) If an option like that doesn't appear it means that java isn't installed. You can install it by using the command:

> sudo aptitude install sun-java5-bin

Hope that helps.

---

### Post by Duccio on 2006-10-24
**DarkOx**: I only had /usr/bin/gij-wrapper-4.1 and /usr/lib/jvm/java-gcj/jre/bin/java, then I installed sun-java5-bin and switched to it (*Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.*), still opera returns the very same errors.

**funkyade**: I couldn't find Opera with Synaptic, here's my sources.list (I played with it the first day I used ubuntu so it might be messed up, at that time the cp command wasn't my friend...):
```
# deb-src http://it.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://it.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```
anyway the *deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse* and *deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse* lines are there and should be enough. Maybe the package isn't there because Opera isn't shipped for AMD64?

---

### Post by Sef on 2006-10-24
> Maybe the package isn't there because Opera isn't shipped for AMD64?

The only version of Opera for Linux i386 looks like it is 32 bit.

> # deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

Shouldn't you uncomment these, or is there a reason you haven't?

---

### Post by funkyade on 2006-10-24
I don't have AMD64 platform to confirm this on, but I know of several people who have installed 32bit apps using some kind of chroot system.

In essence you make an alternative environment to run the app in that is actually 32bit and utilises the 32bit mode of the 64bit CPU. I suggest googling or searching these forums for a lead on this...

You may have problems using sun java on AMD64 also as I don't think sun support AMD64 linux at the moment... you would be better off using GCJ or Blackdown.

hth

---

### Post by Duccio on 2006-10-25
> **Sef said:**
> The only version of Opera for Linux i386 looks like it is 32 bit.
```
# deb-src http://it.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
```
Shouldn't you uncomment these, or is there a reason you haven't?
No, well, I really didn't have much clue when editing it, I was trying to make [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) work but failed, I still can't figure out why, but my wildguess is that it is related to the architecture, as I tried any possible combination and added all the repositories but still got the *Couldn't find package* error message from apt-get. The reason I commented the deb-src is probably that [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine) said deb-src was useful for developers. Uncommenting it didn't help anyway, I still can't find Opera in the repositories.

**funkyade**: ok, I switched back to */usr/lib/jvm/java-gcj/jre/bin/java*, the problem is still there anyway. I've been giving a look to chroot, and apart that it sounds quite complicated and that I can't understand what really it is (some sort of virtual machine?) and how I should really use it to get Opera working ([http://ubuntuforums.org/showthread.php?t=24575]("http://ubuntuforums.org/showthread.php?t=24575") seems to tell me to install a old (hoary) ubuntu install?), I am now wondering if this AMD64 is worth the effort, under Windows x64 I could run both AMD64 and 32bit code without all of this hacking and I thought it would have been the same under Linux, but if I knew all this effort was needed just to open YouTube, I'd have probably choosen the i386... too bad there wasn't any warning on the download page about this...

---

### Post by tyufi on 2006-11-03
You should just use the i586 java. If you download it from [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) just select the jre with i586 ending. If you run this file from a terminal it will install java runtime into the actual directory and you can specify this directory as java home directory in the opera.
I think the point is that opera is 32 bit and cannot work together with 64 bit java.
But it is not really relevant as amd processors can run the 32 bit applications without problem...

---

