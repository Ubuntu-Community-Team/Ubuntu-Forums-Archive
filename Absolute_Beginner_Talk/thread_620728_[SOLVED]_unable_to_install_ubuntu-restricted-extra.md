---
title: "[SOLVED] unable to install ubuntu-restricted-extras"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by samuel.rajesh on 2007-11-22
Hi ,

I jus made the move to ubuntu 7.10 today and im tearing my hair out .i got it installed and running and connected to the internet and am trying to play divx and mp3 files ,so i tried to install the ubuntu-restricted-extras through application --> add remove ---> and then searching for the package and then clicking

what happens is
1)when its selected a window pops up "list of applications not available "
2) then i click refresh as indicated where it dowloads something
3) tada nothing happens the apply changes button is not activated

I tried installing other software as well nothing happens
tried the terminal and here is what i got

sam@sam-laptop:~$ sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package gstreamer0.10-pitfdll
sam@sam-laptop:~$

Now what could be the problem ,internet is working jus fine ,please help .


thanks
Sam

---

### Post by taurus on 2007-11-22
I bet all your repos in /etc/apt/sources.list are commented out, with a # in front of all the lines.

Can you post it here?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Kingsley on 2007-11-22
```
sudo gedit /etc/apt/sources.list
```

Remove the '#' from the website links. Then try to install whatever you needed.

---

### Post by samuel.rajesh on 2007-11-22
dang i think i screwed it further 


used the below command 

sudo gedit /etc/apt/sources.list

and then did a replace **#** with "**empty**" as in blank space 


now i get this message 


This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.



Sam

---

### Post by samuel.rajesh on 2007-11-22
sam@sam-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
 See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
 newer versions of the distribution.

 Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
 Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

 Major bug fix updates produced after the final release of the
 distribution.
 Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
 Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

 N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 team, and may not be under a free licence. Please satisfy yourself as to
 your rights to use the software. Also, please note that software in
 universe WILL NOT receive any review or updates from the Ubuntu security
 team.
 Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
 Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
 Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
 Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

 N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 team, and may not be under a free licence. Please satisfy yourself as to 
 your rights to use the software. Also, please note that software in 
 multiverse WILL NOT receive any review or updates from the Ubuntu
 security team.
 Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
 Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
 Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
 Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

 Uncomment the following two lines to add software from the 'backports'
 repository.
 N.B. software from this repository may not have been tested as
 extensively as that contained in the main release, although it includes
 newer versions of some applications which may provide useful features.
 Also, please note that software in backports WILL NOT receive any review
 or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

 Uncomment the following two lines to add software from Canonical's
 'partner' repository. This software is not part of Ubuntu, but is
 offered by Canonical and the respective vendors as a service to Ubuntu
 users.
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

 Line commented out by installer because it failed to verify:
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
 Line commented out by installer because it failed to verify:
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
 Line commented out by installer because it failed to verify:
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
 Line commented out by installer because it failed to verify:
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
 Line commented out by installer because it failed to verify:
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
 Line commented out by installer because it failed to verify:
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
sam@sam-laptop:~$

---

### Post by taurus on 2007-11-22
You are supposed to remove the # from all the lines that start with **deb** & **deb-src** only, not all the lines in there.  Therefore, you need to edit it again

```
**gksudo** gedit /etc/apt/sources.list
```
and put back the # in front of all the lines that don't have deb or deb-src at the beginning.

---

### Post by FuturePilot on 2007-11-23
Looks like you uncommented everything. You only need to remove the # in front of the lines that begin with deb and deb-src

taurus beat me to it ;)

---

### Post by taurus on 2007-11-23
> **FuturePilot said:**
> Try
```
sudo apt-get update
sudo apt-get install -f
```
That will try to correct any dependency problems you might have

Look at his /etc/apt/sources.list.

---

### Post by FuturePilot on 2007-11-23
> **taurus said:**
> Look at his /etc/apt/sources.list.

Yes, I just noticed that. I fixed my other post.

---

### Post by samuel.rajesh on 2007-11-23
> **taurus said:**
> You are supposed to remove the # from all the lines that start with **deb** & **deb-src** only, not all the lines in there.  Therefore, you need to edit it again

```
**gksudo** gedit /etc/apt/sources.list
```
and put back the # in front of all the lines that don't have deb or deb-src at the beginning.


:) that did it ,now its downloading a lot of stuff and hopefully it should solve the problem ,thanks mate for ur time and patience ,i owe u one .

Sam

---

### Post by erfahren on 2007-11-23
one note: it's important that you only have one package management service open at a time. So don't have Synaptic open when updating or installing through the terminal for example. Or Add/Remove open with Synaptic, etc.

ok, do this: 
first backup your current sources.list
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

```
then open up your sources.list again and replace the sources (starting below where it lists your CD) with this:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Uncomment deb-src if you wish to download the source packages

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse 
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted 
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted 
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted 

## START -- MANUALLY ADDED
##

## BACKPORTS REPOSITORY
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted
deb http://archive.ubuntu.com/ubuntu gutsy-backports universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports universe multiverse

## THIRD-PARTY REPOSITORIES
##
## MEDIBUNTU  
deb http://packages.medibuntu.org/ gutsy free non-free

## CANONICAL REPOSITORY
deb http://archive.canonical.com/ubuntu gutsy partner

```
then in terminal do this (add the key for Medibuntu):
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```
then
```

sudo apt-get update

```
```

sudo apt-get install -f

```

---

### Post by samuel.rajesh on 2007-11-23
Now how do i mark this thread as solved ???

---

### Post by erfahren on 2007-11-23
go to where it says "Thread Tools" at the top

---

