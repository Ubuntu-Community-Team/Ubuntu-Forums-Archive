---
title: "Package Update Problems"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Kevin Funnell on 2007-02-02
Good Day One & All,

1.   While I was updating using sudo aptitude Update, ther was apower failure, after powering on again and loging in I could not use the above means of Updating but received the following pop-up:
 Error
The following problems were fould on your system:
E:/var/cache/apt/archives/libgtk2.0-common_22.8.20-0ubuntu1.1_all.deb: subprocess dpkg-deb -- fsys-tarfile returned error exit status 2

2.  I tried to re-install the package(files) by other means and a pop-up said to use Synatic Package Manager or  sudo apt-get install -f, whitch is all double dutch to me.

Could someone please help me to sort out the mess and I thank you in advance.

Old Kevin

---

### Post by empthollow on 2007-02-02
go to applications -> accessories -> terminal  and type ```
sudo apt-get install -f
``` it will automatically fix all broken packages

---

### Post by Kevin Funnell on 2007-02-02
Tried "sudo apt-get install -f  and this is what was displayed

[COLOR="Blue"]Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgtk2.0-common
The following packages will be upgraded:
  libgtk2.0-common
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/3709kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 102530 files and directories currently installed.)
Preparing to replace libgtk2.0-common 2.8.20-0ubuntu1 (using .../libgtk2.0-commo n_2.8.20-0ubuntu1.1_all.deb) ...
Unpacking replacement libgtk2.0-common ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/libgtk2.0-common_2.8.20-0ubuntu1. 1_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libgtk2.0-common_2.8.20-0ubuntu1.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

Old Kevin

---

### Post by psyne on 2007-02-02
After you get that error, try apt-get -f install to force an install of the files that didn't get loaded because of the error. Then try apt-get upgrade again, apt-get -f install back and forth until only the package that has the error is left that is what I read as the resolution to that particular error.

---

### Post by Kevin Funnell on 2007-02-02
Tries the Sudo apt-get install -f and & sudo apt-get upgrade received the following:
 [COLOR="Blue"]sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgtk2.0-common
The following packages will be upgraded:
  libgtk2.0-common
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/3709kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 102530 files and directories currently installed.)
Preparing to replace libgtk2.0-common 2.8.20-0ubuntu1 (using .../libgtk2.0-commo n_2.8.20-0ubuntu1.1_all.deb) ...
Unpacking replacement libgtk2.0-common ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/libgtk2.0-common_2.8.20-0ubuntu1. 1_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libgtk2.0-common_2.8.20-0ubuntu1.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Family:/home/kevin# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libgtk2.0-0: Depends: libgtk2.0-common (>= 2.8.20-0ubuntu1.1) but 2.8.20-0ubun tu1 is installed
E: Unmet dependencies. Try using -f.
[/COLOR]

I am not making heads or tails - do not know what it means!

Old Kevin

---

### Post by psyne on 2007-02-02
Did you remember to update your packages first?

```

sudo aptitude update
sudo aptitude dist-upgrade

```

What is in your source list

```

gedit /etc/apt/sources.list

```

You could also try removing the package. Then reinstalling it.

---

### Post by Kevin Funnell on 2007-02-02
Updated & Upgraded sill same errors.

Source List  below:

[COLOR="Blue"]deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
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

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
## deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
[/COLOR]

Old Kevin

---

### Post by psyne on 2007-02-02
I would try removing it the reinstalling it

```
sudo apt-get remove libgtk2.0-common
```

---

### Post by Archmage on 2007-02-02
How about just deleting the corrupt package? (Although I'm sure that there is a apt-get commando to do this)

```

sudo rm /var/cache/apt/archives/libgtk2.0-common_2.8.20-0ubuntu1.1_all.deb

```

---

### Post by Kevin Funnell on 2007-02-02
Thanks All for Your Help,  after fiddleing around half the night I have now reinsttall Ubuntu from LiveCD as I think this is my best option to fix a number of finger problems. so this Post is Resolved for me.
Old Kevin

---

