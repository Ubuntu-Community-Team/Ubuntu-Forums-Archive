---
title: "Need Help Installing GnuCash"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Rbaldwin7 on 2007-08-28
Firstly:  I have looked around and read all installation posts and solutions for this program and nothing has helped me. I am very new to linux and have never installed a program.

Secondly:  I am using Ubuntu 6.06 LTS.  I have an AMD Athlon Duel core 64 bit processor. ( if that matters ? )

Third and last:  My problem is that I cannot seem to install GnuCash.  I downloaded the stable version "gnucash-2.2.1.tar.gz" to my desktop.  

I've tried "sudo apt-get install gnucash" in the terminal ( logged in normal) but that returns an error:

> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gnucash

I checked "etc/apt/sources.list" but im not sure what I need to change? if anything?

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Well, that is all the information I could think to give at this point.
Any and all help or ideas would be greatly appreciated.
Thank you.

---

### Post by dptxp on 2007-08-28
It is in add/remove in Feisty Fawn (7.04). Just tick and click apply.
Do not know about LTS version.

---

### Post by bobbybobington on 2007-08-28
I think its not installing because you have the 64-bit OS. I would try posting your question in the [64-bit users forum]("http://ubuntuforums.org/forumdisplay.php?f=134"). They'll be able to help out a lot more there.

---

### Post by Seisen on 2007-08-28
You have to enable this repository
```
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
``` just remove the "#" from in front of the repository.
Then do ```
sudo apt-get update
```

---

### Post by Rbaldwin7 on 2007-08-28
after enabling the repository and updating, as you said to Seisen, I used "sudo apt-get install gnucash" which worked.  I then typed "gnucash" into the terminal and it started up.  Thank you so much.  It was a good learning experience.

One thing, I don't understand what enabling the dapper universe was for?  Or what the dapper universe does. Any link to something valueable a person like me could read would be great.  Also there isn't a shortcut or any other way to start this program besides typing it in the terminal.

---

