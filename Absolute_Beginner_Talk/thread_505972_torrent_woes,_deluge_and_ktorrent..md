---
title: "torrent woes, deluge and ktorrent."
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by natakim on 2007-07-21
having problems with both torrent clients, neither will open. tried various methods to re-install but with no joy. currently i can't even open synaptic packet manager. i get this error. what can i do?

any idea, please.

cheers

---

### Post by geist27 on 2007-07-21
Hmm, interesting, I saw someone else having the same problem with their virtualbox .deb install, have you tried:

```
$ sudo apt-get update
```will update your repos

```
$ sudo apt-get upgrade
```will update your system to see if you have a dependency problem

```
$ sudo apt-get check
```will check for missing dependencies

```
$ sudo apt-get clean
```will clean your /tmp I believe if uneeded debs lying around

```
$ sudo apt-get remove ktorrent
```as a last resort will remove ktorrent and you can reinstall it and hope for the best

I am using ktorrent now with Feisty and not having any probs

---

### Post by natakim on 2007-07-21
> **geist27 said:**
> Hmm, interesting, I saw someone else having the same problem with their virtualbox .deb install, have you tried:

```
$ sudo apt-get update
```will update your repos

```
$ sudo apt-get upgrade
```will update your system to see if you have a dependency problem

```
$ sudo apt-get check
```will check for missing dependencies

```
$ sudo apt-get clean
```will clean your /tmp I believe if uneeded debs lying around

```
$ sudo apt-get remove ktorrent
```as a last resort will remove ktorrent and you can reinstall it and hope for the best

I am using ktorrent now with Feisty and not having any probs



thanks i'll give it a try.
cheers

---

### Post by corevette on 2007-07-21
If it still doesn't work, first give us the error with Synaptic.  After, go to Applications >> Accessories >> Terminal and type in 'ktorrent' or 'deluge' (without quotes of course).  Tell/paste us what it says or the output in this forum.

---

### Post by natakim on 2007-07-21
ok it appears that it's deluge that's the problem. how do i uninstall it completely?

> natakim@natakim-desktop:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package deluge-torrent needs to be reinstalled, but I can't find an archive for it.


---

### Post by natakim on 2007-07-21
> **corevette said:**
> If it still doesn't work, first give us the error with Synaptic.  After, go to Applications >> Accessories >> Terminal and type in 'ktorrent' or 'deluge' (without quotes of course).  Tell/paste us what it says or the output in this forum.


yikes...

> natakim@natakim-desktop:~$ deluge
Traceback (most recent call last):
  File "/usr/bin/deluge", line 58, in <module>
    import deluge
ImportError: No module named deluge
natakim@natakim-desktop:~$ 


after ktorrent in terminal, it shows in system monitor but nothing launches on desktop. only cache cleaner then nothing

> natakim@natakim-desktop:~$ ktorrent
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
natakim@natakim-desktop:~$ kio_http_cache_cleaner: Already running! (kio_http_cache_cleaner-2)


---

### Post by natakim on 2007-07-21
ok, i tried to remove both using

sudo apt-get remove 'torrent client'

got this again

> natakim@natakim-desktop:~$ sudo apt-get remove deluge
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package deluge-torrent needs to be reinstalled, but I can't find an archive for it.
natakim@natakim-desktop:~$ sudo apt-get remove ktorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package deluge-torrent needs to be reinstalled, but I can't find an archive for it.
natakim@natakim-desktop:~$ 


---

### Post by forestpixie on 2007-07-21
try to purge it 

```

sudo apt-get --purge remove deluge
```

---

### Post by natakim on 2007-07-21
> **forestpixie said:**
> try to purge it 

```

sudo apt-get --purge remove deluge
```

still getting same message?

> natakim@natakim-desktop:~$ sudo apt-get --purge remove deluge
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package deluge-torrent needs to be reinstalled, but I can't find an archive for it.
natakim@natakim-desktop:~$ 

is this a problem?

---

### Post by forestpixie on 2007-07-21
try reinstalling it and then removing it

sudo apt-get install deluge

sudo apt-get --purge -remove deluge

---

### Post by natakim on 2007-07-21
> **forestpixie said:**
> try reinstalling it and then removing it

sudo apt-get install deluge

sudo apt-get --purge -remove deluge


