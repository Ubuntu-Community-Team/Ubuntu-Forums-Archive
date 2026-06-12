---
title: "Problem installing Kile"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by cledezma on 2006-04-13
I installed Ubuntu about one week ago in my notebook, and today tried to install kile following the instructions that are in the HowTo section. I downloaded and installed TexLive 2005 without problems. My problem, is that when I try to install kile (i.e. when I type sudo apt-get install kile) I get the following message:

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kile: Depends: kdelibs4c2 (>= 4:3.4.1) but it is not installable
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installable
        Depends: konsole but it is not installable
        Depends: tetex-bin but it is not installable
E: Broken packages

Any ideas of why this is happening? Thanks in advance for your help.

---

### Post by gingermark on 2006-04-13
I think this is a problem with your sources.list (located in /etc/apt),
If you could post it here then we should be able to help further.

---

### Post by cledezma on 2006-04-13
Hi gingermark, and thanks for your reply. Belowe I copied what I have in sources.list. I appreciate your help on this.

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

---

### Post by gingermark on 2006-04-14
Ok, remove all the '#'s before the lines that start with the word "deb".
Save the file, then in your terminal type "sudo apt-get update".

Basically a '#' symbol before a line ensures that line is ignored - great for the comments, not so good for repositories we want to use. "sudo apt-get update" then reloads these "new" repositories so we can use them.

Now try "sudo apt-get install kile" again. It should work, but post if you have any other problems.

And now if you run Synaptic Package Manager (and reload the repositories there if you have to) you can now search though a lot of software that is easily installable. And you can upgrade to get security fixes too!

---

### Post by cledezma on 2006-04-14
It worked!!! ... thank you very much for all your help.

---

