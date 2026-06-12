---
title: "apt-get update errors"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-02-12
Whenever I run apt-get update, I get the following errors at the end. What's wrong?

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde35_dists_breezy_main_binar y-i386_Packages) - stat (2 No such file or directory)

Should I just delete them from sources.list or what. Yesterday, apt-get update was working well, today I get these error. I tried adding extra repositories but those didn't work. I deleted those but still get these errors.
What's wrong.?

:h34r: Jaygo333 :h34r:

---

### Post by Tiede on 2006-02-12
rerun ```
sudo apt-get update
```
If it is not something you modified by hand, it should be fixed automagically (I use gnome so I don't know the kubuntu reps to verify your sources.)

---

### Post by sailor2001 on 2006-02-12
sudo apt-get update && sudo apt-get upgrade

---

### Post by Jaygo333 on 2006-02-12
Tried both. ITs how I'm getting the errors. 
I read somewhere that the us archives have been having troubles. 
Is this true.
I just did apt-get update and my errors changed.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Help

:h34r: Jaygo333 :h34r:

---

### Post by aysiu on 2006-02-12
I just did a *sudo apt-get update* and didn't get any errors.

Please post the output of this command: ```
cat /etc/apt/sources.list
```

---

### Post by grimdaze on 2006-02-12
i'm getting a similar error over here on my ppc

Fetched 191B in 1s (120B/s)
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

i get that when running sudo apt-get update
my results of cat /etc/apt/sources.list

> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)]/ breezy main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy multiverse universe main restricted


Edit: aysiu's first link in sig seems to have fixed my error

---

### Post by savastux on 2006-02-12
Hi all...


Here's mine Synaptic reload result text:

```

http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz: 404 Not Found


``` 
Hope some of you know what's going on...

Thanks in advance,
Savastux

---

### Post by Jaygo333 on 2006-02-12
Here's my cat.sources.list

jaygo333@Ubuntu:~$ sudo cat /etc/apt/sources.list
Password:
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
#Wine
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
#Wine

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main
## created by arniemaxremoved

##FreeNX
deb [http://www.linux.lk/~anuradha/nx/](http://www.linux.lk/~anuradha/nx/) /
deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas freenx
##FreeNX
jaygo333@Ubuntu:~$

Forget the comments around some of them. Reminds me I isntalled them and if causing trouble can delete them easily.

Now what do you want us to do with them?

:h34r: Jaygo333 :h34r:

I hope you know where you area going with this :p

---

### Post by savastux on 2006-02-13
I've got it!

I don't know why, but it seems to be a HTTP repository issue.
I've just changed my repositories to FTP and it just worked.



Thanks anyway!:D

Savastux

---

### Post by Happy Hammer on 2006-02-14
I was suffering from the same problem. I changed all the *archive.ubuntu.com* and *security.ubuntu.com* lines in sources.list to *us.archive.ubuntu.com* and *us.security.ubuntu.com* and ran **apt-get update**.

This gave me errors saying that us.security.blahblahblah couldn't be found so I changed them back to their original values and it sorted it out.

---

### Post by ubunlilluz on 2006-02-14
here we go. My error message:

Get:26 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Sources [1223kB]
83% [26 Sources gzip 0]                                                                                                                     3402B/s 4m28s
gzip: stdin: not in gzip format
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Sources
  Il sottoprocesso gzip ha ritornato un codice d'errore (1)
Scaricato 4391kB in 43m10s (1695B/s)
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Il sottoprocesso gzip ha ritornato un codice d'errore (1)
Lettura della lista dei pacchetti in corso... Fatto
E: Impossibile scaricare alcune file di indice, essi verranno ignorati, oppure si useranno quelli precedenti.
Password:
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
I seguenti pacchetti sono stati mantenuti alla versione attuale:
  linux-image-386 linux-restricted-modules-386
0 aggiornati, 0 installati, 0 da rimuovere e 2 non aggiornati.

so far i've tried the impossible to solve it...:cry: :cry: :cry:

---

### Post by aysiu on 2006-02-14
Forget us.archive.
Forget it.archive.
Go with just archive.

For more details, see the first link of my signature, especially the bottom part.

---

### Post by gmmazlum on 2006-02-14
I can't update from one of my offices... got this errors
[I]apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
  Temporary failure resolving 'packages.freecontrib.org'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg)  Temporary failure resolving 'packages.freecontrib.org'
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

[/I]

I'm gonna  try in other one to see wath happens

---

### Post by aysiu on 2006-02-14
Forget the us.archive repositories.
See the first link of my signature... especially the last part.

---

### Post by Jaygo333 on 2006-02-14
[QUOTE=aysiu]Forget the us.archive repositories.
See the first link of my signature... especially the last part.[/QUOTE]

U sure it can work? 
I don't want to lose everything u know.

:h34r: Jaygo333 :h34r:

---

### Post by ihristov on 2006-02-15
I am getting [COLOR="Red"]BADSIG 40976EAF437D05B5[/COLOR]
```

Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Fetched 191B in 2s (93B/s)
Reading package lists... Done
W: GPG error: http://security.ubuntu.com hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```

Changing [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) to [http://archive.ubuntu.com](http://archive.ubuntu.com) does not help. Still get the same error.

Any ideas?

---

### Post by ihristov on 2006-02-15
[QUOTE=ihristov]I am getting [COLOR="Red"]BADSIG 40976EAF437D05B5[/COLOR]
[/QUOTE]

The solution is the post from **AgenT** at
[http://ubuntuforums.org/showthread.php?t=128602](http://ubuntuforums.org/showthread.php?t=128602)

> 
There's some weird glitch where residual info hangs out and gives you a GPG signature error. If that's the case, do this:

```

# become root
sudo su

# go to apt folder
cd /etc/apt

# Back up current sources.list
cp sources.list sources.list_backup

# make an empty sources.list
> sources.list

# update with your empty repositories list
apt-get update

# revert to saved list
cp sources.list_backup sources.list

# update again and this time you should get no errors
apt-get update 

```


---

### Post by mjfleck2000 on 2006-02-15
After receiving the same gpg errors I tried the suggestion above which worked perfectly.  Thanks




# become root 
sudo su 
# go to apt folder 
cd /etc/apt
 # Back up current sources.list
 cp sources.list sources.list_backup 
# make an empty sources.list
 > sources.list 
# I actually just did "touch sources.list" which also makes an empty file  #named sources.list
# update with your empty repositories list
 apt-get update 
# revert to saved list
 cp sources.list_backup sources.list
 # update again and this time you should get no errors
 apt-get update

---

