---
title: "Java 6 wont install?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-05-26
Hey guys! i've been using ubuntu for around a week now and it's amazing, but i cannot download the latest version of java. I went to their website, saw the options for linux, tried each one, but none worked. I keep getting an error message

[[IMG]http://images6.pictiger.com/thumbs/49/b4c497078a4207701de35ee6093b5949.th.png[/IMG]](http://server6.pictiger.com/img/175403/picture-hosting/-home-mykola-desktop-screenshot-.php)

What's going on?

---

### Post by taurus on 2007-05-26
Which release are you running?

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Tyke91 on 2007-05-26
I'm running Feisty ubuntu, to be honest, i have no clue what kind of java i need. im downloading from this website


[http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80)

---

### Post by taurus on 2007-05-26
Why do it the hard way when the latest java, 1.6, is available from the repos?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font
java -version
```

---

### Post by Tyke91 on 2007-05-26
lol! thanks m8

I guess i was put off when i saw 1.6, i thought that the latest version was 6 ;)

---

### Post by taurus on 2007-05-26
java5 = java 1.5
java6 = java 1.6

You can search for Sun java from synaptic or Add/Remove.

---

### Post by Tyke91 on 2007-05-26
btw - thx for the amazing response time

8 mins and the problem's solved :D

---

### Post by jasond123 on 2007-05-27
The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc which is a virtual package.
  sun-java6-jre: Depends: java-common (>= 0.24) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

i get this error. please help

---

### Post by taurus on 2007-05-27
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by jasond123 on 2007-05-27
sure, here it is

dino@Aeon:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
dino@Aeon:~$

---

### Post by taurus on 2007-05-27
Try to run these two commands again from a terminal.

```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font
```

---

### Post by arvevans on 2007-05-27
Thanks for the info.  That solved my Java problems as well.

Arv
_._


[I]
> **taurus said:**
> Why do it the hard way when the latest java, 1.6, is available from the repos?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font
java -version
```

[/I]

---

### Post by jasond123 on 2007-05-27
Sorry, tried it but same error as berfore.

---

### Post by Tyke91 on 2007-05-28
I'm also getting the same error... it turns out that that command only updated me to java 4?

---

