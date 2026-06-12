---
title: "Basic Installation"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by pichon on 2007-05-30
Hi I'm having problems with basic installations I don't know if my connection is restricting me or something but when I ping outside (google.com) I get an answer

I was trying to install java 6
```

apt-get install sun-java6-jdk sun-java6-jdk sun-java6-plugin sun-java6-bin

```
and I got:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-jdk

```

I've already checked and I have **multiverse** repository if I cat my **/etc/apt/source.list**  y get

```

## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb http://mx.archive.ubuntu.com/ubuntu/ feisty main restricted
#deb-src http://mx.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mx.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
#deb-src http://mx.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mx.archive.ubuntu.com/ubuntu/ feisty universe
#deb-src http://mx.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mx.archive.ubuntu.com/ubuntu/ feisty multiverse
#deb-src http://mx.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mx.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
#deb-src http://mx.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
#deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
#deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
#deb http://edevelop.org/pkg-e/ubuntu feisty e17
#deb http://e17.dunnewind.net/ubuntu feisty e17
#deb-src http://edevelop.org/pkg-e/ubuntu feisty e17

```

I also tryed with us and gb instead of mx for the ubuntu archive

I'll apreciate any suggestions

PME

---

### Post by starcraft.man on 2007-05-30
> **pichon said:**
> 

```

apt-get install sun-java6-jdk sun-java6-jdk sun-java6-plugin sun-java6-bin

```


I'm gonna take a wild guess here, but you put jdk twice.... so, lets try this command...

```
sudo aptitude install sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-fonts 
```

Also, you do know that jdk is the java development kit right? You only need that if you plan to make something for java... jre is the java runtime environment, thats what actually runs the apps. You can remove the jdk from the command if you don't need/want it.

That should do it, oh and I see your using Ubuntuguide's source list, good man :).

---

### Post by Warbo on 2007-05-30
I use aptitude rather than apt-get since it is interactive, so I can see exactly which packages are available (no typos :) )

---

### Post by starcraft.man on 2007-05-30
> **Warbo said:**
> I use aptitude rather than apt-get since it is interactive, so I can see exactly which packages are available (no typos :) )

I suppose pichon might not know the difference, here is a link to [explain the two for you.]("http://www.psychocats.net/ubuntu/aptitude")

That should be it, have fun with Java apps. I also use aptitude as was in my command :)

---

### Post by pichon on 2007-05-30
thanks for the help, so far I tried aptitude instead of apt-get but this is what I get

```

root@pichoWorkshopUbuntu:~# aptitude install sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "sun-java6-jre"
Couldn't find any package whose name or description matched "sun-java6-jdk"
Couldn't find any package whose name or description matched "sun-java6-plugin"
Couldn't find any package whose name or description matched "sun-java6-bin"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


```

and YES I do know that jdk is the develper kit, and I need it, I'm a Web-develper (J2EE) and plan to mount a tomcat5.5 server in this machine

---

### Post by starcraft.man on 2007-05-31
> **pichon said:**
> thanks for the help, so far I tried aptitude instead of apt-get but this is what I get

```

root@pichoWorkshopUbuntu:~# aptitude install sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "sun-java6-jre"
Couldn't find any package whose name or description matched "sun-java6-jdk"
Couldn't find any package whose name or description matched "sun-java6-plugin"
Couldn't find any package whose name or description matched "sun-java6-bin"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


```

and YES I do know that jdk is the develper kit, and I need it, I'm a Web-develper (J2EE) and plan to mount a tomcat5.5 server in this machine

Ok... thats really weird... post the output of this:

```
sudo aptitude search sun-java
```

and this command:

```
ping  mx.archive.ubuntu.com
```

Push ctrl + C after 5-6 lines of ping appear, then paste the output.

If both check out, thats really weird.... I of course will offer a suggestion, I think I know what might fix this if both check out.

---

### Post by pichon on 2007-05-31
Starcraft.man I have ping to mx.archive.ubuntu.com

If your suggestion was to run

```

aptitude update

```

you where RIGHT, rookie mistake, but after I ran that command and then **aptitude install sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-bin** I'm being able to download and install everything I need

Thank ALL of you guys for pitching in :p

---

