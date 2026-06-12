---
title: "problem while installing limewire"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by alket on 2007-05-09
[COLOR="Red"]error : dependency is not satisfiable: libc6[/COLOR]

---

### Post by Terl on 2007-05-09
> **babaroga said:**
> [COLOR="Red"]error : dependency is not satisfiable: libc6[/COLOR]

libc6 is available through synaptic.

---

### Post by alket on 2007-05-09
but still isnt working

---

### Post by Happy_Man on 2007-05-09
```
sudo apt-get install libc6
```

---

### Post by alket on 2007-05-09
i tryed and that but still not working please help

---

### Post by alket on 2007-05-09
???????????????????????????? pls hlp

---

### Post by Happy_Man on 2007-05-11
Can you post the output of 
```
cat /etc/fstab
```

for us please?

---

### Post by madman1337 on 2007-05-13
I am having the same issue with installing limewire. Here is a post from the terminal:

```
madman1337@madman1337-desktop:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
madman1337@madman1337-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by Happy_Man on 2007-05-13
Damn...didn't realize I posted the wrong command! :razz:

Try ```
cat /etc/apt/sources.list
``` 
instead. Sorry!

---

### Post by madman1337 on 2007-05-13
here is what comes up.

```
madman1337@madman1337-desktop:~$ cat /etc/apt/sources.list

deb http://mx.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mx.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://mx.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://mx.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mx.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://mx.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

---

### Post by Happy_Man on 2007-05-13
Enter ```
sudo gedit /etc/apt/sources.list
```

and wherever you see a line that has ONE # symbol in front, delete the # symbol. Nothing else. If there are two, leave it. Then save, and restart the package manager.

After that, try to install.

---

### Post by wastedfluid on 2007-05-25
> **Happy_Man said:**
> Enter ```
sudo gedit /etc/apt/sources.list
```

and wherever you see a line that has ONE # symbol in front, delete the # symbol. Nothing else. If there are two, leave it. Then save, and restart the package manager.

After that, try to install.

I'm having the exact same problems.  I did what you said; i re-installed every libc6 package except for the 64-bit editions.  Still get the same error.

---

### Post by Panzor on 2007-05-25
You guys need to use Frostwire. It's identical, but it linux-morefriendly XD.

---

### Post by wastedfluid on 2007-05-25
> **Panzor said:**
> You guys need to use Frostwire. It's identical, but it linux-morefriendly XD.


I can't use Frostwire.

It lets you choose a port to forward on(I have ports 4000, and 4500 open for P2P - I use this on Windows, and it works) - but it DOESN'T let you put in a manual IP address.

The configuration screen shows "Ath0 - 192.168.2.1" and "lo" 

This will not work.  I need to be able to manually edit that IP to my real IP.  I cannot download anything off Frostwire, which is why I was going to attempt to use Limewire.

I just want a P2P rpogram that lets you configure your ip address, and port forwarding.  I'm behind a wireless router.. and my IP always shows up as "192.168.2.1" and it needs to be my Comcast one.

:(

See this picture:

[http://www.jbodystreet.com/screenshot3.png](http://www.jbodystreet.com/screenshot3.png)

You see?  I need to be able to edit that.  and I can't.  >:|

---

### Post by Happy_Man on 2007-05-26
Azureus FTW!

---

### Post by wastedfluid on 2007-05-26
Azureus is BitTorrent.  I like P2P better for individual songs.

---

### Post by invizibility on 2007-06-10
I have the exact same problem but I believe the problem is due to versioning. This is what I have

```
Package: libc6
Status: install ok installed
Priority: required
Section: libs
Installed-Size: 9932
Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Architecture: i386
Source: glibc
Version: 2.3.6-0ubuntu20.4
```

And LimeWire needs a higher version of libc6 which synaptic doesn't provide. Is there a way to get around this?

Appreciate all the help.

---

### Post by akshayas1986 on 2007-06-12
Do not at any cost try to mess around with libc6 or libc6-dev. Dont try to manually upgrade it or downgrade it. Ubuntu uses these libraries for everything even command prompt. So what if you cant install limewire- its better than crashing the system

---

### Post by Malibu Illusion on 2007-06-12
Don't install LimeWire via the .deb package - grab the 'other' package [here](http://www.limewire.com/download/download.php?version=other), extract it and execute by issuing:

```
sh runLime.sh
```

It should work providing you have a suitable JRE installed.

---

