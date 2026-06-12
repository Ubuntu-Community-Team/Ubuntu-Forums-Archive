---
title: "Hi!  How can I correct this error?"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by izvie on 2006-11-17
Hi,

I got the following error message when I tried to use the automatic updates function tonight:

E: Malformed line 30 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

I also get the exact same message when I try to open the Synaptic Package Manager.  I am on version 6.06.

Thanks!

---

### Post by taurus on 2006-11-17
Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here.

```
cat /etc/apt/sources.list
```

---

### Post by Antrix on 2006-11-17
Just paste the contents of /etc/apt/sources.list here.

By the looks of it there is a syntax error around line 30.

---

### Post by izvie on 2006-11-17
Ok, here is what I got:

## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiversedeb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
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
deb [http://wine.sourceforge.net/apt/binary](http://wine.sourceforge.net/apt/binary)
dana@dana-desktop:~$

Thanks!

---

### Post by izvie on 2006-11-17
*Bump*

---

### Post by dweez on 2006-11-17
izvie, I think you left some of it out but try this.  Comment out the last line (the wine.sourceforge.net) by putting a # at the front of the line then open up Synaptic, do a Refresh, and try an update.

---

### Post by izvie on 2006-11-18
dweez, thanks for the tip.  I'll have to take a look at this tomorrow...gotta get up early tomorrow...

---

### Post by adam.tropics on 2006-11-18
```
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiversedeb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
```

somewhere you have lost a newline, so it should be...

```
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
```

---

### Post by dweez on 2006-11-20
adam.tropics, that's true as well (I eluded at it but wasn't clear when I told izvie that he didn't seem to copy/paste his/her whole sources.list).

izvie, the error indicates that line 30 is where the error is.  Open your sources.list and count down to line 30.  If it's the line adam.tropics mentions, that's what's causing you the problem.  If not, post up that line for us to see.

---

