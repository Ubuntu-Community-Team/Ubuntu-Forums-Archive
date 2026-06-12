---
title: "Huge 'eb-src' problem!!!!!!!"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by bandeiram on 2007-05-13
Hey there everyone... Brand new to Ubuntu 6.06 Dapper Drake and to the entrire Linux OS, and already screwing it up... argh... :)

**My panel is displaying the following message:**

An error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was: 'Error Opening the cache (E:Type 'eb-src' is not known on line 40 in source list /etc/apt/source.list, E: The list of sources could not be read.)'

**Symptoms:**

- Firefox won't load any pages even though the internet will connect with 'pon dsl-provider';
- Synaptic Package Manager won't load - it gives the following message:
                     "Go to the repository dialog to correct the problem"
- Add/Remove won't load - it gives the following message:
                     *"Failed to check for installed and available applications*
                     This is a major failure of your software management system. Check the file permissions and
                     correctness of the '/etc/apt/sources.list' and reload the software information: 'sudo apt-get
                     update'."

**Line 40 in Source List reads...**
                     eb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free

I tried to open the source list and delete this line, however, under the Permission tag inside the right-click menu Properties of the sources.list is reads:
                     "You're not the owner, so you can't change these permissions."

**I imagine I'm getting these problems because earlier today I was trying to make *.avi files run in this OS (which by the way I failed terribly at).**

I hope to hear from someone soon, before I smash my computer on my head:lolflag: 

Cheers everyone, and thank you in advance!!!!

---

### Post by bonzodog on 2007-05-13
You need to edit your sources list as root, so use
```
sudo gedit /etc/apt/sources.list
```

In dapper, there should be no references to breezy at all.

just delete any lines that mention it completely.

Then Post your sources.list here and we will tell you if it's correct.

---

### Post by bandeiram on 2007-05-13
> **bonzodog said:**
> You need to edit your sources list as root, so use
```
sudo gedit /etc/apt/sources.list
```

In dapper, there should be no references to breezy at all.

just delete any lines that mention it completely.

Then Post your sources.list here and we will tell you if it's correct.

Hey there Bonzodog!!! Thank you so much for your quick reply to my problems!!!

There is a list of my sources.list as requested:

BEGINNING...

deb-src [http://br.archive.ubuntu/](http://br.archive.ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that softyware in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that softyware in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe



deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

...END

I tried the code you gave me and it worked on most of the problems I was having (which were problably unrelated to the one I currently have).

I'm still not able to connect to my dsl-provider, I don't know why...

I posted a new thread on this... If you could help me that would be phenomenal...

---

