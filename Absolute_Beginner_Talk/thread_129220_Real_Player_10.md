---
title: "Real Player 10"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by carverj on 2006-02-13
hifellow ooboo's
just trying to install my chmoded realplayer10.bin and as you can see there is some problem/conflict??

jeremy@UBUNTU:~$ cd /home/jeremy/download
jeremy@UBUNTU:~/download$ ls -l
total 5720
-rw-r--r--  1 jeremy jeremy   31963 2006-02-10 21:46 Metallica+-+Kill+%27Em+All.torrent
-rw-r--r--  1 jeremy jeremy   19071 2006-02-13 18:54 NBAActionweek14060211([www.fulldls.com).torrent](www.fulldls.com).torrent)
-rwxr-xr-x  1 jeremy jeremy 5789348 2006-02-13 22:50 RealPlayer10GOLD.bin
jeremy@UBUNTU:~/download$ ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

is ./RealPlayer10GOLD.bin the correct command to install here? 
and if so, is there something I have missed?

Thanks guys and gals

---

### Post by Perfect Storm on 2006-02-13
This way is better:

```
 sudo gedit /etc/apt/sources.list 
```

add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]


```
sudo apt-get update
sudo apt-get install realplay
```

---

### Post by Perfect Storm on 2006-02-13
[QUOTE=carverj]hifellow ooboo's
just trying to install my chmoded realplayer10.bin and as you can see there is some problem/conflict??

jeremy@UBUNTU:~$ cd /home/jeremy/download
jeremy@UBUNTU:~/download$ ls -l
total 5720
-rw-r--r--  1 jeremy jeremy   31963 2006-02-10 21:46 Metallica+-+Kill+%27Em+All.torrent
-rw-r--r--  1 jeremy jeremy   19071 2006-02-13 18:54 NBAActionweek14060211([www.fulldls.com).torrent](www.fulldls.com).torrent)
-rwxr-xr-x  1 jeremy jeremy 5789348 2006-02-13 22:50 RealPlayer10GOLD.bin
jeremy@UBUNTU:~/download$ ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

is ./RealPlayer10GOLD.bin the correct command to install here? 
and if so, is there something I have missed?

Thanks guys and gals[/QUOTE]

```
sudo apt-get install libstdc++5
```

Then try again.

---

### Post by gingermark on 2006-02-13
EDIT: Beaten to the punch by A.I.

---

### Post by carverj on 2006-02-15
well, managed to download realplayer, but there is a problem. It's  (real player) saying that some components are missing (such as video/X-RN-QT-RAWAU
audio/X-RN-QT-RAWAU when I try to open a .mov file)

I'll start from the beginning. I recently edited source.list with the repositories suggested by A.I in a recent post I came across.

