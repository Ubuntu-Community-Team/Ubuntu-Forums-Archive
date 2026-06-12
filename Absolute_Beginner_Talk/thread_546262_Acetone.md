---
title: "Acetone"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by johnnyw on 2007-09-08
heres my problem
[http://ubuntuforums.org/showpost.php?p=3332063&postcount=20](http://ubuntuforums.org/showpost.php?p=3332063&postcount=20)

---

### Post by diatribe on 2007-09-08
that post tells absolutely nothing, and why would you create a post to link to another

---

### Post by johnnyw on 2007-09-08
It seems you dont want to help..if help is not your will please dont post in my thread..

thx

---

### Post by schorsch on 2007-09-08
As diatribe mentioned: There are no infos in your post what you want to do and what you did to get these error message so we are not able to help to you.

---

### Post by johnnyw on 2007-09-09
this is the error I get

> acetoneiso2: symbol lookup error: acetoneiso2: undefined symbol: _ZN12QApplicationC1ERiPPci

---

### Post by bulletxt on 2007-09-09
AcetoneISO2 uses QT4. If you are getting errors on that the only thing you can do is :


-install libqt4-dev
-download AcetoneISO2 1.0.2 sources [here]("http://downloads.sourceforge.net/acetoneiso2/AcetoneISO2-1.0.2r-generic-src.tar.gz?use_mirror=heanet") uncompress,
enter src dir and compile:
qmake-qt4
make
Then replace /usr/bin/acetoneiso2 with the new acetoneiso2 file in src directory.

NOTE: if you get an error when doing qmake-qt4, simply type qmake.

this should make it go.

---

### Post by johnnyw on 2007-09-09
how about this?

> libqt4-dev:
 Depends: libmng-dev but it is not going to be installed
 Depends: libpng12-0-dev
 Depends: libjpeg62-dev but it is not going to be installed
 Depends: zlib1g-dev but it is not going to be installed
 Depends: libfreetype6-dev but it is not going to be installed
 Depends: xlibmesa-gl-dev  but it is not installable or
	libgl-dev
 Depends: libglu1-xorg-dev  but it is not installable or
 	libglu1-mesa-dev but it is not going to be installed or
	libglu-dev
 Depends: libxft-dev but it is not going to be installed

---

### Post by bulletxt on 2007-09-09
ok so you are a totally newbie :D

it's not a problem.

open Synaptic and install all those packages. it's very simple.

---

### Post by johnnyw on 2007-09-09
yep, thats why I post here.. and actually that results posted before were the ones that the synaptic itself gave me :S

EDIT: all the list above says in synaptic it cant be installed as it depends on other libs :S :S.. is there any solution=??????

---

### Post by bulletxt on 2007-09-10
well there is quite of a mess in your system then.

I suggest you to check your repository file maybe you changed it and made this mess.

this is mine of Ubuntu Feisty 32 bit. change it with yours in /etc/apt/sources.list

after saving, open synaptic and click on "reload" button" . also be sure under options packages that all repo are activated.

here we go:

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) feisty main restricted 
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) feisty main restricted
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) feisty-updates main restricted 
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) feisty universe 
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) feisty universe
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) feisty multiverse 
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) feisty multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse 
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security main restricted 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security universe 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security multiverse 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security multiverse 
deb [http://kubuntu.org/packages/kde-357](http://kubuntu.org/packages/kde-357) feisty main

This should help, if it doesn't please ask someone else on another topic because here the problem isn't AcetoneISO2 but it's your system ;)

---

### Post by johnnyw on 2007-09-10
I aint have fesity, I have dapper.... how can I modify my sources.list ?? it does not allow me to save  

i wont create a new thread as this is my thread.. if it off topic whoever does not like it, just dont watch it..

---

### Post by chessercizes on 2007-09-10
hey.
if i understand your problem, make sure you are editing the file as root.

```
sudo gedit /etc/apt/sources.list
```

---

### Post by johnnyw on 2007-09-11
I have about 200 MB  in updates.and my connection gets ****** up every hour or so.. so I have to start downloading again.. is there any other solution ?????

 I think the guy bullettxt gave me the updates for feisty and I aint got feisty.. is that a problem??

---

### Post by johnnyw on 2007-09-11
can someone help me please?? I am stuck with this :S

---

### Post by Terl on 2007-09-11
Well, look below for why folks may not bve rushing to help.  You have bitten the folks that tried to assist.

> **johnnyw said:**
> I aint have fesity, I have dapper.... how can I modify my sources.list ?? it does not allow me to save  

i wont create a new thread as this is my thread.. if it off topic whoever does not like it, just dont watch it..

Anyway, what is it exactly you are trying to do?  It seems as if you tried to download something and received an error.  Is this the problem?

If you have updates you may have to do those first.  I would.  If you cannot get them all at once, deselect some and get the rest after the first finish.

Does your ISP log you off if it thinks you are inactive?  Or is there some other reason you said:  > my connection gets ****** up every hour or so

---

### Post by johnnyw on 2007-09-11
sorry..I think I acted wrong :S. sorry guys.. I think my precarious English makes me mad with myself as i feel I cannot express my troubles fully and I am completely stuck :S

I have just replace my sources.lists with the one provided by bullet, so as to be able to run acetone properly. The fact is that I have dapper drake and he has feisty and I have now about 200 MB in downloads and my connection cripples every one hour so I canr finish to download them fully :S


My ISP those not monitor/filter anything at all. i live in a 3rd world country. apart from having a crappy ISP I think I should update my D link router as It freezes lots of times a day. I used to do the way you say: select a couple of updates and update like this many times until I have em all installed. But do not know why when i do so I just starts downloading all the bunch of em.

Thx

J

---

### Post by 3rr0r on 2007-09-11
why don't you tell us what distro you are using???  That would make a lot more sense.  WHy don't you post your repo list for us?

---

### Post by johnnyw on 2007-09-11
i am ussing dapper drake ( 6.06). I do not know what the repositories are..

are this of any help???

---

### Post by Terl on 2007-09-11
johnnyw:  Thanks for explaining everything a little better.  It helps a lot in us helping you.  

Run this:  ```
sudo gedit /etc/apt/sources.list
``` and post the output here and we can tell you how to fix this.

---

### Post by johnnyw on 2007-09-11
this is my actual code.. i had a previous was that was supposed to be defective...all those update I have/can do in the update manager have appeared after I replaced the old with the new list


```
deb http://it.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ feisty main restricted
deb http://it.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb http://it.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://it.archive.ubuntu.com/ubuntu/ feisty universe
deb http://it.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ feisty multiverse
deb http://it.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ feisty-security main restricted
deb http://security.ubuntu.com/ubuntu/ feisty-security universe
deb-src http://security.ubuntu.com/ubuntu/ feisty-security universe
deb http://security.ubuntu.com/ubuntu/ feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu/ feisty-security multiverse
deb http://kubuntu.org/packages/kde-357 feisty main

```

cheers and thx

J

---

### Post by Terl on 2007-09-11
Run the command again.  When gedit opens go through each line and where it says feisty change it to dapper.  Save it and you should be all set.

Have you already tried updating using the Feisty files you just posted?  I am not certain but it could cause problems.

---

### Post by bulletxt on 2007-09-11
You can't do anything. You can't update Dapper to Feisty simply updating the repositories. The best solution is to download the full Ubuntu Feisty 7.04.

And another thing just to be clear, AcetoneISO2 won't work on Dapper because the new fuseiso depends on libfuse 2.6 and dapper has an older version. Don't even waiste time trying to update everything.


Download Ubuntu Feisty and everything will work.

---

### Post by johnnyw on 2007-09-11
I have feisty on a cd that canonical sent me :) :) .. is there any GUI app like norton image ghost ( very very easy to use) , so as to backup all my existing data to another hdd??

I am a stupid and dont know how to work with partitions :P

---

### Post by johnnyw on 2007-09-11
anybody would like to help me??
:KS

---

### Post by johnnyw on 2007-09-11
anyone willing to helP????

---

### Post by bulletxt on 2007-09-13
there are different tools to make a backupg of hard disk and most of them are in synaptic.

if your goal is to just do a copy of files and not the hard disk structure make a tar arcive (not gz) of the root folder you want to backup.

---

