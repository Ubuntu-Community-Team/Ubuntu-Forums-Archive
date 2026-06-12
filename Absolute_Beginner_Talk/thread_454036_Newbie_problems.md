---
title: "Newbie problems"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by dovael on 2007-05-25
Have installed Ubunto 7.04 and have loaded Firefox & Thunderbird successfully, both older 1,5 versions, but can't update them. I have tried using Adept manager to find repositories but it tells me it is in "read only mode.need root privledges". 
I also want to install Skype and a driver for my Epson stylus CX3500 printer/scanner but don't know how to do it. Would also like to change password to system.
Thank you for any help & suggestions.

---

### Post by linuxwizard on 2007-05-25
Use these instructions to install newer versions of Firefox and Thunderbird.
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird)

---

### Post by vikramsharma on 2007-05-25
You can also use Automatix to install various apps and codecs required, Swiftfox i686 optimized version of Firefox.  You can get Automatix from [here]("http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.3-7.04feisty_i386.deb") .  There is a complete list of apps available in the left column section.

---

### Post by linuxwizard on 2007-05-25
[https://help.ubuntu.com/community/Automa](https://help.ubuntu.com/community/Automa)

Warning:Please note that Automatix2 is a third-party utility, developed and maintained independently by the [WWW] Automatix Team and is not supported or recommended by Ubuntu.


Warning Regarding Alternative Installation Methods

Warning: EasyUbuntu and Automatix are third-party utilities for installing the most commonly requested applications in some Debian-based distributions. They are not supported or recommended by Ubuntu. While they work well for many users, they have also been known to corrupt systems and leave them in a state where they cannot be upgraded to a later Ubuntu release.

---

### Post by hyper_ch on 2007-05-25
You can easily add skype:

(1) Use the version offered on skype.com:  [http://www.skype.com/intl/en/download/skype/linux/repositories.html](http://www.skype.com/intl/en/download/skype/linux/repositories.html)

> 
Skype for Linux Repositories
Using Skype's apt repository
1. As the root user, add this line to the end of your /etc/apt/sources.list file:
```

deb http://download.skype.com/linux/repos/debian/ stable non-free

```
2. Then run
```

sudo apt-get update

```
to sync to the latest repository and 
```

sudo apt-get install skype

```
to install the latest version of Skype on your computer.


(2) Use the Medibuntu Repository:

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by dovael on 2007-05-27
Thank you for all of the suggestions.Basic problems have been resolved.

---

### Post by oilchangeguy on 2007-05-27
> **linuxwizard said:**
> [https://help.ubuntu.com/community/Automa](https://help.ubuntu.com/community/Automa)

Warning:Please note that Automatix2 is a third-party utility, developed and maintained independently by the [WWW] Automatix Team and is not supported or recommended by Ubuntu.


Warning Regarding Alternative Installation Methods

Warning: EasyUbuntu and Automatix are third-party utilities for installing the most commonly requested applications in some Debian-based distributions. They are not supported or recommended by Ubuntu. While they work well for many users, they have also been known to corrupt systems and leave them in a state where they cannot be upgraded to a later Ubuntu release.

please provide proof that someone from within ubuntu itself (not just someone posting here) has said that ubuntu does not support the use of automatix. and as far as automatix corrupting systems, i'm sure that many more have been corrupted by improper command line usage. a quick look around this user forum will confirm that fact.

---

### Post by linuxwizard on 2007-05-28
At the top of this link
[https://help.ubuntu.com/community/Automatix](https://help.ubuntu.com/community/Automatix)

At the bottom of this link
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

