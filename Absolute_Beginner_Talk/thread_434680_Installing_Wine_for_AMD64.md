---
title: "Installing Wine for AMD64"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by voidoid on 2007-05-06
OK, I've been trying to install Wine on my AMD64 equipped machine, which is running Dapper, as described at this site [http://doc.gwos.org/index.php/Wine_AMD64]("http://doc.gwos.org/index.php/Wine_AMD64") 
 but when I come to the command ```
sudo apt-get install build-essential gcc-3.4 libc6-i386 libc6-dev-i386 ia32-libs
```

I get told that none of the files were found, so my question is, how do I find them? and in the next step how will I know where my libraries are and what to put in ld.so.conf?

Thanks in advance

---

### Post by pay on 2007-05-06
Can you post ```
cat /etc/apt/sources.list
```

---

### Post by voidoid on 2007-05-06
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) dapper main main-all
deb [http://mirror3.ubuntulinux.nl/](http://mirror3.ubuntulinux.nl/) dapper-seveas freenx
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper universe

There it is

---

### Post by zvacet on 2007-05-06
```
sudo apt-cdrom add
            sudo aptitude update
            sudo aptitude install build-essential
```

and make line # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

look like this  deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 

```
sudo aptitude update
```

---

### Post by voidoid on 2007-05-06
What cdrom exactly? my install disk? and aptitiude update tells me that the following are duplicates

W: GPG error: [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by zvacet on 2007-05-06
Yes your install disc,bacause you have built-essential on it.Correct your source list by deleting duplicate lines.

---

### Post by Enverex on 2007-05-06
Why use Dapper just out of interest? Using old packages is probably not a good idea on something still quickly evolving such as AMD64 in its current state and especially with an app like Wine which tends to like new shiny versions of dependencies...

There is also a pre-built package for 7.04 AMD64 in the WineHQ repo now which would make your life easier.

---

### Post by Pale_Buddha on 2007-05-06
> **Enverex said:**
> Why use Dapper just out of interest? Using old packages is probably not a good idea on something still quickly evolving such as AMD64 in its current state and especially with an app like Wine which tends to like new shiny versions of dependencies...

There is also a pre-built package for 7.04 AMD64 in the WineHQ repo now which would make your life easier.

Where?  From winehq.org:

While there is currently no Wine package explicitly designed for the 64-bit version of Ubuntu, there is an easy hack that can be used to install the 32-bit package into the 64-bit distribution and have it function normally.

Point me to the package and I'm a happy man
PB

---

### Post by Enverex on 2007-05-07
The page is just out of date.
[http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.36~winehq0~ubuntu~7.04-2_amd64.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.36~winehq0~ubuntu~7.04-2_amd64.deb)

Or to browse them all: [http://wine.budgetdedicated.com/apt/pool/main/w/wine/](http://wine.budgetdedicated.com/apt/pool/main/w/wine/)

---

### Post by Pale_Buddha on 2007-05-07
> **Enverex said:**
> The page is just out of date.
[http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.36~winehq0~ubuntu~7.04-2_amd64.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.36~winehq0~ubuntu~7.04-2_amd64.deb)

Or to browse them all: [http://wine.budgetdedicated.com/apt/pool/main/w/wine/](http://wine.budgetdedicated.com/apt/pool/main/w/wine/)

You posted it and I installed it  :-)
Thanks!
PB

---

### Post by voidoid on 2007-05-09
Right, just spent a couple of days updating to Feisty, followed the link, and guess what.

It works perfectly, Thanks for the help

---

