---
title: "major failure of software management"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by lostinub on 2007-03-11
I have just tried to install automatix as described by ubuntu geek, and have gone really wrong somewhere. When i try to open application  > add/remove  all i get is a message
"This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'."
Unfortunately, I dont know what to check and if it is right or wrong. Pls help.

---

### Post by HereInOz on 2007-03-11
You have not told us which version you are running.  I am using Dapper, so my sources list may or may not be the same as yours, depending on which version you have.

The first thing you need to do is to open a terminal:  Applications > Accessories > Terminal
Type in: cd /etc/apt
Type in: ls -l

You will see a list of files, and in there there will be the sources list file, and the line should look like:

-rw-r--r-- 1 root root  2854 2007-03-02 22:37 sources.list

The numbers, date, and time will be different  but it is the first stuff that is important.

If the permissions listed (-rw-r--r-- 1 root root) are OK, then:

Type in: gksudo gedit sources.list
Enter your password

This will show you your sources.list file.

So you can check, this is what my sources.list file looks like:

===================================================

# 
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

# Line commented out by installer because it failed to verify:
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
#AUTOMATIX REPOS END

==================================================

If you are running Edgy, then all references will be to Edgy, rather than Dapper, but essentially it should be the same.

This should give you something to start with to do what the message says - check out the permissions and correctness of your sources.list file.

If this doesn't help and nothing changes, then post back.

---

### Post by HereInOz on 2007-03-11
By the way, you will also notice, in /etc/apt that there should be backups taken of your sources.list file.  These have a date embedded in the filename.

These may help you to recover from what has happened as well.

---

### Post by lostinub on 2007-03-11
drwxr-xr-x 2 root root 4096 2007-03-11 12:03 sources.list.

looks a bit different at the front end

---

### Post by lostinub on 2007-03-11
copy of sources list file

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe main multiverse restricted #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.cononical.com/ubuntu](http://archive.cononical.com/ubuntu) edgy-commercial main
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main&#8221;
&#8220; [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main&#8221;

---

### Post by HereInOz on 2007-03-11
Something is not right there.  Did you use the .deb file to install Automatix?  If so, you can easily uninstall it (dpkg purge {application name}) and then rename the sources.list file as sources.old, and rename the latest backup file as sources.list.

No guarantees, but this may get you back and ready for another shot.

There are certainly no Automatix entries in your sources.list file, so something has gone very wrong with the installation of Automatix.

How comfortable are you with the terminal?  Can you rename files and change permissions?  The permissions of your sources.list look odd - the "d" is telling you that it is a directory, when clearly it is not.  I am a little bewildered at that.

If you are not comfortable with the terminal, open a terminal and type:
gksudo nautilus
Then enter your password.

This will give you the GUI file manager with root permissions, which will allow you to work in the /etc/apt folder and change names and permissions of the files.

Hope this helps.

---

### Post by jackrobinson on 2007-03-11
> **lostinub said:**
> copy of sources list file

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe main multiverse restricted #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.cononical.com/ubuntu](http://archive.cononical.com/ubuntu) edgy-commercial main
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”
“ [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”
just do the following:
```
sudo gedit /etc/apt/sources.list
```
and make the SECOND-LAST line look as follows.,:
> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
and delete the LAST line
> “ [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”
now save and close the file and do:
```
sudo apt-get update
``````

```

---

### Post by lostinub on 2007-03-11
All working!!!
Thanks  very much.  I can try and work my way down from panic to usual bewilderment

---

