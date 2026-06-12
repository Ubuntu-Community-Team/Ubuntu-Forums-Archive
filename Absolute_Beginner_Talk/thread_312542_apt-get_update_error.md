---
title: "apt-get update error"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2006-12-04
Whilst doing an apt-getb update I got this message;

Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.bz2](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.bz2)  MD5Sum mismatch
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.bz2](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.bz2)  MD5Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.bz2)  MD5Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.



What do I do please?

Tony

---

### Post by taurus on 2006-12-04
I would remove the "au." in front of those lines in /etc/apt/sources.list and see what happens.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by tchoklat on 2006-12-04
They are not in the sources list, here it is!

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END



Also when I update I get this message

E: Malformed line 16 in source list /etc/apt/sources.list (dist parse)


regards


Tony

---

### Post by taurus on 2006-12-04
> **tchoklat said:**
> They are not in the sources list, here it is!

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END



Also when I update I get this message

E: Malformed line 16 in source list /etc/apt/sources.list (dist parse)


regards


Tony

Please look over your /etc/apt/sources.list again because I see a bunch of lines with "au." in them...

```

deb http://**[SIZE="4"]au.[/SIZE]**archive.ubuntu.com/ubuntu/

```

---

### Post by tchoklat on 2006-12-04
thanx for persevering...

I have removed the au (even though I am in australia. My sources.list looks like this now -

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

## Major bug fix updates produced after the final release of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe' repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

## Uncomment the following two lines to add software from the 'backports' repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

#AUTOMATIX REPOS END

When I , 

tony@tony:~$ sudo aptitude update
E: Malformed line 14 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 14 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
tony@tony:~$ 


still problematic.

Is there a 'standard' sources.list that I can utilise?


Tony

---

### Post by taurus on 2006-12-04
You need to put a # in front of line 14 in /etc/apt/sources.list, the one just right above the [http://www.getautomatix.com](http://www.getautomatix.com)!

```
#deb http://archive.ubuntu.com/ubuntu/ edgy
deb http://www.getautomatix.com/apt edgy main
```

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by tchoklat on 2006-12-04
I also put one in front of line 27 and it works now. What does the # do?


Tony

---

### Post by kakalaky on 2006-12-04
anything on the rest of a line after # is ignored

---

### Post by taurus on 2006-12-04
> **tchoklat said:**
> I also put one in front of line 27 and it works now. What does the # do?


Tony
# means comment so it will not be looked at.  In other words, every line that starts with the # sign will be skipped over...

---

### Post by tchoklat on 2006-12-04
thanks taurus all working now

thanks for your patience!

---

### Post by taurus on 2006-12-04
> **tchoklat said:**
> thanks taurus all working now

thanks for your patience!
No problem, mate.

---

