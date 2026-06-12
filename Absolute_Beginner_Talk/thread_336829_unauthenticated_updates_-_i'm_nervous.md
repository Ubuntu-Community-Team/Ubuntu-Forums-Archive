---
title: "unauthenticated updates - i'm nervous"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Tanchelm on 2007-01-12
I had a balloon pop up to tell me that I have 44 updates to install.  when I click install I receive a warning that the software cannot be authenticated - and I'm worried I'm dowloading nasty stuff.  so I thought I'd post this before I bite the bullet.

I am only very new to Ubuntu and have only recently been able to use Ubuntu to connect to the net.

could use some reassurance or guidance thanks.

---

### Post by Bachstelze on 2007-01-12
Could you please paste your /etc/apt/sources.list ?

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Tanchelm on 2007-01-12
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


when I typed the line in terminal it responded with:

tanchelm@edgy:~$ gksudo gedit /etc/apt/sources.list
(gedit:7844): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by Bachstelze on 2007-01-12
The last thing you mention is pretty normal. What happens when you run this ?

```
sudo apt-get update
```

---

### Post by Tanchelm on 2007-01-12
it seemed to hang for a while and then I got an error.  This does not surprise me - I have an unresolved problem of not being able to update my software sources - do you have any suggestions?

the following is the result of sudo apt-get update:

tanchelm@edgy:~$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg                                               
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                                     
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]

---

### Post by Delkster on 2007-01-12
> **Tanchelm said:**
> [Connecting to security.ubuntu.com (1.0.0.0)]

Like I responded in the [other thread](http://ubuntuforums.org/showthread.php?t=332182), it seems to think that the IP address of security.ubuntu.com is 1.0.0.0, which it certainly isn't.

---

### Post by Bachstelze on 2007-01-12
Yep, most likely a DNS problem. Is evrything else web-related working properly ?

---

### Post by jvc26 on 2007-01-12
I'd try the following:
```

sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list

```

Then replace all the stuff in your /etc/apt/sources.list file with:
```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen

```

Then save the edited file and close it.
Then in terminal type:
```

wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update

```
Then try again - (this was taken off the ubuntu guide so the sources.list is reputable.)

A while back I had a similar problem which was resolved by this, however it may well be as HymnToLife suggests a DNS problem
Il

---

### Post by Pobega on 2007-01-12
If that doesn't work you can always try putting us. in front of your URLs, like so:

> deb [http://**us.**archive.ubuntu.com/ubuntu](http://**us.**archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

I'm not exactly sure if this will work, but if it is a DNS problem this will likely solve it for now.

---

