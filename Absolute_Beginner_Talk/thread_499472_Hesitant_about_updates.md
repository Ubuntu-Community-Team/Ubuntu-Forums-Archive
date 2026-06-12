---
title: "Hesitant about updates :/"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by Hickler on 2007-07-12
Well, the previous three times I have installed Ubuntu on my machine, I installed the updates right away. Those previous three times, I had problems like firefox just closing at different pages (ie. google worked fine, Ubuntuforums however, did not) and not starting up at all. Also some other programs like thunderbird did not work as well. I was wondering if the updates had anything to with this and as I've stated in the title, I am hesitant about installing the updates because the previous three times I've had to spend hours uninstalling and reinstalling Ubuntu. I just wanted to know your opinions.. Thank you.

---

### Post by bapoumba on 2007-07-12
Which flavor of ubuntu are you using?
Feisty up to date here :)

Could you paste your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by twiceasworn on 2007-07-12
I personally have never had an issue with the updates breaking things on my system.  The only thing I could really suggest is to make sure and read what you are installing before letting it do the update.  Sometimes there are things you do not need/want.

---

### Post by annda on 2007-07-12
in my experience, if you stick to a recent stable version - like edgy or even better feisty now - and ubuntu repositories, you will be fine. if you try automatix, envy or some other exotic repos, you might get unstable libraries, conflicts and whatnot...

---

### Post by twiceasworn on 2007-07-12
> **annda said:**
> in my experience, if you stick to a recent stable version - like edgy or even better feisty now - and ubuntu repositories, you will be fine. if you try automatix, envy or some other exotic repos, you might get unstable libraries, conflicts and whatnot...

Yes, I suppose I should have mentioned that.  When you go adding repositories and what not for packages things can get a little wacky.  Just stick to the ubuntu repos and you should be ok.  In the event that things do not go over smoothly, post the problem and we would be happy to try and solve it with you :)

---

### Post by Hickler on 2007-07-12
I'm using Feisty and here is the sources list.. I think...

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
seth@ubuntu:~$

---

### Post by bapoumba on 2007-07-12
You should be fine :)
(I have the same sources.list).

---

### Post by Hickler on 2007-07-12
Well, thank you very much, I'll look over the updates now and not install any I feel I don't need. Thank you for your support.

---

### Post by bapoumba on 2007-07-12
You're welcome.
Do not hesitate to ask if you have any question.

---

