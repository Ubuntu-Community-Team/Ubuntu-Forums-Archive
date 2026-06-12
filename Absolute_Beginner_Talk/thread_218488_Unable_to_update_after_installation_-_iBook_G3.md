---
title: "Unable to update after installation - iBook G3"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by tjod on 2006-07-18
Hi all;

Having a bit of an odd problem here.](*,) 

I installed Ubuntu 6.06 LTS on a Mac iBook G3 14.1 screen. When I try to update via the update Manager, I get x number of messages (84 the last time) such as: 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/wpasupplicant_0.4.8-3ubuntu1.1_powerpc.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/wpasupplicant_0.4.8-3ubuntu1.1_powerpc.deb)
  Connection failed [IP: 82.211.81.151 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb)
  Connection failed [IP: 82.211.81.151 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_4_all.deb)
  Connection failed [IP: 82.211.81.151 80]

When I run the exact URL noted above on another machine on the same network (a WinXP machine) I can get through to the site just fine and download the file. When I manually insert the URL into Firefox on the Ubuntu iBook, I get a message saying. that Apache has not been configured on the server. All of my standard URLs and websites work fine on the Ubuntu machine, as does email. 

Any ideas? 

TIA!

tj

---

### Post by Skia_42 on 2006-07-18
It sounds like your internet connection is fine, would you mind posting your source list? (/etc/apt/sources.list)

---

### Post by shoot2kill on 2006-07-18
> **Skia_42 said:**
> It sounds like your internet connection is fine, would you mind posting your source list? (/etc/apt/sources.list)
to me it sounds like internet is not configured... please, test internet for me... try google or ubuntuforums on internet in ubuntu, or try
> ping [www.google.com](www.google.com)
in terminal

---

### Post by tjod on 2006-07-18
"All of my standard URLs and websites work fine on the Ubuntu machine, as does email. "  i.e. internet /network is configured

---

### Post by tjod on 2006-07-18
Here it is: 

# 
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release powerpc (20060531)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release powerpc (20060531)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Skia_42 on 2006-07-18
ok, you are running Dapper correct? If so, backup your original source list and try mine:
> # deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
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

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


---

### Post by tjod on 2006-07-18
Thanks, I'll give that a try. 

I'm curious as to how it was decided to rewrite the file (by the installer, I assume?) and why it's so ambiguous in the messages. The site is certainly valid. FWIW this was a fresh install so there was nothing leftover to influence anything.

---

### Post by tjod on 2006-07-18
> **Skia_42 said:**
> ok, you are running Dapper correct? If so, backup your original source list and try mine:

Errrr ... I can't seem to save the file. I keep getting a message saying I don't have permission. Doesn't a normal user have rights to edit a file??

What do I need to do to edit the file "sources.list" AND save it?

---

### Post by Jagot on 2006-07-18
> **tjod said:**
> What do I need to do to edit the file "sources.list" AND save it?

From Terminal:

```
sudo gedit /etc/apt/sources.list
```

---

### Post by tjod on 2006-07-18
I tried that, but maybe I typoed something wrong.  Thx. 8-)

---

### Post by catlett on 2006-07-18
If you are running dapper do not use skia's list. Skia's list is for the older edition of Ubuntu.
It will not update your system. There is a chance it might downgrade your system to Breezy.
This is your system 
```
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release powerpc (20060531)]/ dapper main restricted
```It is ubuntu 6.06 Dapper


This is Skia's system 
```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)]/ breezy main restricted
```
5.10 Breezy Badger

You can't mix the repositories.
If Skia was to put your list in, it would cause that system to update to Dapper.
I have never seen what happens when someone puts in an old list like you are about to do. At the worst it will downgrade your system to 5.10. At the least it will do nothing because all your packages will be at a higher level than the ones in those repositories.

Go to those sights with firefox and see if you can access the server and download. Just click on the url in this thread from the source list you posted. If you get in you will see an index of ubuntu with a small menu. Go to dists and then to any dapper link. Select power pc and see if you can download the tar gz. If you can do that, then synaptic should be able to as well.

If that works, put this in the terminal to update via the terminal```
 sudo aptitude update
```
```
sudo aptitude upgrade
```But only if you didn't change your list. If you changed the list, change it back.

---

### Post by tjod on 2006-07-18
$ sudo aptitude update
E: Type 'Edit/Delete' is not known on line 42 in source list /etc/apt/sources.list
E: Type 'Edit/Delete' is not known on line 42 in source list /etc/apt/sources.list
E: The list of sources could not be read.

