---
title: "Problems upgrading from CD (Edgy to Fiesty)"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by fez on 2007-04-26
I tried:

```
gksu sh /cdrom/cdromupgrade
```

Which didn't give any messages or confirmations. So then I was about to try:

```
sudo apt-cdrom add

sudo apt-get update

sudo apt-get dist-upgrade 
```

The first command was fine, but I got this output after the second:

```
$ sudo apt-get update
Errhttp://gb.archive.ubuntu.com edgy Release.gpg
  Temporary failure resolving ‘gb.archive.ubuntu.com’
Errhttp://gb.archive.ubuntu.com edgy/main Translation-en_GB
  Temporary failure resolving ‘gb.archive.ubuntu.com’
Errhttp://gb.archive.ubuntu.com edgy/restricted Translation-en_GB
  Temporary failure resolving ‘gb.archive.ubuntu.com’
Errhttp://gb.archive.ubuntu.com edgy/universe Translation-en_GB
  Temporary failure resolving ‘gb.archive.ubuntu.com’
Errhttp://gb.archive.ubuntu.com edgy-updates Release.gpg
  Temporary failure resolving ‘gb.archive.ubuntu.com’
Errhttp://gb.archive.ubuntu.com edgy-updates/main Translation-en_GB
  Temporary failure resolving ‘gb.archive.ubuntu.com’
Errhttp://gb.archive.ubuntu.com edgy-updates/restricted Translation-en_GB
  Temporary failure resolving ‘gb.archive.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security Release.gpg
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/main Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/restricted Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_GB
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_GB
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_GB
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_GB
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg  Temporary failure resolving ‘gb.archive.ubuntu.com’
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘gb.archive.ubuntu.com’
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘gb.archive.ubuntu.com’
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘gb.archive.ubuntu.com’
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg  Temporary failure resolving ‘gb.archive.ubuntu.com’
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘gb.archive.ubuntu.com’
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘gb.archive.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

I am really new to Linux/Ubuntu and haven't been able to get my network card working under any of the previous versions, so I've got no internet access (which is why I need to upgrade using CD).

Anyone know what I'm doing wrong?

---

### Post by diskotek on 2007-04-27
in the forum there are many threads toward upgrading to feisty from edgy. and i think it's not so safe to do. i think clean install would be better. just an opinion...

by the way this error sounds like connection error to server. and you are trying to upgrade via servers as i see. you should double check forum about upgrading from cd. you should add cd to your repo list. 

system / administration / package sources or software sources (i translated it from turkish :)

---

### Post by zvacet on 2007-04-27
You didn´t run proper command
```
gksu "sh /cdrom/cdromupgrade" 
```


And it should be alternate Cd to do upgrade from.

---

### Post by fez on 2007-04-30
Thank you for your help. I am now posting from Ubuntu after many months of trying, and failing, to install Linux!

:guitar:

---

