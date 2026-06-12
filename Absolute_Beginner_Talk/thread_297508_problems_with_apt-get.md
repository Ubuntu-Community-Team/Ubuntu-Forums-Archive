---
title: "problems with apt-get"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by flajus on 2006-11-11
please sombody help me when i try to use apt-get i always get this error:
............
Reading package lists... Error!
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
............

What i need to do? please somebody help;)

---

### Post by taurus on 2006-11-11
Can you paste your /etc/apt/sources.list here?  Open a terminal, Applications -> Accessories -> Terminal, and type

```
cat /etc/apt/sources.list
```

---

### Post by loclei on 2006-11-11
> **taurus said:**
> Can you paste your /etc/apt/sources.list here?  Open a terminal, Applications -> Accessories -> Terminal, and type

```
cat /etc/apt/sources.list
```

i have problems with apt-get too ..
```

user@user-desktop:~$ sudo apt-get update
Errhttp://security.ubuntu.com edgy-security Release.gpg
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/main Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/restricted Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/multiverse Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/restricted Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/main Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/multiverse Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/universe Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://archive.ubuntu.com edgy Release.gpg
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy/main Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy/restricted Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy/multiverse Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy/universe Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy-updates Release.gpg
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy-updates/main Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy-updates/restricted Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy-updates/multiverse Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```
 when i do the command you said i get:
```

user@user-desktop:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://security.ubuntu.com/ubuntu/ edgy-security restricted main multiverse universe


```

---

### Post by taurus on 2006-11-11
> **loclei said:**
> i have problems with apt-get too ..
```

user@user-desktop:~$ sudo apt-get update
Errhttp://security.ubuntu.com edgy-security Release.gpg
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/main Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/restricted Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/multiverse Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/restricted Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/main Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/multiverse Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/universe Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://archive.ubuntu.com edgy Release.gpg
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy/main Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy/restricted Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy/multiverse Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy/universe Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy-updates Release.gpg
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy-updates/main Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy-updates/restricted Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy-updates/multiverse Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_GB.bz2  Temporary failure resolving ‘security.ubuntu.com’
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```
 when i do the command you said i get:
```

user@user-desktop:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://security.ubuntu.com/ubuntu/ edgy-security restricted main multiverse universe


```

Is your network connection working at all?

---

### Post by loclei on 2006-11-11
yes it does

but i'm behind a proxy which looks like ip : port

---

### Post by taurus on 2006-11-11
> **loclei said:**
> 
but i'm behind a proxy which looks like ip : port
That's your problem right there, proxy!!!  Did apt-get work before or is this the first time you run "sudo apt-get update"?

---

### Post by loclei on 2006-11-11
i tried many times this but with same results
how to set the proxy for this??
or if possible to set a proxy for all programs that use internet connection
thx

---

### Post by taurus on 2006-11-11
Okay, here are a few links from google...

[http://www.ubuntuforums.org/showthread.php?t=281874](http://www.ubuntuforums.org/showthread.php?t=281874)
[http://www.ubuntuforums.org/showthread.php?p=1722157](http://www.ubuntuforums.org/showthread.php?p=1722157)
[http://linux.ncl.ac.uk/proxy/](http://linux.ncl.ac.uk/proxy/)
[http://tldp.org/HOWTO/TransparentProxy-4.html](http://tldp.org/HOWTO/TransparentProxy-4.html)
[http://www.linuxjournal.com/article/6333](http://www.linuxjournal.com/article/6333)

---

### Post by loclei on 2006-11-11
your links are good but for someone who wants to set up a proxy server
i merely want to set the proxy for the apt-get procedure

---

### Post by .t. on 2006-11-11
export http_proxy="ip:port"

---

### Post by loclei on 2006-11-11
how to use the command you showed?
i just replaced the "ip:port" with the proxy ip and port and nothing happens

---

### Post by .t. on 2006-11-11
Nothing is supposed to happen. This just means that you have set the proxy in the environment, for other applications to use. The command `export` doesn't produce (stdout) output in this situation. However, you should now be able to use apt through the proxy.

---

### Post by loclei on 2006-11-11
thx man i did  
```

export http_proxy="http://ip:8080"

```
and it worked 
thx
you're the best

---

### Post by .t. on 2006-11-11
No problem man, any time :D

---

### Post by flajus on 2006-11-12
> **taurus said:**
> Can you paste your /etc/apt/sources.list here?  Open a terminal, Applications -> Accessories -> Terminal, and type

```
cat /etc/apt/sources.list
```



HERE IT IS:


#Atkomentuokite (istrinkite #) reikiamus saltinius (eilutes, prasidetancias deb)
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

#Sifruotu DVD palaikymas (libdvdcss2 paketas), nuosavybiniai audio/video dekoderiai bei kiti multimedia paketai
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main              #Sifruotu DVD palaikymas (libdvdcss2) ir kt

#Baltix GNU/Linux papildomu programu paketu saugykla.
#deb [ftp://ftp.akl.lt/Linux/Baltix/Baltix-Ubuntu_packages](ftp://ftp.akl.lt/Linux/Baltix/Baltix-Ubuntu_packages) breezy main    #Baltix paketu saugykla

#Lietuvisku debian paketu saugykla. Naudoti tik patyrusiems
#deb [ftp://debian.home.lt/debian](ftp://debian.home.lt/debian) unstable main contrib non-free              #Lietuvisku debian paketu saugykla

#Windows emuliatorius (WINE)
#deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) breezy/

# Source packages (deb-src) are needed only for developers and advanced users for compilation.
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe


deb [http://lt.archive.ubuntu.com/ubuntu/](http://lt.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [http://lt.archive.ubuntu.com/ubuntu/](http://lt.archive.ubuntu.com/ubuntu/) breezy main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

