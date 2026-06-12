---
title: "Duplicate Source list error"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-17
Keep getting this duplicate source list error. I tried /etc/apt/sources.list but get a "permission denied" message. Anyone know how to fix this? Thanks.

---

### Post by NeoLithium on 2007-04-17
In a terminal window, can you type:
```

cat /etc/apt/sources.list

```
And paste the results?

---

### Post by jacatone on 2007-04-17
Don't understand? Paste the results. Paste them where? It's a rather long list.

---

### Post by jfinkels on 2007-04-17
> **jacatone said:**
> Don't understand? Paste the results. Paste them where? It's a rather long list.

Copy and paste them here, to the forums! Then we can tell you what to do.

---

### Post by Static-X on 2007-04-22
Hi guys... I was getting that error... look... thank you.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted main multiverse #Added by software-properties
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse #Added by software-properties

#AUTOMATIX REPOS START

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-security restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-security restricted main #Added by software-properties

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted #Added by software-properties


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-security main

#AUTOMATIX REPOS END
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

---

### Post by Static-X on 2007-04-22
Jacatone... sorry dude for use this post....

---

### Post by DSn0wMan on 2007-04-22
It looks like automatix put some duplicate entries in your sources.list

---

### Post by Ferrat on 2007-04-22
I'm having the exact same problem, tried reseting my source.list to the basic one, but I don't think that's the problem, I got the [UPDATE DIST] button before in my Update manager but not now, All I can see is a Opera update that isn't selectable

Edit:
messed around abit and well seems that the acrives isn't reachable :(

---

### Post by Static-X on 2007-04-23
Thank's  DSn0wMan... I fixed... right now i'll fix my wi-fi. :)

---

