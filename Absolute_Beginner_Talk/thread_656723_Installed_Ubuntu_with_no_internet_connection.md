---
title: "Installed Ubuntu with no internet connection"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by patrickaupperle on 2008-01-02
It said that it commented out a few lines somewhere:confused: is this a  problem?

---

### Post by overdrank on 2008-01-02
> **patrickaupperle said:**
> It said that it commented out a few lines somewhere:confused: is this a  problem?

HI and I believe that would be your repos list You can use this command ```
gksudo gedit /etc/apt/sources.list
```
Example
```
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
```
You can remove the # in front of the repos you wish to add. And if you don't have internet don't worry. Hope this helps and good luck!

---

### Post by Saint Angeles on 2008-01-02
or if editing your sources.list sounds scary, just open synaptic package manager from system->administration and goto settings->repositories and check the ones you want.

---

### Post by PeterJS on 2008-01-02
Yeah, it does that, it's dumb, and I seem to be spear heading a personal crusade against this as I always seem to turn up for these threads. The lines it commented out are the online software sources in /etc/apt/sources.list. If you open up the sources file with:
```

sudo gedit /etc/apt/sources.list

```
You should see a bunch of lines commented out with a # at the front of them. If you have an internet connection you can safely uncomment them by removing the #. Obliviously comments that are actual comments should have the # left in front of them.

---

### Post by patrickaupperle on 2008-01-02
ok thankyou it turns out ive already fixed that:KS

---

### Post by bindatype on 2008-01-02
Comment out the CD line at the top too--its annoying when it asks you to insert the CD when it should be parsing the online repos.

---

### Post by patrickaupperle on 2008-01-03
OK i did

---

