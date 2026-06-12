---
title: "How to apt-get install from Internet repository"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by smith.norton on 2006-12-19
I am unable to install bison, lex, etc. using apt-get. My home PC is not connected to Internet, so is there any way I can take these from the internet to my home PC using a removable disk  and then do apt-get install. If yes please tell me the exact steps to do so.

---

### Post by Bachstelze on 2006-12-19
All the packages in the repos can be downloaded from [http://packages.ubuntu.com](http://packages.ubuntu.com)

When you have transeffer the DEBs to your other box, you can install them with *sudo dpkg -i filename.deb*. Just a suggestion though, I recommend you use Debian on a non-Internet-connected machine, as it has 21 CDs of apt-gettable packages.

---

### Post by xyz on 2006-12-19
> **smith.norton said:**
> I am unable to install bison, lex, etc. using apt-get. My home PC is not connected to Internet, so is there any way I can take these from the internet to my home PC using a removable disk  and then do apt-get install. If yes please tell me the exact steps to do so.
Hi,
You can download it:
[BISON]("http://www.icewalkers.com/Linux/Software/515090/bison.html")
[Install it]("http://www.linux.com/guides/html/chapter06/bison.shtml")
Watch for dependencies.

[ftp://ftp.gnu.org/gnu/bison/](ftp://ftp.gnu.org/gnu/bison/)

---

### Post by ghaz on 2006-12-19
I also do not have an internet connection at home. So I keep my own local mirror of the ubuntu repos on my usb hdd.

You can use the program 'debmirror'. This is the script I got from somewhere and edited to fit my needs. Maybe it can be of some use to you.

```

#!/bin/bash

HOST=ftp.blah.ac.za

DISTS="edgy,edgy-security,edgy-updates"
ARCHS="i386"
SECTION="main,multiverse,restricted,universe"

MIRROR_ROOT='ubuntu'
LOCAL="/media/usbdisk/ubuntu_mirror"

#OPTIONS="--passive --progress --verbose --nosource"
OPTIONS="--passive --progress --verbose --ignore-missing-release --ignore-release-gpg --nosource"

if [ -f $LOCAL/Archive-Update-in-Progress-debian ]
then
echo "Mirroring ubuntu Testing Package"
echo "So exiting"
exit
fi

echo "Processing standard using $HOST"
/usr/bin/debmirror --section=$SECTION --host=$HOST --dist=$DISTS --arch=$ARCHS $OPTIONS -r $MIRROR_ROOT $LOCAL
/bin/rm -f $LOCAL/Archive-Update-in-Progress-debian 


```

Then you just need to edit '/etc/apt/sources.list' at home to include your local repos.


[edit] Just remember that this downloads about 10GB of packages and it doesn't contain the source.

---

