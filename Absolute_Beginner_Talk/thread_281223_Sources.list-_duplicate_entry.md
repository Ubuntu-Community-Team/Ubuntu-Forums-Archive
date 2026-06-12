---
title: "Sources.list- duplicate entry"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Dual Cortex on 2006-10-20
I get the following warning:
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packag es (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i3 86_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Pack ages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binar y-i386_Packages)
W: You may want to run apt-get update to correct these problems






**[COLOR="Red"][SIZE="4"]the following is my sources.list:[/SIZE][/COLOR]**





## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
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

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free


deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx


# Repositories added to enable Beryl (XGL/Compiz community branch)
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main




I'm wonder where the duplicate  entry is!?

---

### Post by Sef on 2006-10-20
Just put a # before one of the duplicates.  That comments the line, i.e., tells the computer to ignore it.

---

### Post by Dual Cortex on 2006-10-20
THat is what I want to do but I dont know where are the duplicates.

Are the lines that start with deb and deb-src the same thing? (deb source?)
I'm guessing if they pretty much are, I'm guessing I should put a # on the deb-src.
I just have no idea what the deb and deb-src are... other than deb is a package file, but I wonder how this relates to repos and their addresses.

---

### Post by Dual Cortex on 2006-10-26
/Bump - I don't think Sef's answer is an answer... I don't see any duplicates!

---

### Post by Esben Kramer on 2006-10-26
I had the same problem in Dapper. After a quick restart of X, the problem just went away. 

The problem does not seem to be the sources.list file itself though?

---

### Post by Dual Cortex on 2006-10-26
Yeah, well I've probably turned off and booted my computer about 30 times since I started this thread, and I still receive that warning. I really, really doubt that you got that fixed just by restarting X.
Where's aysiu?!

---

### Post by Esben Kramer on 2006-10-26
Hmmm. I just upgraded to Edgy, and I now have the same problem again. I hope somebody can help?

---

### Post by spg76 on 2006-10-27
Try this:

```
sudo apt-get clean ; sudo apt-get check
```

That worked for me.

---

### Post by Bad Seed on 2006-10-28
> **Esben Kramer said:**
> Hmmm. I just upgraded to Edgy, and I now have the same problem again. I hope somebody can help?
I ended on this thread for the same reason :p

> **spg76 said:**
> Try this:

```
sudo apt-get clean ; sudo apt-get check
```That worked for me.
Thank you spg76. I don't know what those commands do, but the warning has gone for me :mrgreen:.

---

