---
title: "Synaptic reload GPG error"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by danielsbrewer on 2007-10-24
Hello,

I keep getting the following error when reloading the repositories in Synaptic:

W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I have tried changing to the central repositories as suggested by some and then this goes away sometimes and then comes back.

Any idea why this happens on and off?  Can I fix it or is it a server problem?

---

### Post by habtish on 2007-10-24
Please post your apt sources list... ```
 vim /etc/apt/sources.list
```

---

### Post by danielsbrewer on 2007-10-25
Here you go:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security main restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security multiverse

# deb [http://www.sourcekeg.co.uk/cran/bin/linux/ubuntu](http://www.sourcekeg.co.uk/cran/bin/linux/ubuntu) gutsy/

---

### Post by habtish on 2007-10-25
It looks like you will need to add a GPG key for the last repo ```
 # deb [http://www.sourcekeg.co.uk/cran/bin/linux/ubuntu](http://www.sourcekeg.co.uk/cran/bin/linux/ubuntu) gutsy/ 
``` You will need to download the GPG key for that repo and add it to your apt key. Something like..```
 
wget -q [url for jpg key.gpg]("about:blank") -O- | sudo apt-key add - && sudo apt-get update 
``` Someone please feel free to jump in... I might be wrong here....

---

### Post by danielsbrewer on 2007-10-25
Thanks, but that line is commented out so I do not think my problem is associated with that.

---

### Post by danielsbrewer on 2007-10-26
I am still getting the same problem.  Surely either
1) Other people are having the same problem and it is a problem at the repository end
2) It is a problem with my configuration
3) People just ignore gpg protection

A few people have posted about this problem before and there has never been a satisfactory answer.

Please help.

---

### Post by danielsbrewer on 2007-10-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/33505](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/33505) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Think I have found the problem courtesy of bug #33505.  It might be because I am behind a transparent proxy.  The solution that works for me is to use this on the command line:

sudo apt-get update -o Acquire::http::No-Cache=True

Not sure how to get update manager and synaptic to use this though.  Any ideas?

---

### Post by donnykurnia on 2008-03-15
I found this page from google. Having the same problem, the option No-Cache works for me. To make this permanent, edit or create if not exist file /etc/apt/apt.conf. Add this line at the end of file:
```

Acquire::http::No-Cache "true";

```
It will make that option called even from update manager or synaptic.

---

