---
title: "Aptitude update problem - archive.ubuntu"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by VraiChevalier on 2007-04-14
Trying to update  /etc/apt/sources.list via "sudo aptitude update" but for some reason it cannot connect with [http://archive.ubuntu.com](http://archive.ubuntu.com). 

Does anyone know if there is a problem on their end?

All my other internet connections and URL's in "aptitude update" seem to be working fine.

---

### Post by Seisen on 2007-04-14
Post exactly what you source list looks like by doing this.

```
sudo gedit /etc/apt/sources.list
```

---

### Post by VraiChevalier on 2007-04-14
This is what it looks like. I was trying to enable and update sources list using Psychocats wiki so I could install XFCE. Does it look "right"?

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by Seisen on 2007-04-14
I don't see anything wrong with it, they might just be having problems with it. You can always try putting the link into firefox and see if it works.

[http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu")

---

### Post by VraiChevalier on 2007-04-14
Thanks Seisen!

I appreciate the feedback. I did try putting the URL in Firefox. I tries to open but just keeps trying, and trying, and trying. No luck. Other URL's from the sources.list open fine.

I think it must be a problem on their end. I was checking to see if it was just me or if any others were having the same problem.

I'll try it again later.

Ubuntu Forums Rock.

---

### Post by Seisen on 2007-04-14
I can open it up just fine in firefox, so that makes me wonder what else could be the problem. I am using feisty so I can't really check to see if the dapper repo's are having problems or not.

---

### Post by VraiChevalier on 2007-04-14
:confused: That thumping noise is my head banging on the table!:redface: 

I finally realized after some poking and prodding around some settings that I had changed my Firestarter policy and it was blocking the archive address! That's the only one it was blocking though! I had it set to block reserved addresses on  public interfaces . I am chagrined](*,)

But I still appreciate the help!

Problem solved - user error

---