stilling getting same message, crap (scratches head). :(

> natakim@natakim-desktop:~$ sudo apt-get install deluge
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package deluge-torrent needs to be reinstalled, but I can't find an archive for it.
natakim@natakim-desktop:~$ sudo apt-get --purge -remove deluge
E: Command line option 'r' [from -remove] is not known.
natakim@natakim-desktop:~$ sudo apt-get --purge remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package deluge-torrent needs to be reinstalled, but I can't find an archive for it.
natakim@natakim-desktop:~$ 

---

### Post by davidjmayo on 2007-07-21
> E: The package **deluge-torrent **needs to be reinstalled, but I can't find an archive for it.
natakim@natakim-desktop:~$

Try all the above advice with deluge-torrent instead of deluge

---

### Post by forestpixie on 2007-07-21
whoops :oops:

---

### Post by natakim on 2007-07-21
> **davidjmayo said:**
> Try all the above advice with deluge-torrent instead of deluge

yikes...


> natakim@natakim-desktop:~$ sudo apt-get install deluge-torrent
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package deluge-torrent needs to be reinstalled, but I can't find an archive for it.
natakim@natakim-desktop:~$ sudo apt-get --purge remove deluge-torrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package deluge-torrent needs to be reinstalled, but I can't find an archive for it.
natakim@natakim-desktop:~$  

:confused:

---

### Post by avik on 2007-07-21
Can you post your /etc/apt/sources.list file please?

---

### Post by forestpixie on 2007-07-21
try to purge deluge-torrent this time :)

sudo apt-get --purge -remove deluge-torrent

edit - oh you'd done it sorry

---

### Post by forestpixie on 2007-07-21
I used this command once or twice to get rid of really stubborn stains

dpkg --remove --force-remove-reinstreq deluge-torrent

and then you should be able to reinstall it

---

### Post by natakim on 2007-07-21
> **forestpixie said:**
> try to purge deluge-torrent this time :)

sudo apt-get --purge -remove deluge-torrent

edit - oh you'd done it sorry

no joy...

> natakim@natakim-desktop:~$ sudo apt-get --purge -remove deluge
E: Command line option 'r' [from -remove] is not known.
natakim@natakim-desktop:~$ sudo apt-get --purge remove deluge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package deluge-torrent needs to be reinstalled, but I can't find an archive for it.
natakim@natakim-desktop:~$ sudo apt-get --purge remove deluge-torrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package deluge-torrent needs to be reinstalled, but I can't find an archive for it.
natakim@natakim-desktop:~$ 

---

### Post by natakim on 2007-07-21
> **forestpixie said:**
> I used this command once or twice to get rid of really stubborn stains

dpkg --remove --force-remove-reinstreq deluge-torrent

and then you should be able to reinstall it

that did something different...

> natakim@natakim-desktop:~$ dpkg --remove --force-remove-reinstreq deluge-torrentdpkg: requested operation requires superuser privilege
natakim@natakim-desktop:~$ sudo dpkg --remove --force-remove-reinstreq deluge-torrent
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 137961 files and directories currently installed.)
Removing deluge-torrent ...


:)

---

### Post by natakim on 2007-07-21
> **avik said:**
> Can you post your /etc/apt/sources.list file please?

sorry not sure how to locate this.

---

### Post by natakim on 2007-07-21
> **forestpixie said:**
> I used this command once or twice to get rid of really stubborn stains

dpkg --remove --force-remove-reinstreq deluge-torrent

and then you should be able to reinstall it

bingo i can open synaptic pac man now. i'll try re-install.


worked, god i love this forum, you people are soooo helpful and patient, much appreciated.

thanks again:):):)

---

### Post by forestpixie on 2007-07-21
if you needed to post the contents of a file like the sources list

```
cat /etc/apt/sources.list
```

would do it

---

### Post by forestpixie on 2007-07-21
excellent glad your there - sorry for the deluge/deluge-torrent confusion :)

---

### Post by natakim on 2007-07-21
> **forestpixie said:**
> if you needed to post the contents of a file like the sources list

```
cat /etc/apt/sources.list
```

would do it

cheers, good to know.

like thus then...

> natakim@natakim-desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
natakim@natakim-desktop:~$ 

---

### Post by natakim on 2007-07-21
> **forestpixie said:**
> excellent glad your there - sorry for the deluge/deluge-torrent confusion :)

thank you...

:KS

---

### Post by avik on 2007-07-22
I can't guarantee this will work, but let's try something.  Open up your sources.list file as root:

```
gksudo gedit /etc/apt/sources.list
```

You see the section in that file between "AUTOMATIX REPOS START" and "AUTOMATIX REPOS END?"  Comment out all the lines in that section by putting a # sign at the beginning of each line.  Save the file and exit gedit.

Now do:

```
sudo apt-get update
```

Now try the advice in this thread.

If that doesn't work, you can always uncomment the lines you commented before.

---