This is too bizarre. Did the wrong files come with the installation? I did not change anything prior to trying the updates.  Is Linux always this much fun or does it get better? 8-)

---

### Post by tjod on 2006-07-18
re-saved the file and tried again. This is now the original sources.list file

--------------------------
tjod@skykomish:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Ign cdrom://Ubuntu 6.06 _Dapper Drake_ - Release powerpc (20060531) dapper Release.gpg
Ign cdrom://Ubuntu 6.06 _Dapper Drake_ - Release powerpc (20060531) dapper Release
Ign cdrom://Ubuntu 6.06 _Dapper Drake_ - Release powerpc (20060531) dapper/main Packages
Ign cdrom://Ubuntu 6.06 _Dapper Drake_ - Release powerpc (20060531) dapper/restricted Packages
Ign cdrom://Ubuntu 6.06 _Dapper Drake_ - Release powerpc (20060531) dapper/main Packages
Ign cdrom://Ubuntu 6.06 _Dapper Drake_ - Release powerpc (20060531) dapper/restricted Packages
Err cdrom://Ubuntu 6.06 _Dapper Drake_ - Release powerpc (20060531) dapper/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 6.06 _Dapper Drake_ - Release powerpc (20060531) dapper/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 6.06 _Dapper Drake_ - Release powerpc (20060531) dapper/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 6.06 _Dapper Drake_ - Release powerpc (20060531) dapper/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 82.211.81.151 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed [IP: 130.239.18.159 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 82.211.81.151 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 82.211.81.151 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed [IP: 130.239.18.159 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed [IP: 130.239.18.159 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed [IP: 130.239.18.159 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 82.211.81.151 80]
----------------------------------------------------

Ugh.

---

### Post by Skia_42 on 2006-07-18
> **catlett said:**
> If you are running dapper do not use skia's list. Skia's list is for the older edition of Ubuntu.
It will not update your system. There is a chance it might downgrade your system to Breezy.
This is your system 
```
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release powerpc (20060531)]/ dapper main restricted
```It is ubuntu 6.06 Dapper


This is Skia's system 
```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)]/ breezy main restricted
```
5.10 Breezy Badger

You can't mix the repositories.
If Skia was to put your list in, it would cause that system to update to Dapper.
I have never seen what happens when someone puts in an old list like you are about to do. At the worst it will downgrade your system to 5.10. At the least it will do nothing because all your packages will be at a higher level than the ones in those repositories.

Go to those sights with firefox and see if you can access the server and download. Just click on the url in this thread from the source list you posted. If you get in you will see an index of ubuntu with a small menu. Go to dists and then to any dapper link. Select power pc and see if you can download the tar gz. If you can do that, then synaptic should be able to as well.

If that works, put this in the terminal to update via the terminal```
 sudo aptitude update
```
```
sudo aptitude upgrade
```But only if you didn't change your list. If you changed the list, change it back.

I am running 6.06 on my computer, my list would not downgrade yor system to 5.10 for I copied it from my source file. All of the Breezy Badger repositories are denoted as comments with "#". (Correct me if I am wrong)

---

### Post by tjod on 2006-07-19
Reinstalled. Same issue(s). I think I will try from a completely different network tomorrow.

---

### Post by Jagot on 2006-07-19
Have you tried using the sources.list from here:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

### Post by Electric_Cowboy on 2006-07-20
I just installed ubuntu 6.06 but was not asked for an admin/root 
password during install. When I tried to update it asked for
an admin password.

Is there a default admin password? :confused: 

If so what is it, and how do I change it?

---

### Post by Jagot on 2006-07-20
There is no root user by default.  You can read about how Ubuntu handles this here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

When it asks for a password enter your user password.

---

### Post by tjod on 2006-07-20
Thanks to all who replied.

I am now updated. Resolved by:

1. Reinstalled from original disc.

2. ran 'sudo aptitude update' 

3. ran Synaptic.

By all appearances I am completely updated, though some messages remain about not being able to contact various security update locations.

Thanks to all who replied!

tj:D

---

### Post by catlett on 2006-07-20
> **Skia_42 said:**
> ok, you are running Dapper correct? If so, backup your original source list and try mine:

My apologies Skia. I just looked at the cd line and saw Breezy. I should have looked further and I would have noticed the comment marks. I stand corrected, sorry if I caused an offense.

---

