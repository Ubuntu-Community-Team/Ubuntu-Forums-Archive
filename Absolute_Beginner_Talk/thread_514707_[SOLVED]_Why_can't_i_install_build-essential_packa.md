---
title: "[SOLVED] Why can't i install build-essential package?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by amazingjxq on 2007-08-01
when i 
 sudo apt-get install build-essential

the terminal showed this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

I just wonder why

---

### Post by scxtt on 2007-08-01
what's the output of: **cat /etc/apt/sources.list** ... ?

it's in the "main" section, btw -- [http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/](http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/)

---

### Post by tchoklat on 2007-08-01
look in synaptic

---

### Post by amazingjxq on 2007-08-01
I can't find it in synaptic.Should i search build-essential in the "search"?

---

### Post by scxtt on 2007-08-01
synaptic reads /etc/apt/sources.list the same way apt-get/aptitude do ... if you don't have the "main" section in that file, you won't be able to install it via apt ...

---

### Post by amazingjxq on 2007-08-01
> **scxtt said:**
> what's the output of: **cat /etc/apt/sources.list** ... ?

it's in the "main" section, btw -- [http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/](http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/)

Should i download the  build-essential_11.3_i386.deb       or what?

---

### Post by amazingjxq on 2007-08-01
> **scxtt said:**
> synaptic reads /etc/apt/sources.list the same way apt-get/aptitude do ... if you don't have the "main" section in that file, you won't be able to install it via apt ...

What is the "main" section?

---

### Post by scxtt on 2007-08-01
from my file /etc/apt/sources.list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty **main** restricted

that's what i'm talking about w/ "main" ... the link i provided before was just "proof" that that's where build-essential was ... it's possible that you could just dpkg -i the *.deb, don't know if it has dependencies that aren't on your box ...

if you post your sources.list, it would be helpful ...

---

### Post by ugm6hr on 2007-08-01
> **amazingjxq said:**
> when i 
I just wonder why

Are you online from your Ubuntu box?

---

### Post by amazingjxq on 2007-08-01
> **scxtt said:**
> from my file /etc/apt/sources.list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty **main** restricted

that's what i'm talking about w/ "main" ... the link i provided before was just "proof" that that's where build-essential was ... it's possible that you could just dpkg -i the *.deb, don't know if it has dependencies that aren't on your box ...

if you post your sources.list, it would be helpful ...

Thx,i will upload it after i come back home. Now i'm not using ubuntu.
By the way,how to open the source.list ?Is the source.list like server.met in emule?
When i sudo apt-get install build-essential the terminal said  can't find *** package. What's wrong?

---

### Post by aktiwers on 2007-08-01
The sourcelist is the text file where apt and synaptic gets the links it need to download the software from. To open and modify in it type:
```
gksudo gedit /etc/apt/sources.list
```

Maybe paste it here so we can see whats missing.

---

### Post by Seisen on 2007-08-01
You can also modify your source list through Synaptic by clicking on Settings>Repositories.

---

### Post by aysiu on 2007-08-01
*build-essential* should also be on your installation CD if you don't have an internet connection. ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by amazingjxq on 2007-08-01
This is my sources.list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntuarchive.is.co.za/ubuntu/](http://ubuntuarchive.is.co.za/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntuarchive.is.co.za/ubuntu/](http://ubuntuarchive.is.co.za/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntuarchive.is.co.za/ubuntu/](http://ubuntuarchive.is.co.za/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntuarchive.is.co.za/ubuntu/](http://ubuntuarchive.is.co.za/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://ubuntuarchive.is.co.za/ubuntu/](http://ubuntuarchive.is.co.za/ubuntu/) feisty-security main restricted
deb [http://ubuntuarchive.is.co.za/ubuntu/](http://ubuntuarchive.is.co.za/ubuntu/) feisty-security universe
deb [http://ubuntuarchive.is.co.za/ubuntu/](http://ubuntuarchive.is.co.za/ubuntu/) feisty-security multiverse



PS:I remember i checked the language surpport and in the Download from i choose "choose best server",would this affect it?

---

### Post by aysiu on 2007-08-01
You may just have to click **Reload** in Synaptic before searching for *essential*

---

### Post by amazingjxq on 2007-08-01
OK, now it's downloading. I chose another server and reloaded it.

---

### Post by Seisen on 2007-08-01
Anytime you make a change to your source list always either do a```
sudo apt-get update
``` or if you are using Synaptic hit Reload.

---

### Post by amazingjxq on 2007-08-01
Yes, thank you all. I wil remember this.

---

