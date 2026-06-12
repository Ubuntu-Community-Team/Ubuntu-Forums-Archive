---
title: "msttcorefonts installation problem"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by boudreaujr on 2007-04-23
I've checked my repositories and have muliverse enabled.  When I select msttcorefonts for installation I get the following error message and no installation is available.

msttcorefonts:
 Depends: cabextract  but it is not installable

Has this package been removed?

Denis

---

### Post by Snowcat on 2007-04-23
You have mutiverse, but do you also have universe enabled? A quick look in my Synaptic list shows cabextract to be present there (on Feisty, but I'm sure it's there on Edgy as well).

---

### Post by boudreaujr on 2007-04-23
Everything is selected except "Source Code"

That is what is puzzeling me.  I've just installed Feisty on my laptop as my only OS and am trying to make the conversion over to Linux only, but need the ms core fonts for old documents.  

Thanks,

Denis

---

### Post by Bachstelze on 2007-04-23
"Everything" doesn't help us much. Please paste your /etc/apt/sources.list.

---

### Post by boudreaujr on 2007-04-23
Hymntolife:  sorry for the lack of info.  Here is the source list...

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe

---

### Post by Snowcat on 2007-04-23
Hmm... The only relevant thing I have which you don't is:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

Maybe try adding that?

---

### Post by boudreaujr on 2007-04-23
Snowcat:  I added the line you suggested and reloaded Synaptic.  I forgot to mention that I am also getting this error when doing a reload..

"Could not download all repository indexes"

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

I am not sure if this has anything to do with my problem as well.  I'm still having fun with Ubuntu and looking forward to getting all my issues worked out.  It is still a learning experience.

Denis

---

### Post by Snowcat on 2007-04-23
This problem has been mentioned a lot. see here:

[http://ubuntuforums.org/showthread.php?p=2511002](http://ubuntuforums.org/showthread.php?p=2511002)

---

### Post by boudreaujr on 2007-04-23
Snowcat:  Thanks, I think the ftp switch fixed everything.  Installing ms core fonts now.  Didn't think to search on that to begin with.

Denis

---

