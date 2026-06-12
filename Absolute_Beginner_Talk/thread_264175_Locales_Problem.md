---
title: "Locales Problem"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by BrianAT on 2006-09-24
I get the following when I tried to dpkg -reconfigure --force locales

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Package `lacales' is not installed and no info is available.

```

I have been doing a few things to fix a problem I [reported earlier]("http://www.ubuntuforums.org/showthread.php?t=262740").
The last thing I tried was "dpkg -P language-pack-en-base", "dpkg -P language-pack-en" and "dpkg -P language-support-en" So I could do a clean reinstall of the Enlighs language pack. 
If I "apt-get language-pack-en-base" the system freezes. I will try to recreate what it said right before it froze:

```
Setting up language-back-en-base
Generating locales
 en_AU.UTF-8... /usr/sbin/locale-gen: line 238:5549 Segmentation fault l
ocaldef sno_archive --magic= $GLIBC MAGIC -l $input -c -f $charset $locale_alias
 $locale
failed
en_BW.UTF-8...
```

And that is where it freezes. I may have wrote down or mistyped some of the above, but that is as close as I can get it without being able to copy/paste.
Before it got to that part there was a "Selecting previously deselected package" or something along those lines. Perhaps dpkg is trying to read an old one that is broken rather then a new one?
I figure either the script is off, or the something it is reading off a pack on the HD is bad. I downloaded the language-pack-en-base and language-pack-en from the Ubuntu website, but I am not sure what to do with them now...if they will do my any good.
If anyone has any help to offer it would be appriciated. Some programs just seem to refuse to install, or install but don't work with the language pack being out of whack. (Such as gcompris, which during install said something like "Please check that your locale settings" in the terminal window while installing. While it seemed to finish the install fine, it logs me off and sends me to the GUI logon prompt of Ubuntu.)

---

### Post by stilus on 2006-09-26
If you have a network connection (or CD), you might want to try an 
```
apt-get -f install 
```.
This could help when you are missing packages. 
and ```
apt-get --reinstall install locales 
``` might help as well. 
I'm not at my machine so I cannot find out in more detail...

good luck,

stilus

---

### Post by BrianAT on 2006-09-26
Well that fixed a couple programs anyhow.
If I try to use the Language Support option in Administration, the system still freezes once it gets to Generating Locals. 

Here is the output of locale
```
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LANGUAGE=en_US:en_GB:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

EDIT to add:
Here is the output of sudo dpkg-reconfigure --force locales
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_GB.ISO-8859-1... up-to-date
  en_US.ISO-8859-1... up-to-date
  pt_BR.ISO-8859-1... up-to-date
  pt_PT.ISO-8859-1... up-to-date
Generation complete.
Current default timezone: 'America/New_York'.
Local time is now:      Tue Sep 26 11:03:13 EDT 2006.
Universal Time is now:  Tue Sep 26 15:03:13 UTC 2006.
Run 'tzconfig' if you wish to change it.
```

So it is starting to improve. Something wrong with the setting of LC_* stuff, but we are a few steps closer. Thank you.

---

### Post by Iarwain ben-adar on 2006-09-26
Hi,
i fixed it by typing something like this (don't copy over unless you are sure it is correct,
or confirmed by someone else ;-) )

```
sudo aptitude install libc6 \dapper
```

I don't know about the \dapper part, but i know "dapper" was surely in it..

I found the answer on this forum, try searching for "libc6" and "locale"


Iarwain

---

