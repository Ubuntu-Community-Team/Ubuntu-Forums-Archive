---
title: "Using Wine"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by WarAngel on 2006-02-11
I am using the Wine distro which is available through Synaptic. However, when I try to run wine, I get the following error:

```

chandlerm@chandlerm:~$ wine
wine: creating configuration directory '/home/chandlerm/.wine'...
Unknown option '-w'

usage: wineserver [options]

options:
   -d<n>  set debug level to <n>
   -p     make server persistent
   -h     display this help message
   -s     server will use shared memory where possible rather than pipe communication
   -f     server will will not run as daemon

wine: wineprefixcreate failed while creating '/home/chandlerm/.wine'.
chandlerm@chandlerm:~$ wineserver: could not save registry branch to /home/chandlerm/.wine-Z0Jk0b/system.reg : No such file or directory
wineserver: could not save registry branch to /home/chandlerm/.wine-Z0Jk0b/userdef.reg : No such file or directory
wineserver: could not save registry branch to /home/chandlerm/.wine-Z0Jk0b/user.reg : No such file or directory

```

If anyone could please help me, I would be appreciative!

---

### Post by o_fortuna on 2006-02-11
[QUOTE=WarAngel]I am using the Wine distro which is available through Synaptic. However, when I try to run wine, I get the following error:

```

chandlerm@chandlerm:~$ wine
wine: creating configuration directory '/home/chandlerm/.wine'...
Unknown option '-w'

usage: wineserver [options]

options:
   -d<n>  set debug level to <n>
   -p     make server persistent
   -h     display this help message
   -s     server will use shared memory where possible rather than pipe communication
   -f     server will will not run as daemon

wine: wineprefixcreate failed while creating '/home/chandlerm/.wine'.
chandlerm@chandlerm:~$ wineserver: could not save registry branch to /home/chandlerm/.wine-Z0Jk0b/system.reg : No such file or directory
wineserver: could not save registry branch to /home/chandlerm/.wine-Z0Jk0b/userdef.reg : No such file or directory
wineserver: could not save registry branch to /home/chandlerm/.wine-Z0Jk0b/user.reg : No such file or directory

```

If anyone could please help me, I would be appreciative![/QUOTE]
You normally need to have something set up wine, like winesetuptk. However, I'd highly recommend that you get the newest Wine - just go into settings, click repositories, add, and custom, and copy this line in:
```
deb http://wine.sourceforge.net/apt binary/
```
Or, better yet, use [Automatix.]("http://ubuntuforums.org/showthread.php?t=66563")
Just tell it to install wine. The newer Wine has wineconfig, which will automatically make everything work. Also, the new Wine is better, it has installed stuff a lot better for me.

---

### Post by WarAngel on 2006-02-11
I used both methods you gave and neither of them worked. I still get the exact same error. I appreciate your help anyway though.

Does anyone else have any idea as to what is wrong?

---

### Post by patrick295767 on 2006-02-12
Normally u install wine with : 

```
apt-get -f -y install wine
```
  
with such sources.list breezy :
in /etc/apt/sources.list

Also, the Crossover Weager has a very good version of wine to install windwos programs
in /opt/cxoffice/bin
But, that 's for microsoft office mainly
(and u have to pay for it, or  know someome to get it or search... )

Greetz

Pat'

```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## breezy-extras
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secundairy repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secundairy are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
## deb http://wine.sourceforge.net/apt/ binary/

## opera web browser
## deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./

deb http://www.kadu.net/download/binary/ubuntu/repo breezy main


```

---

