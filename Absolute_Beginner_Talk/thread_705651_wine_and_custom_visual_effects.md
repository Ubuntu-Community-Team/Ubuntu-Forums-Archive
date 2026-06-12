---
title: "wine and custom visual effects"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by rhddallas on 2008-02-23
ok...
im trying to install both of them but neither will install at all
when i try to install visual effects i get this

ryan@Ryan-Linux:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
ryan@Ryan-Linux:~$ 

and with wine

ryan@Ryan-Linux:~$ wget -q [http://wine.bugetdedicated/apt/387EE263.gpg-O-](http://wine.bugetdedicated/apt/387EE263.gpg-O-) | sudo apt-key add-
[sudo] password for ryan:
Usage: apt-key [command] [arguments]

Manage apt's list of trusted keys

  apt-key add <file>          - add the key contained in <file> ('-' for stdin)
  apt-key del <keyid>         - remove the key <keyid>
  apt-key update              - update keys using the keyring package
  apt-key list                - list keys

ryan@Ryan-Linux:~$ 

and i try to go farther on wine... even though i fugred it wont work... 

ryan@Ryan-Linux:~$ sudo wget [http://wine.budgetdedicated.com/apt/soucres.list.d/gutsy.list-O/etc/apt/soucres.list.d/winehq.list](http://wine.budgetdedicated.com/apt/soucres.list.d/gutsy.list-O/etc/apt/soucres.list.d/winehq.list)
--15:34:17--  [http://wine.budgetdedicated.com/apt/soucres.list.d/gutsy.list-O/etc/apt/soucres.list.d/winehq.list](http://wine.budgetdedicated.com/apt/soucres.list.d/gutsy.list-O/etc/apt/soucres.list.d/winehq.list)
           => `winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184, 88.159.206.7, 2001:4de0:aaac:0:2456::2
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:34:19 ERROR 404: Not Found.

ryan@Ryan-Linux:~$ 


help please... needed desperately

---

### Post by northern lights on 2008-02-23
Do you have the neccessary repos enabled?

If you dunno what I'm talking about, post the output of```
cat /etc/apt/sources.list
```

---

### Post by rhddallas on 2008-02-24
ryan@Ryan-Linux:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse restricted universe main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
ryan@Ryan-Linux:~$ 


thats what i got when i typed that in

---

### Post by jordanmthomas on 2008-02-24
You need a space after "add" in this command.
```
wget -q http://wine.bugetdedicated/apt/387EE263.gpg-O- | sudo apt-key add -
```

Also, Go to System -- Administration -- Software Sources and enable your repositories.
(A similar effect would be to edit /etc/apt/sources.list and remove the # from the beginning of lines beginning with "deb")

After enabling the repositories, refresh apt's database
```
sudo apt-get update
```

Now, you should be able to install things.

---

### Post by northern lights on 2008-02-25
The above post says it.

If you dunno what to uncomment (where to remove the pounds), make a backup of your current file and open it as root ```
sudo gedit /etc/apt/sources.list
```
and replace yours with```
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by jordanmthomas on 2008-02-25
> **northern lights said:**
> ```
sudo gedit /etc/apt/sources.list
```


Just so you know, you should use gksudo when launching graphical applications.  Otherwise permissions on your own files can get messed up (in particular, .dmrc and .ICEAuthority).

For example, ```
sudo firefox
``` will launch firefox using the USER's themes, bookmarks, preferences, etc.  This means that if a file is created by this process, it will be root's and not the user's.  If you were to use ```
gksudo firefox
``` instead root's preferences would be used.

Using sudo to launch gedit isn't likely to cause problems, and most programs work fine this way, but it's always a good idea to use gksudo instead since there's a chance permissions will be messed up.  Perhaps you've seen people get their .dmrc files get messed up and they can't log in to gnome?  That's usually caused by using sudo instead of gksudo.

I hope I didn't come off as mean or something, I just figure the more you know, the better.  :)

---

### Post by northern lights on 2008-02-25
> **jordanmthomas said:**
> I hope I didn't come off as mean or something, I just figure the more you know, the better.  :)
No offence taken - extending knowledge could never be anything but better indeed.

> **jordanmthomas said:**
> This means that if a file is created by this process, it will be root's and not the user's.
Shouldn't that one be "the user's and not the root's" --> Then this would make more sense to me (if it's not a typo, but what you meant to say, please explain further)...

---

### Post by jordanmthomas on 2008-02-25
You can read up a little more on it here.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

The problem is that user files are created but are owned by root.  It's a little confusing, yes.  Say firefox has a file called preferences.conf (it doesn't, but bear with me).    If this file wasn't there before the user ran 
```
sudo firefox
```
Firefox would create this file and fill it with defaults.  It would put this file in your user's directory, not root's.  This file would be owned by root, and possibly could only be read by root.  Later, when the user tries to run firefox, it can't read its configuration file and annoyances ensue.  

Do you see what I mean?  The file is FOR the user, but it's not the user's file.

---

### Post by northern lights on 2008-02-25
Aight, got it. Makes sense.

I have a "gksu gnome-terminal" launcher and thus hardly ever use sudo for root work, but will now more deliberatelysee to use either that or "gksudo" from regular terminal.

Thanks mate.

---

### Post by rhddallas on 2008-02-25
wow ok...
lol little over my head but ill try it when i get home..
im on my laptop running XP at school right now... my desktop is the one running ubuntu
so yea... thanks for the help yall... ill tell u what i come up with when i get home

---

### Post by jordanmthomas on 2008-02-25
If you get confused anywhere post back and someone can explain things further if needed.

---

