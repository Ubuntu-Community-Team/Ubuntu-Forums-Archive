---
title: "Firefox Crashes!"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by say592 on 2006-12-09
I dont have any extensions installed, and am using firefox just like it was when i installed ubuntu, why is it crashing when I go to certain pages, I know these pages are firefox compatable as I could use firefox on windows with the site.  How do I fix this!

---

### Post by taurus on 2006-12-09
Are you using Dapper or Edgy?  Do those sites happen to run flash or java applets?

---

### Post by say592 on 2006-12-09
I am using version 6.10 of ubuntu and yeah the sites run flash? How do I fix this, on windows I would intsall a plugin, can I go to that portion of the FF site, and install plugins?

---

### Post by taurus on 2006-12-09
Install automatix2 first.  Then use it to install all the plugins and codecs for your Edgy...

[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29)

---

### Post by say592 on 2006-12-09
> **taurus said:**
> Install automatix2 first.  Then use it to install all the plugins and codecs for your Edgy...

[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29)

It said app based error occured and installation was unable to continue on all of the apps!

---

### Post by taurus on 2006-12-09
What command did you run to get that error message?  In the meantime, can you paste your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by say592 on 2006-12-09
OK so here is what i got when i ran that code you posted:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END

---

### Post by taurus on 2006-12-09
Remove the # in front of these lines...

```

deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```
Save it and at the prompt, run

```
sudo aptitude update
sudo aptitude install automatix2
```

---

### Post by say592 on 2006-12-09
Complete n00b here, so I dont quite get it.........Simple step by step please ;) thanks

---

### Post by taurus on 2006-12-09
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Now, use the arrow keys to move around and remove the # in front of those lines.  Save it and run thise two commands to update the list and install automatix2.

---

### Post by useResa on 2006-12-09
I remember that this was reported before and maybe the solution as posted [here ](http://www.ubuntuforums.org/showthread.php?t=286069&highlight=firefox+crash) can solve your problem.

I know it did the trick for me (and I didn't even have to do the other two suggestions).

---

### Post by say592 on 2006-12-09
kk this is what I saw after I eddited that file closed the window, then ran those 2 codes you gave me:

Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by say592 on 2006-12-09
> **useResa said:**
> I remember that this was reported before and maybe the solution as posted [here ](http://www.ubuntuforums.org/showthread.php?t=286069&highlight=firefox+crash) can solve your problem.

I know it did the trick for me (and I didn't even have to do the other two suggestions).
Ok so I tried that, but the file is read only, so I cant eddit it.... How do I get passed that......

---

### Post by taurus on 2006-12-09
```
sudo dpkg --configure -a
```

---

### Post by useResa on 2006-12-09
> **say592 said:**
> Ok so I tried that, but the file is read only, so I cant eddit it.... How do I get passed that......
```
sudo gedit /etc/firefox/firefoxrc
```

---

### Post by say592 on 2006-12-10
Ok, so taurus when/where do I run that code? And I did that whole thing the other thread said to, eddited that file and such,  and it helped a few sites, but not all of them.

---

### Post by say592 on 2006-12-10
Never Mind! I dont think that the way taurus said ever actualy did install, but It isnt crashing! YAY!

---

### Post by useResa on 2006-12-10
> **say592 said:**
> Never Mind! I dont think that the way taurus said ever actualy did install, but It isnt crashing! YAY!
Regardless what actually did the trick, glad you got a non-crashing FF up and running.

---

