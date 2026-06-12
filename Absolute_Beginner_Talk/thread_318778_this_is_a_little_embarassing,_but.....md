---
title: "this is a little embarassing, but...."
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by frootstripe on 2006-12-14
Hi, how do I know what version of Kubuntu I am running? I recently did a dist-upgrade but I didn't update the sources.list (i'm supposed to right?). Could we have an "official" page that shows the release version, corresponding kernel, and the official sources.list. This would be great for people like me who tend to be sloppy with their administration tasks.

Thanks

---

### Post by Sqwishy on 2006-12-14
sources.list changes from person to person. for example... someone who uses beryl will have the beryl repositories. but by default they arn't included. so there is no official sources.list

---

### Post by Lord Illidan on 2006-12-14
Click on the menu, Help, then About Kubuntu.

Mine shows this :

---

### Post by muep on 2006-12-14
Can you paste your sources.list? If you dist-upgraded in some automatic way, it probably updated it. Or if you just ran sudo apt-get dist-upgrade without doing anything else, the effect is almost the same as sudo apt-get upgrade. Usually it is exactly the same.

---

### Post by frootstripe on 2006-12-14
My /etc/sources.list:

```
# deb http://kubuntu.org/packages/amarok-1.3.8 breezy main
# deb http://kubuntu.org/packages/kde35 breezy main
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
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe
```

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

# deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary /

# deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
# deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

~
~
```

```

So, I'm unclear on what `dist-upgrade' does from the response above. I ran `apt-get dist-upgrade', btw. Does it automatically update sources.list?

---

### Post by meng on 2006-12-14
Looks like you're using Breezy 5.10.
Ctrl-alt-f1 should confirm this (ctrl-alt-f7 to get back).

---

### Post by frootstripe on 2006-12-14
Yes, I'm using Breezy. Just for clarity, if I'm updating from the command line with `apt-get dist-upgrade', is my sources.list automatically updated as well?

---

### Post by Lord Illidan on 2006-12-14
> **frootstripe said:**
> Yes, I'm using Breezy. Just for clarity, if I'm updating from the command line with `apt-get dist-upgrade', is my sources.list automatically updated as well?

No it's not.

---

### Post by frootstripe on 2006-12-14
Ok, thanks for the info. I guess I updated the sources.list myself and forgot about it....

---

