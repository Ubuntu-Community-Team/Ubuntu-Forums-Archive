---
title: "[SOLVED] fasing problum after upgrade to 7.10"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by rahul_bhise on 2008-01-01
i burned a alternate cd i md5sum it and also checked it.it is ok
after inserting it i was given two option 
1>open it with synaptic manager
2>upgrade
first i chossed upgrade option but after some time it told me that it could not calculate upgrade time (or something) and aborded upgrade
then in the secont time i chossed the first option and it opende the synaptic manager and showed 175 upgrade some, programes would be deleated and some unchanged. i clicked appluy and ok.
then after upgrading and all that, the system restarted and i was taken to the user login i chossed the administer user and gave my password but then i was taken to a blank screen.
what should i do.
i also have a live cd.

---

### Post by wasing on 2008-01-01
did you back up your files before trying to upgrade with the alternate install

---

### Post by rahul_bhise on 2008-01-01
no i did not backup for i don't have any important files on it
also i have my home folder on a different partition

---

### Post by overdrank on 2008-01-01
> **rahul_bhise said:**
> no i did not backup for i don't have any important files on it
also i have my home folder on a different partition

Hi and what is the model of the graphics card and did you attempt to reconfigure it from recovery mode.

---

### Post by rahul_bhise on 2008-01-01
i have intel(R) 82845G graphics controller
i dont now how to reconfiger it
what is the command for it as in the recovery mode  i can login to the root.

---

### Post by overdrank on 2008-01-01
> **rahul_bhise said:**
> i have intel(R) 82845G graphics controller
i dont now how to reconfiger it
what is the command for it as in the recovery mode  i can login to the root.

Hi and you can try ```
sudo dpkg-reconfigure xserver-xorg
``` but intel works pretty good so I believe something else may have happened during the upgrade.

---

### Post by rahul_bhise on 2008-01-01
i tried to sudo dpkg-reconfigure xserver-xorg  but it said
```
user/sbin/dpkg-reconfigure: xserver-xorg is broken or not installed properly
```

---

### Post by rahul_bhise on 2008-01-02
i got into login screen by doing this in terminal
```
sudo dpkg --configure -a
sudo apt-get install ubuntu-desktop --reinstall
```
then paste my backup copy of xorg to the now config one
but there are still some weared problems
1> when i click on help buttion the help appears but only for 2 seconds and then closes
2> most of the application in system>administration does not work as update manager,software sorces etc

---

### Post by rahul_bhise on 2008-01-03
i am in despereate need of help

---

### Post by xeth_delta on 2008-01-03
Have you tried:
```
sudo apt-get clean
sudo apt-get check
```

---

### Post by rahul_bhise on 2008-01-04
the problem was not solved after doing the above two commands
the output of update-manager
```
**brahul@uhome:~$ update-manager**
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:48: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import atk
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk.glade
ImportError: cannot import name Widget from gtk
**brahul@uhome:~$** 
```

---

### Post by xeth_delta on 2008-01-05
> **rahul_bhise said:**
> the problem was not solved after doing the above two commands
the output of update-manager
```
**brahul@uhome:~$ update-manager**
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:48: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import atk
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk.glade
ImportError: cannot import name Widget from gtk
**brahul@uhome:~$** 
```

Seems to be a problem with update-manager. Try an "apt-get update" in a termilnal and post the eventual errors.

---

### Post by rahul_bhise on 2008-01-06
```
**brahul@uhome:~$ apt-get update**
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
**brahul@uhome:~$ sudo apt-get update**
[sudo] password for brahul:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_IN
Get:1 http://in.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://in.archive.ubuntu.com gutsy/main Translation-en_IN                  
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_IN
Ign http://in.archive.ubuntu.com gutsy/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com gutsy/universe Translation-en_IN
Ign http://in.archive.ubuntu.com gutsy/multiverse Translation-en_IN
Get:3 http://in.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://in.archive.ubuntu.com gutsy-updates/main Translation-en_IN
Ign http://in.archive.ubuntu.com gutsy-updates/restricted Translation-en_IN
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_IN
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_IN
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_IN
Ign http://in.archive.ubuntu.com gutsy-updates/universe Translation-en_IN
Ign http://in.archive.ubuntu.com gutsy-updates/multiverse Translation-en_IN
Get:4 http://in.archive.ubuntu.com gutsy-backports Release.gpg [191B]
Ign http://in.archive.ubuntu.com gutsy-backports/main Translation-en_IN
Hit http://security.ubuntu.com gutsy-security Release
Ign http://in.archive.ubuntu.com gutsy-backports/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com gutsy-backports/universe Translation-en_IN
Ign http://in.archive.ubuntu.com gutsy-backports/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com gutsy Release
Hit http://in.archive.ubuntu.com gutsy-updates Release
Hit http://in.archive.ubuntu.com gutsy-backports Release            
Hit http://security.ubuntu.com gutsy-security/main Packages         
Hit http://in.archive.ubuntu.com gutsy/main Packages
Hit http://in.archive.ubuntu.com gutsy/restricted Packages
Hit http://in.archive.ubuntu.com gutsy/universe Packages
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://in.archive.ubuntu.com gutsy/multiverse Packages
Hit http://in.archive.ubuntu.com gutsy-updates/main Packages
Hit http://in.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://in.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://in.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://in.archive.ubuntu.com gutsy-backports/main Packages
Hit http://in.archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://in.archive.ubuntu.com gutsy-backports/universe Packages
Hit http://in.archive.ubuntu.com gutsy-backports/multiverse Packages
Fetched 4B in 2s (1B/s)  
Reading package lists... Done
**brahul@uhome:~$** 
```

---

### Post by rahul_bhise on 2008-01-06
problem solved
i installed some software
libiconv-1.11
glib-2.14.3
atk-1.9.1
and my update-manager, yelp and all the system>administration>*all application*  started working properly

---

