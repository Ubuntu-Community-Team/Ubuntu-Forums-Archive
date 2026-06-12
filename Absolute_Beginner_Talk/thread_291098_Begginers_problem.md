---
title: "Begginers problem"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Luj0 on 2006-11-02
Hi,
newbie at this, so i have a problem, and i know that you will be able to solve it :) 
I cant install anything :-k  , in synaptic package manager all the files are installed, when i search for, example, TV TIME nothing is found, and i cant opet add/remove programs,when it finishes checking for nstalled... window disapears.
Sorry if this isn't a way to install things, n000000000000b ](*,) so please I need a little help...

---

### Post by NeoLithium on 2006-11-02
I'm not sure if you have dapper installed or not; but you may want to check if you have all the repositories enabled.  There's a quick tutorial on how to maximize the stuff you can install located [here]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories").
Hopefully this helps you out! :)

---

### Post by Luj0 on 2006-11-02
# Settings -> Repositories
# In the Installation Media tab, click Add. There are three separate repositories; Dapper Drake, Security Updates and Updates. Select each repository and check Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse). Ensure you click OK between each repository to save your changes 




When i open synaptic, and then click on repositories, there arent dapper drake and the rest, there is only instalation media, internet updates and updates

---

### Post by NeoLithium on 2006-11-02
Really? Can you open a terminal window, and paste the results of this:
```
 cat /etc/apt/sources.list 
```

Normally they should have all of them there by default; but normally just not activated. For instance, here is what mine looks like:
```
 
deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

---

### Post by Joe_CoT on 2006-11-02
The easiest way to get your sources is [source-o-matic](http://www.ubuntulinux.nl/source-o-matic).

From a console, type:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo gedit /etc/apt/sources.list
```

In source-o-matic, select your distro, your architecture, your country, that you want security updates and updates, and that you want official and community packages. Click "Give me my sources.list", and overwrite your sources.list with what it gives you. It's not updated for Edgy yet, but you can do a find and replace to change Dapper to Edgy.

Save the file, restart Synaptic, then click reload. Should work.

---

### Post by Luj0 on 2006-11-02
Coudnt before, but i managed wit the link u gave,i have changed something and now this appears, and i can search with synaptic

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by NeoLithium on 2006-11-02
Joe's idea works very well, I should point out. I've messed up my sources a few times, but that happens.  Basically when I have a fresh install of Ubuntu ; I activate the multiverse repo's ASAP, and pretty much everything, and run my update; pretty snappy and find it works well; of course everyone has their preferences.

---

