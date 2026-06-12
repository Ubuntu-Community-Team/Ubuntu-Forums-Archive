---
title: "couldn't find package cvs"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by TRAyres on 2007-09-02
Hi everyone,
I've got Feisty Fawn 7.04, and I'm currently trying to get my linksys wireless USB network adapter to work  (WUSB11 version 2.5). 

I found the page: [https://wiki.ubuntu.com/WifiDocs/Device/LinksysWUSB11](https://wiki.ubuntu.com/WifiDocs/Device/LinksysWUSB11)
and started to follow the directions, but I get to number 14, which is typing "sudo apt-get install cvs"
- I type this into the terminal, and it tells me "Couldn't find package cvs". I have the ISO I installed ubuntu from in the drive an on hand.

I can't seem to move forward without this being resolved. Can somebody please help me?

I type sudo apt-get install cvs, it asks for a password, then it says,
"Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package cvs"

---

### Post by Hobo Joe on 2007-09-02
Are all your repositories enabled?

---

### Post by TRAyres on 2007-09-02
Not that I am aware of - I don't even know what that is.

Edit: I looked it up, went to System/Administration/Software Sources, and main, universe, restricted, and multiverse are all checked. So I think they're all enabled. Thats interesting, because I just put the CD in and installed it and never told it to enable them. Are they normally off?

This is a 64 bit distribution - does that affect anything?

Thanks for the help so far

---

### Post by por100pre1 on 2007-09-02
Try searching for it:

```
aptitude search cvs
```

---

### Post by TRAyres on 2007-09-02
aptitude search cvs returned nothing - just went to a new terminal line....

---

### Post by por100pre1 on 2007-09-02
I'm using a 32bit  version so I can't tell you if cvs is available for the version you are using. :(

EDIT: here it shows an enormous list.

EDIT:Just in case:

```
cat /etc/apt/sources.list
```

and post the results...

---

### Post by TRAyres on 2007-09-02
This is the output:
cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse
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

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe


Thanks for all the help so far everyone!

-Any ideas as to how to fix this yet?

---

### Post by TRAyres on 2007-09-03
Bump

---

### Post by por100pre1 on 2007-09-03
> **TRAyres said:**
> This is the output:
cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse
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

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[COLOR="Red"]# [/COLOR]**deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse**
[COLOR="Red"]# [/COLOR]**deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse**

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe


Thanks for all the help so far everyone!

-Any ideas as to how to fix this yet?

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

```
sudo gedit /etc/apt/sources.list
```

Delete the shown [COLOR="Red"]#[/COLOR] and the space after it in the bold lines. 

Save and do:

```
sudo apt-get update
```

Let's see if that helps... :-k

---

### Post by schorsch on 2007-09-03
> **por100pre1 said:**
> 
EDIT: here it shows an enormous list.

```
aptitude search ^cvs
```
or
```
apt-cache search ^cvs
```
will make the list a lot shorter .... but only if the desired package name really starts with cvs .. ;-)

---

### Post by por100pre1 on 2007-09-03
> **schorsch said:**
> ```
aptitude search ^cvs
```
or
```
apt-cache search ^cvs
```
will make the list a lot shorter .... but only if the desired package name really starts with cvs .. ;-)

Thanks for the command! The problem here is that the OP gets nothing.

---

### Post by schorsch on 2007-09-03
CVS is in the main repos according to [this link]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Fc%2Fcvs%2Fcvs_1.12.13-5build1_amd64.deb&md5sum=4978409f40ea7a32ce3cf846b5b9ad41&arch=amd64&type=main") even for 64 Bit and it will be installed per default as it is in the "main" repos when you install Feisty and have network access.
@ OP: Do you have wired access to network to install those packages?

---

### Post by TRAyres on 2007-09-04
I could run some cat5 to my linux box I guess. I'll have to go get some.
*edit* is that the solution? Reinstall only connected to a network?

---

