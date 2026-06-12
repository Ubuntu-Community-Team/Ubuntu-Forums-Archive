---
title: "Problem with automatix2"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by hacklab on 2007-09-23
[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.12-7.04feisty_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.12-7.04feisty_i386.deb)

Im trying to install automatix with debi package installer.

when I try to run the *.deb file nothing happens?

What to do?

---

### Post by kellemes on 2007-09-23
[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

Edit: If you need to go graphically, get **gdebi**.

---

### Post by oilchangeguy on 2007-09-23
never mind. i had the same link as the op.
but you should be presented with a box asking if you want to open the file. click yes.

---

### Post by asmoore82 on 2007-09-23
Automatix is bad: [http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

You may want to check out this thread:
[**Sticky:**  Supported Installation Alternatives to Automatix]("http://ubuntuforums.org/showthread.php?t=519872")

If you read the fine print on their webpage, *even* Automatix's coders
**don't** recommend using it for 3D graphics drivers.

---

### Post by hacklab on 2007-09-23
roko@linux:~$ cd Desktop
roko@linux:~/Desktop$ dir
automatix2_1.1-4.12-7.04feisty_i386.deb  pidgin-2.2.0.tar.bz2
roko@linux:~/Desktop$ 
roko@linux:~/Desktop$ sudo dpkg -i automatix2_1.1-4.12-7.04feisty_i386.deb
Password:
Selecting previously deselected package automatix2.
(Reading database ... 88146 files and directories currently installed.)
Unpacking automatix2 (from automatix2_1.1-4.12-7.04feisty_i386.deb) ...
dpkg: dependency problems prevent configuration of automatix2:
 automatix2 depends on python2.4; however:
  Package python2.4 is not installed.
dpkg: error processing automatix2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 automatix2
roko@linux:~/Desktop$ 

Whats wrong?

---

### Post by FuturePilot on 2007-09-23
```
sudo apt-get install -f
```

---

### Post by por100pre1 on 2007-09-23
There's no need to use Automatix. For codecs do [this]("http://ubuntuforums.org/showthread.php?t=413624"). For anything else let us know.

---

### Post by hacklab on 2007-09-23
Again a problem:

roko@linux:~/Desktop$ sudo apt-get install -f
E: Type '“deb' is not known on line 44 in source list /etc/apt/sources.list
E: The list of sources could not be read.
roko@linux:~/Desktop$

What to do?

---

### Post by por100pre1 on 2007-09-23
```
cat /etc/apt/sources.list
```

Post the results...

**EDIT: I remember when Automatix messed up my sources.list**

---

### Post by Maestro23 on 2007-09-23
> **hacklab said:**
> Again a problem:

roko@linux:~/Desktop$ sudo apt-get install -f
E: Type '“deb' is not known on line 44 in source list /etc/apt/sources.list
E: The list of sources could not be read.
roko@linux:~/Desktop$

What to do?


Your sources.list file is incorrect.  Type the following in terminal and copy/paste the output here:

> cat /etc/apt/sources.list (lower case L)

---

### Post by hacklab on 2007-09-23
roko@linux:~/Desktop$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
1234






12343









11234324
roko@linux:~/Desktop$

---

### Post by runemaste644 on 2007-09-23
Automatix always ends up breaking systems. Save yourself while you can!

---

### Post by Maestro23 on 2007-09-23
Delete the **"** from the beginning of the following line.

> **“**deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”

To edit it:

> gksudo gedit /etc/apt/sources.list

Make the change and save the file.

---

### Post by por100pre1 on 2007-09-23
> **hacklab said:**
> roko@linux:~/Desktop$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
[COLOR="Red"]&#8220;[/COLOR]deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main[COLOR="Red"]&#8221;[/COLOR]
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
1234






12343

11234324
roko@linux:~/Desktop$

```
sudo gedit /etc/apt/sources.list
```

and remove the characters shown in red.
[SIZE="3"]
[COLOR="Red"]**Automatix did it again!!!**[/COLOR][/SIZE]

---

### Post by runemaste644 on 2007-09-23
Again, Automatix will break your system!

---

### Post by por100pre1 on 2007-09-23
To the OP: remove Automatix before it's too late!

---

### Post by w4ett on 2007-09-23
Might I suggest the the OP direct his Automatix support questions to the appropriate place:
> 
[http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/)

This is the Automatix support forum link....The developers of automatix have asked that all support questions for their application be directed to their forums.  ):P

---

### Post by por100pre1 on 2007-09-23
IMHO, the OP will do better by removing Automatix now.

---

