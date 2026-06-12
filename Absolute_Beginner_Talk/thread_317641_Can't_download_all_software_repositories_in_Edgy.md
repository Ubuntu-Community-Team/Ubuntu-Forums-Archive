---
title: "Can't download all software repositories in Edgy"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by crazybrit4967 on 2006-12-12
Hello all,
For some reason, when I do sudo aptitude update (or try to update with any package manager) I get the error message 
```
99% [2 Packages gzip 0]            
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 2B in 5s (0B/s)
Reading package lists... Done

```

Anyone know why this is?

---

### Post by taurus on 2006-12-12
Let's have a look at your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by wpshooter on 2006-12-12
Go into Software Properties or whatever the menu choice is called in Edgy and make sure all of the Repository choices are MARKED.

You will probably be prompted to RELOAD when you attempt to exit - do the RELOAD.

---

### Post by John.Michael.Kane on 2006-12-12
You will need to uncomment the lines in your sources.list

Run:
```
gksudo gedit /etc/apt/sources.list
```

Heres a working edgy sources.list you can copy past it.

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

```

Next run:
```
sudo aptitude update
```

---

### Post by vayde on 2006-12-12
I've got the same problem with a fresh edgy install.

There's nothing wrong with my /etc/apt/sources.list.  It came fresh off the install cd, which has worked flawlessly before today.

I've even downloaded [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) by hand.  It won't open.  I suspect someone uploaded a bad file recently, but I don't know what we do about it.

---

### Post by crazybrit4967 on 2006-12-12
Yeah, I don't see why it would be a problem with my sources.list - it seems more like a corrupt file.  For the record, my sources.list is completely commented out, but everything is checked in Synaptic.  However, all the repos except the universe repository work fine.

---

### Post by wpshooter on 2006-12-13
> **crazybrit4967 said:**
> Yeah, I don't see why it would be a problem with my sources.list - it seems more like a corrupt file.  For the record, my sources.list is completely commented out, but everything is checked in Synaptic.  However, all the repos except the universe repository work fine.

If you have all the proper things checked in Software properties and have restarted your machine afterwards and it still will not work, there almost has to be something work on the Ubuntu end.

---

### Post by vayde on 2006-12-13
I pretty much guarantee it's on the ubuntu end.  Question is, who do we contact to fix it?

---

### Post by crazybrit4967 on 2006-12-13
Whoa.  I'm not liking these new buttons one bit.

(bump)

---

