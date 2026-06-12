---
title: "Using add/remove package downloads begin and then stop"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by DoubleR on 2007-05-13
Updated to Fiesty after installing Edgy a few months ago.  I have not made but a few changes to the original default install.

I have recently tried to install new applications using add/remove and synaptic.  For example I want to use Thunderbird as my email client. The download of the package begins and after about 5% of the file downloads to the cache it stops followed by the can not fetch message.  I have no problem loading pages in a browser.  If I run a speed test (speakeasy) I have no trouble downloading or uploading a large files.

I think the problem did not existed before upgrading to Feisty.   When at Edgy the few applications I added I did so using the the terminal and sudo

I tried the following a few minutes ago with the same results.

sudo apt-get update
sudo aptitude install mozilla-thunderbird

The first time the cache went from 65% to 70% stopped and timed out

Oddly I ran it again and was successful. Thunderbird is installed.

Any thoughts on what to read or check to get to solve this is appreciated

---

### Post by x64Jimbo on 2007-05-13
Sounds like it may have been a temporary problem. Possibly a server overload or an ISP issue. Have you seen this happen again at all?

---

### Post by BHelts on 2007-05-13
Hello, I had a very similar problem.  Could you post your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```

and also you could try

```
sudo apt-get update --fix-missing
```

---

### Post by DoubleR on 2007-05-13
Thank you for the suggestions,

I was suspicious at first it was an ISP problem as there was a service interruption in the area.  It was repeatable all day Sat. and most of today even with other internet access dependent applications were working OK.  And now I can not get it to repeat.  So perhaps it was an random ISP problem

Here is my source list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
  

Again thanks for the  response
Ray

---

### Post by BHelts on 2007-05-14
Glad everything is working!

---

