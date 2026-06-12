---
title: "Malformed line 40 ..."
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by jtuttle on 2007-07-21
I am now on my second day so you know where I am.  I am getting the error message

"E: Malformed line 40 in the source list/etc/apt/sources list
E: The list of sources could not be re
go to the repository dialog to correc
E: _cache->open()failed, please rep"

Here is what you see.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://google.com/google](http://google.com/google) earth



Wheere did I go wrong? What do I do?

Thanks,

Jerry Tuttle

---

### Post by jtuttle on 2007-07-21
I also see a reference to Google Earth which I downloaded and tried to run.  This may be the cause of it all.

Jerry Tuttle

---

### Post by forestpixie on 2007-07-21
you've added the last line to the sources.list I assume

to fix the error

```
sudo gedit /etc/apt/sources.list
```

and delete, or comment out (with a #) the line with google in it then save and close

```
sudo apt-get update
```

try this to install google earth
```

sudo apt-get install google-earth
```

---

### Post by lluisanunez on 2007-07-21
[http://google.com/google](http://google.com/google) earth sure doesn't look like a repository. Edit /etc/apt/sources.list and delete the line

---

### Post by jtuttle on 2007-07-21
Thank you both very much, that fixed it!

Jerry Tuttle

---

### Post by forestpixie on 2007-07-21
If when you try to install it can't find google-earth

this page gives instructions

[http://www.google.com/linuxrepositories/apt.html](http://www.google.com/linuxrepositories/apt.html)

good luck

Edit - alternatively it's already worked and then I'm glad it worked for you! :D

---

