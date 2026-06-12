---
title: "duplicate sources help"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by itsashame on 2007-11-16
Hi,

When updating (via autoupdate) I get a duplicate sources error, with the following details

W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_feisty_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_feisty_non-free_binary-i386_Packages)

Any thoughts? I'm using 7.04

Thank you.

---

### Post by Sturmeh on 2007-11-16
Open your lists for editing... 

> sudo gedit /etc/apt/sources.list

Then manually find the duplicates listed, and ensure there is only one of each ( duplicates should be EXACT copies, and not just similar. )

---

### Post by itsashame on 2007-11-27
thank you for the reply....

I've been trying to identify duplicate sources... some look the same but have a gb. or us. at the front of the address. Other than that they are the same. I put a ## in front of some to see what would happen. then removed the ##'s and have now been getting this error when I update! Help!

[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)


Any thoughts... here is a copy of my sources list..



# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
## deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

Thanks in advance...

---

### Post by itsashame on 2007-12-02
anyone? still having the same issue...?:(

---

### Post by itsashame on 2007-12-04
:(:(:(:( help??? :(:(:(:(

---

### Post by maniac_X on 2007-12-05
If you want to generate yourself a fresh source.list, goto 
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Always be safe and backup your old source.list first just as a precaution.

.

---

### Post by hyper_ch on 2007-12-05
Taking the above posted sources.list I would trim it down to this:

```

deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb http://packages.medibuntu.org/ feisty free non-free
deb http://download.tuxfamily.org/3v1deb feisty eyecandy

```

That's all you need (well, according to the above posted sources.list

---

### Post by itsashame on 2007-12-05
thanks both...I'll give it a go.:)

---

### Post by itsashame on 2007-12-06
replaced everything with the list in the post above, when updating I now get

could not download all repository indexes

[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

Any thoughts? Thanks in advance.

---

### Post by hyper_ch on 2007-12-07
strange, replace the "security" line with those two:

```

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

```

They should definitively work - but I can't see an typing error in the list posted above.

---

