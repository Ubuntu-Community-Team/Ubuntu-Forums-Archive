---
title: "&quot;the list of sources could not be read&quot;"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Nyxess on 2007-06-29
E: Malformed line 50 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

this came up when i was trying to add a new repository forCombiz.....what does it mean and how can i fix it?

---

### Post by Rui Pais on 2007-06-29
check line 50 of /etc/apt/sources.list 
 (compare with others to see if you can find the error)

post here your sources.list if you couldn't fix it

---

### Post by Nyxess on 2007-06-29
how do i check that? i following the path in "computer" but there are only two files there.....im pretty new to this and im just trying to install things by following directions. i dont really have a good grasp of whats going on o.O

---

### Post by Rui Pais on 2007-06-29
try past this to a terminal:
```
gksudo gedit /etc/apt/sources.list 
```

---

### Post by Nyxess on 2007-06-29
found it....




## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START


deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates universe multiverse main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper main
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy.
deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm
eb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx

i did find it, right?

---

### Post by mikewhatever on 2007-06-29
It looks like a 'd' is missing in the last line > eb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx

---

### Post by Rui Pais on 2007-06-29
last line:
```
eb http://www.beerorkid.com/compiz dapper main aiglx
```
should be:
```
**d**eb http://www.beerorkid.com/compiz dapper main aiglx
```

:)

---

### Post by Nyxess on 2007-06-29
i gave it that command it gave me

(gksudo:6845): Gtk-WARNING **: cannot open display:

---

### Post by overdrank on 2007-06-29
Hi and yes you found it, you have edgy reops in your dapper system. I believe that will not work. :(

---

### Post by Nyxess on 2007-06-29
thank you =) i should have copied more carefully

---

### Post by Rui Pais on 2007-06-29
> **overdrank said:**
> Hi and yes you found it, you have edgy reops in your dapper system. I believe that will not work. :(

I just looked for line 50 and miss that... [COLOR="Silver"]they were put  there by Automatix...

Another "gentleness" from automatix, i guess...[/COLOR] ... (forget it, incorrect comment)

---

### Post by aeiah on 2007-06-29
the dapper ones are automatix, not the edgy ones

---

### Post by Rui Pais on 2007-06-29
> **aeiah said:**
> the dapper ones are automatix, not the edgy ones

Oh yes you are right... 
sorry, my mistake.

---

### Post by Nyxess on 2007-06-29
ok, i removed the edgy ones, how do i edit the "eb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx"

tried typing it in and replacing the other sources.list file, but it wouldnt let me. is there a command?

---

### Post by Nyxess on 2007-06-29
i got it. thanks for the help, this very sleepy guy appretiates it =)

---

