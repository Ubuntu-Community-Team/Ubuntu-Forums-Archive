---
title: "I've broken Ubuntu!"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Kouki on 2007-06-23
Lastnight I thought I'd install automatix2 on my feisty system since it wasn't working since I upgraded from dapper.

Something went wrong and I thought nothing of it

Until this morning when I can no longer update ubuntu, use SPM or generally most ways of installing new programs.

I'm told I have a defective line 58 in my sources.lst

I would just edit my sources.lst by placing a  '#' in front of the offending line.  However I figured thats probably not the only thing wrong with the file so thought I'd post my sources.lst up here and you can tell me what I need to do to properly tidy up the mess I've caused...

Any pointers greatly appreciated!

My Sources.lst:


deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

# deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

# deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen

# deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

# deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

# deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb [http://packages.dfreer.org](http://packages.dfreer.org)
feisty main
[COLOR="Red"]deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main[/COLOR]
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

---

### Post by Kouki on 2007-06-23
This is the sort of error I'm getting with my new funky sources.lst:

stuart@stuart-desktop:~$ sudo apt-get update
E: Malformed line 58 in source list /etc/apt/sources.list (dist)
stuart@stuart-desktop:~$ sudo apt-get install automatix2
E: Malformed line 58 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
stuart@stuart-desktop:~$

---

### Post by shearn89 on 2007-06-23
the error is here:
> deb [http://packages.dfreer.org](http://packages.dfreer.org)
feisty main

"feisty main" needs to be on the same line.

---

### Post by wjp.reg on 2007-06-23
Just curious why you would be mixing dapper and feisty repos?





> **Kouki said:**
> Lastnight I thought I'd install automatix2 on my feisty system since it wasn't working since I upgraded from dapper.

Something went wrong and I thought nothing of it

Until this morning when I can no longer update ubuntu, use SPM or generally most ways of installing new programs.

I'm told I have a defective line 58 in my sources.lst

I would just edit my sources.lst by placing a  '#' in front of the offending line.  However I figured thats probably not the only thing wrong with the file so thought I'd post my sources.lst up here and you can tell me what I need to do to properly tidy up the mess I've caused...

Any pointers greatly appreciated!

My Sources.lst:


deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

# deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

# deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen

# deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

# deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

# deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb [http://packages.dfreer.org](http://packages.dfreer.org)
feisty main
[COLOR="Red"]deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main[/COLOR]
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

---

### Post by shearn89 on 2007-06-23
surely he isn't, which is why all the dapper ones are commented out?

---

### Post by wjp.reg on 2007-06-23
> **shearn89 said:**
> surely he isn't, which is why all the dapper ones are commented out?

:oops:

---

### Post by Kouki on 2007-06-23
Thanks for the tips, I commented out the offending lines and I fixed it, I'll try popping them back in but this time with lines 58 and 59 on the same lines.

I noticed all the dapper stuff in there and changed all the references of Dapper to Feisty, not that it matters since as you say they are all commented out.  Looks a bit messy, it's a shame when you upgrade ubuntu leaves all the old stuff in the sources.lst.

Edit

Just done it and it works like you say.  Come to think of it, now when I look at the sources.lst it was pretty obvious since the others around it were all on one line.  The truth is that most the stuff in there means nothing to me so I just try to leave it as it is and assume that it's correct!

---

### Post by shearn89 on 2007-06-23
i'm fairly certain you can just remove all the dapper ones, as (i don't think) feisty recognises them. Make a backup of the file, then just delete all the dapper entries, and see if it still works...

---

