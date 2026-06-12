---
title: "I screwed up my sources list."
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by RossAndGarfunkel on 2008-04-15
I think i've managed to ruin my sources list. I ran the following code trying to install psX:

```
echo "deb http://packages.dfreer.org:8080 gutsy main" | sudo tee -a /etc/apt/sources.list
wget http://packages.dfreer.org:8080/7572013D.gpg -O- | sudo apt-key add -
sudo apt-get update
```

and ever since, my update manager has constantly been on. When I try to open it,  it gives me the following message:

> ]An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 57 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Also, when I open Synaptic or Add/Remove Programs, I get this message:

> Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by bodhi.zazen on 2008-04-15
post the optupt of :

```
cat -n /etc/apt/sources.list | grep 57
```

---

### Post by RossAndGarfunkel on 2008-04-15
> **bodhi.zazen said:**
> post the optupt of :

```
cat -n /etc/apt/sources.list | grep 57
```

```
    57  sudo tee -a /etc/apt/sources.list
    63  wget http://packages.dfreer.org:8080/7572013D.gpg -O- | sudo apt-key add -

```

---

### Post by jbrown96 on 2008-04-15
It looks like you're running Hardy Heron. If so here's my sources.list. You can copy/paste it into your sources with ```
sudo gedit /etc/apt/sources.list
```. Next time it might be worthwhile to make a backup first with ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
``` then you can restore it with ```
sudo cp /etc/apt/sources.list.bak /etc/apt/sources.list
``` if something happens again. 

Here's my sources. Note: I have enabled all the sources.
> # 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080318.1)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080318.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


---

### Post by RossAndGarfunkel on 2008-04-15
thanks, but I am running Gutsy.

---

### Post by bodhi.zazen on 2008-04-15
Yikes

You have to delete both of those lines, at least, from your sources list.

```
gksu gedit /etc/apt/sources.list
```

delete those lines, and anything similar, save and exit gedit, and re-try

---

### Post by Inxsible on 2008-04-15
Remove those lines from the sources.list file like bodhi says. Those two commands are supposed to be run in a terminal

---

### Post by Pitabread112 on 2008-04-17
> **jbrown96 said:**
> It looks like you're running Hardy Heron. If so here's my sources.list. You can copy/paste it into your sources with ```
sudo gedit /etc/apt/sources.list
```. Next time it might be worthwhile to make a backup first with ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
``` then you can restore it with ```
sudo cp /etc/apt/sources.list.bak /etc/apt/sources.list
``` if something happens again. 

Here's my sources. Note: I have enabled all the sources.

I was searching forever before I found this thread! I had the exact same thing happen to me while attempting to install a dock. It obviously didnt turn out right. Lucky me - I have Hardy Heron!

Thank you SOOOOOOO much for saving me! Posting your sources.list helped me a great deal, and I got to learn how it actually works :popcorn:

---

