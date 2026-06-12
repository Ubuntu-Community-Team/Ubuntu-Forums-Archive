---
title: "Upgrade Help"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-10-21
Hi,

I followed the instructions in the Kubuntu website for upgrading to Gutsy. But when I click on Managae Resipotories in Adept Package Manager, I dont get a window similar to what is shown in the example snapshot given in the website. I have attached snapshots of my screen. Please help to upgrade to Gutsy.

Thanks.

---

### Post by Pumalite on 2007-10-21
[http://ubuntuforums.org/showthread.php?t=286599](http://ubuntuforums.org/showthread.php?t=286599)

---

### Post by linuxnovice on 2007-10-22
Hi,

That didnt help. I used kdesu update-manager -c and I got an error saying that command missing.

---

### Post by linuxnovice on 2007-10-30
Can someone help me please. I would love to try out Gutsy but I dont know how to upgrade.

---

### Post by rosswmcgee on 2007-10-30
What worked for me was to open system/software/sources/thirdpartysoftware/ and uncheck every thing. Then you should be able to upgrade.

---

### Post by linuxnovice on 2007-10-31
How do you get to that? Do I need to open a folder or something or just use adept?

---

### Post by Maestro23 on 2007-10-31
> **linuxnovice said:**
> How do you get to that? Do I need to open a folder or something or just use adept?

GUI: System>>Admin>>Software Source

Then do as the above post states.

---

### Post by linuxnovice on 2007-10-31
I dont have the admin option in system. Please refer to the pic. Is there anyway of getting to the software source using konsole?

---

### Post by Maestro23 on 2007-10-31
> **linuxnovice said:**
> I dont have the admin option in system. Please refer to the pic. Is there anyway of getting to the software source using konsole?

Sorry, didn't notice you were on KDE.

KMenu>>System>>Adept Package Manager

[https://help.ubuntu.com/community/Repositories/Kubuntu](https://help.ubuntu.com/community/Repositories/Kubuntu)

---

### Post by linuxnovice on 2007-10-31
Please take a look at my first post. That is the problem that I am facing. When I go to adept manager and click on manage resipotories, I get get a screen whose snapshot I have attached to my first post. I dont get the screen that is given in the link that you have in your post. So what do I do now?

---

### Post by Maestro23 on 2007-10-31
> **linuxnovice said:**
> Please take a look at my first post. That is the problem that I am facing. When I go to adept manager and click on manage resipotories, I get get a screen whose snapshot I have attached to my first post. I dont get the screen that is given in the link that you have in your post. So what do I do now?

I don't use KDE, but will try to help from another angle:

Can you open a terminal and type:

> cat /etc/apt/sources.list

Copy/Paste the file here.

---

### Post by linuxnovice on 2007-10-31
I did that. The pics show what I have under manage resipotories in Adept Manager.

---

### Post by linuxnovice on 2007-10-31
Contents of /etc/apt/sources.list:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://jordi.tecnosfera.org/robotOS/debian](http://jordi.tecnosfera.org/robotOS/debian) unstable main
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) feisty-wx main
deb-src [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) feisty-wx main
deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) feisty main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) feisty main

---

### Post by linuxnovice on 2007-11-01
Could someone please help me?

---

### Post by Pumalite on 2007-11-01
Advice from someone that doesn't like upgrades: save /home and data and do a clean install.

---

### Post by greg963 on 2007-11-01
try runn ing 
sudo aptitude install software-properties-kde

then follow the instructions at:
[https://help.ubuntu.com/community/GutsyUpgrades#head-3692aaaed415e3427f54ec62dd8659474516b525](https://help.ubuntu.com/community/GutsyUpgrades#head-3692aaaed415e3427f54ec62dd8659474516b525)

---

### Post by Maestro23 on 2007-11-01
> **greg963 said:**
> try runn ing 
sudo aptitude install software-properties-kde

then follow the instructions at:
[https://help.ubuntu.com/community/GutsyUpgrades#head-3692aaaed415e3427f54ec62dd8659474516b525](https://help.ubuntu.com/community/GutsyUpgrades#head-3692aaaed415e3427f54ec62dd8659474516b525)

Beat me with that link greg.:)

---

### Post by Maestro23 on 2007-11-01
> **Pumalite said:**
> Advice from someone that doesn't like upgrades: save /home and data and do a clean install.

Agree. That's what I did.  The advantages of having a /home partition.  Too many horror stories with this Feisty-Gutsy upgrade.

---

### Post by linuxnovice on 2007-11-02
Thanks guys. I like the idea of doing a clean install even though I need to waste a cd....But please tell me this. When you say save the /home, you mean back it up as in burn it on a DVD or something? 

Could I just point to it as /home during my new Gutsy install?

---

### Post by Pumalite on 2007-11-02
If you have /home in a separate partition, you can use it in your new install. Just don't format it. If you don't; here are a couple of ways of 'saving it':

[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by linuxnovice on 2007-11-02
I have a separate /home partition. I took some good advice about that when I was installing Fiesty :). So, when I install Gutsy, I just point to the /home I have and just not format it? Is that possible to do?

Suppose, I do that, will all my settings get erased? I know my files would be there..but what about my settings? Like I have done some big time modifications..will that all be gone?

---

