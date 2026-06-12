---
title: "how do i fix this odd problem with my source list"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-08-02
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_multiverse_binary-i386_Packages)

---

### Post by scxtt on 2006-08-02
posting your sources.list would probably be helpful ...

---

### Post by catlett on 2006-08-02
You have the same repository listed more than once.
You most likely added to your repository list and there is a duplicate entry.
Just open you repository list and edit out the duplicate entry. If you don't know which one it is, post your list and I are someone will tell you which one it is.
```
sudo gedit /etc/apt/sources,list
```

---

### Post by lime4x4 on 2006-08-02
here is a copy of my current list the odd part is the location of the error

/var/lib/apt/lists

####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

#Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
# deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
# deb [http://claws.sylpheed.org/ubuntu/dapper/](http://claws.sylpheed.org/ubuntu/dapper/) ./

---

### Post by scxtt on 2006-08-02
get rid of the lines in red:
```
#Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
[color=red]deb http://archive.ubuntu.com/ubuntu dapper-backports main
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main

deb http://archive.ubuntu.com/ubuntu dapper-backports restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted[/color]

[color=blue]deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse[/color]

[color=red]deb http://archive.ubuntu.com/ubuntu dapper-backports universe
deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe

deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse[/color]
```they're taken care of by the lines in blue ...

---

### Post by lime4x4 on 2006-08-02
ok thanks that took care of the duplicate errors now i'm left with a new error

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by scxtt on 2006-08-02
hard to say, that might be a problem w/ the actual repo (i can see that file) or your box can't read a bzip2 file (make sure you have bzip2 installed) ...

---

### Post by lime4x4 on 2006-08-02
yeap bzip2 is installed i'll try tomorrow and c what happens
Thanks for the help

---