jeremy@UBUNTU:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
jeremy@UBUNTU:~$ sudo apt-get update
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/restricted Sources
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release
Get:2 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:3 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release.gpg
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-backports Release
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy Release
Ign [http://download.skype.com](http://download.skype.com) stable Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy-updates Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-backports/main Packages
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-backports/main Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-backports/multiverse Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
  404 Not Found
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy/restricted Packages
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy/main Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
  404 Not Found
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
  404 Not Found
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy/universe Packages
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy/universe Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
  404 Not Found
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Fetched 6B in 13s (0B/s)
Failed to fetch [http://antesis.freecontrib.org/mirro.../devnotpublic/dists/breezy/free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirro.../devnotpublic/dists/breezy/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://antesis.freecontrib.org/mirro.../devnotpublic/dists/breezy/non-free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirro.../devnotpublic/dists/breezy/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://antesis.freecontrib.org/mirro.../devnotpublic/dists/breezy/free/source/Sources.gz](http://antesis.freecontrib.org/mirro.../devnotpublic/dists/breezy/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://antesis.freecontrib.org/mirro.../devnotpublic/dists/breezy/non-free/source/Sources.gz](http://antesis.freecontrib.org/mirro.../devnotpublic/dists/breezy/non-free/source/Sources.gz)  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

When I followed the apt-get install realplayer advice (see A.I's reply above), it seemed to have a problem accessing the antesis site above also!

Also, took a look at the source list generator. Was put off using it by the warning about don't use this unless your 100% sure you know what you are doing. Is it really dangerous to use, and if not, how do I find out my key ID to enter the key translation command?

Still having a great time using UBUNTU and it's been a good year or more since I first installed Linux!! If Vista is really as resource hungry and average as my classmate told me, perhaps we'll see many more Linux converts like myself in the very near future!
:) 
Ta very much guys and gals.

---

### Post by Perfect Storm on 2006-02-15
You can leave out:

deb [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free

It's more for testing new stuff for PLF.

Did you choose realplay or realplayer?
Your sourcelist?
Also post the errorlist when apt-get realplay.

---

### Post by carverj on 2006-02-15
OK, first of all thanks for the instant support. Appreciate it as ever!!!!!

changed the privileges as you can see, but cannot remove the lines and save. 
error message: Could not save the file "/etc/apt/sources.list"



jeremy@UBUNTU:/etc/apt$ ls -l
total 28
drwxr-xr-x  2 root root 4096 2006-01-29 23:29 apt.conf.d
-rw-------  1 root root    0 2006-01-29 22:37 secring.gpg
-rwxrwxrwx  1 root root 2704 2006-02-15 17:18 sources.list
-rwxrwxrwx  1 root root 1891 2006-01-30 16:32 sources.list~
-rw-r--r--  1 root root 1801 2006-01-30 16:32 sources.list.save
-rw-------  1 root root 1200 2006-01-29 22:37 trustdb.gpg
-rw-r--r--  1 root root 2393 2006-01-29 22:37 trusted.gpg
-rw-r--r--  1 root root 2381 2006-01-29 22:37 trusted.gpg~
jeremy@UBUNTU:/etc/apt$ sudo gedit /etc/apt/souces.list
jeremy@UBUNTU:/etc/apt$ sudo gedit /etc/apt/souces.list~

I chose realplay and this is whats happening

jeremy@UBUNTU:/etc/apt$ sudo apt-get install realplay
Reading package lists... Done
Building dependency tree... Done
realplay is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

---

### Post by carverj on 2006-02-15
Is there any other way of playing rm files with other media players?

---

### Post by Perfect Storm on 2006-02-16
Hmmm...lets try making a new sourcelist for you. Firstly removing the old one.

```
cd  /etc/apt
sudo rm -r sources.list
sudo gedit /etc/apt/sources.list

```

add:

> 
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

##backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

## Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free


Click the save button. 
Back to the terminal:

```
sudo apt-get update
sudo apt-get install realplay
```

---

### Post by carverj on 2006-02-16
ok, want the good news or the ... ?
am able to play .rm files with totem and xine after running the automatix script!!
went to change sources.list as mentioned above and found it has been changed

jeremy@UBUNTU:/etc/apt$ ls -l
total 80
drwxr-xr-x  2 root root  4096 2006-01-29 23:29 apt.conf.d
-rw-------  1 root root     0 2006-01-29 22:37 secring.gpg
-rw-r--r--  1 root root  2250 2006-02-15 22:30 sources.list
-rwxrwxrwx  1 root root  2704 2006-02-15 17:18 sources.list~
-rwxrwxrwx  1 root root  2529 2006-02-15 20:45 sources.list~~
-rwxrwxrwx  1 root root  2529 2006-02-15 20:48 sources.list_backup_200602152230
-rwxr-xr-x  1 root root  2529 2006-02-15 22:30 sources.list_backup_arnie
-rw-r--r--  1 root root  1801 2006-01-30 16:32 sources.list.save
-rw-------  1 root root  1200 2006-02-15 22:30 trustdb.gpg
-rw-r--r--  1 root root 22647 2006-02-15 22:30 trusted.gpg
-rw-r--r--  1 root root 22647 2006-02-15 22:30 trusted.gpg~

Does the above advice still apply in this case to troubleshoot realplayer installation ?
Thanks very much

---

### Post by Perfect Storm on 2006-02-16
Well, if you used automatix you might backup the sourcelist before you proceed. Better save than sorry ;)

> Does the above advice still apply in this case to troubleshoot realplayer installation ?
Thanks very much

Yes, but before you proceed check if automatix provided the source to realplay:

```
sudo apt-get install realplay
```

---

### Post by arnieboy on 2006-02-16
[QUOTE=Artificial Intelligence]Well, if you used automatix you might backup the sourcelist before you proceed. Better save than sorry ;)[/QUOTE]
a quick update on this note:
Automatix backs up sources.list automatically before doing anything and at the end of all installations, gives the user the option to restore his/her original sources.list. 

EDIT: misread your statement. my apologies.
-Arnie

---

### Post by Perfect Storm on 2006-02-16
If you read my comment carefully, you'll see it was comment on if he wants to change the sourcelist after using automatix with the one I posted so if the sourcelist I gave him failed he could get back on the one automatix provided.

---

### Post by arnieboy on 2006-02-16
alright my bad.. my apologies for having misread your statement.. 

one more comment though. 
1) You should try to avoid suggesting danish repositories to users who are not in or near denmark because it might result in a radical slowdown of updates and downloads.

---

### Post by Perfect Storm on 2006-02-16
It's okay ^^

1. aye, I miss that one, happens sometimes when cut'n'paste from my source list.

---

