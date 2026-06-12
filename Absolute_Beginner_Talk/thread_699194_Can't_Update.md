---
title: "Can't Update"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by splendid on 2008-02-17
Not sure what happened.  When I click on System Administration, many of the selection are no longer there.  I am unable to use update manager.  It say's there are 4 updates out there, but will not download and install them.  Each time I click on Install updates it goes out and searches for the latest updates.  

I don't have the ability to add any new applications since Synaptic Package Manager choice is missing.

Thanks for the help!

---

### Post by jan quark on 2008-02-17
>  Not sure what happened. When I click on System Administration, many of the selection are no longer there. I am unable to use update manager. It say's there are 4 updates out there, but will not download and install them. Each time I click on Install updates it goes out and searches for the latest updates.

please post the output of 

```

cat /etc/apt/sources.list
```

> 
I don't have the ability to add any new applications since Synaptic Package Manager choice is missing.


where is the synaptic choice missing?

---

### Post by splendid on 2008-02-17
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by splendid on 2008-02-17
Synaptic choice is missing from  System>Administration>

---

### Post by jan quark on 2008-02-17
> Not sure what happened. 

:)

tell us the truth ( only joking) 

did you install some unusual applications or did you encounter any error messages before this happened

your software sources seem to be fine

edit: check the main menu settings if they are also missing run

```
alacarte
```

in terminal

---

### Post by splendid on 2008-02-17
I installed Wine and was trying to get my DVD burner working.  K3b does not recognize a blank DVD when I enter it.  

:)

---

### Post by splendid on 2008-02-17
alacarte
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py:50: GtkWarning: cannot open display:  
  self.gnome_program = gnome.init('alacarte', version)

---

### Post by splendid on 2008-02-17
When I select Main Menu, I can see everything there in Administration, and they are unchecked.  When I check to select them, it allows me to do it, but one second later, and the check mark disappears.

---

### Post by jan quark on 2008-02-17
run 

```
metacity --replace
```

and see what happens :)

really weird problem you have

---

### Post by splendid on 2008-02-17
I get this message, when I tried to run update again.

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '23068675' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmp5umN4a' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

---

### Post by splendid on 2008-02-17
Thanks for your help.  I was a 5.10 user and just started re-building to 7.10 from scratch.  Got my printers setup, FTP working, Scanner working.  I really like all the update.  I just seemed to have hit a brick wall here for some reason.

---

### Post by jan quark on 2008-02-17
act of desperation :lolflag:

make a backup of your important data and do a fresh install

or wait for some magician who will say click on that and everything is fine:)

---

### Post by splendid on 2008-02-17
Thanks for all your help.

I will wait a couple hours and see if a magician arrives.  Otherwise, I will do a fresh install.

---

