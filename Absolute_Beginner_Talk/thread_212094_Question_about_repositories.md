---
title: "Question about repositories"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Saubazi on 2006-07-09
I just installed 64bit 6.06. I am now trying to install this or that and it is missing some libraries here or there. I did some searching and found out about repositories. 

I found some of the libraries I was yearning for under warty or hoary. Can I just add these ones into my repositories and go on installing the stuff with apt-get? I am a bit confused because I just got into reading and noticed that the different names warty, hoary and breezy refer to version numbers. I started getting a panic that I am mixing different release versions with one or another.Since I have dapper am I allowed to use packages from others breezy or warty or whatever. I would never use mandrake 9 rpms in 10.1.

Is there an easy explanation or place where I can read more before I mess something up?

---

### Post by mlind on 2006-07-09
It's not advised to install libraries from other than your current version's
repository. Although most of the older libraries should work too.

What libraries are you missing? Have you enabled  restricted/multiverse/universe repositories for Dapper ?

---

### Post by John.Michael.Kane on 2006-07-09
This should help.

```
**sudo gedit /etc/apt/sources.list**
copy and paste the following over your existing sources.list

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

**Then sudo aptitude update **

```

You should find all the software you need under **synaptic**
**you should only use the dapper lib's and files**.

---

### Post by Saubazi on 2006-07-09
I was missing at least, libcurl.so.2. I read from other forums about it being in libcurl2 package and probably hoary or something. It sounded about like a good idea to install it since some other guy was suggesting softlinking libcurl.so.3 to lib.curl.so.2 or whatever.

Another one would be libstdc++-libc6.2-2.so.3, but that's more a problem of having it only for i386 in libs/libstdc++2.10-glibc2.2 for instance...

Hmmm...so basically stick with dapper, eh?

It is also not recommended to get a source from "breezy" or something and compiling?

---

### Post by mlind on 2006-07-09
> **Saubazi said:**
> I was missing at least, libcurl.so.2. I read from other forums about it being in libcurl2 package and probably hoary or something. It sounded about like a good idea to install it since some other guy was suggesting softlinking libcurl.so.3 to lib.curl.so.2 or whatever.


yup, try symlinkin
```

sudo ln -sf /usr/lib/libcurl.so.3 /usr/lib/libcurl.so.2

```

> **Saubazi said:**
> 
Another one would be libstdc++-libc6.2-2.so.3, but that's more a problem of having it only for i386 in libs/libstdc++2.10-glibc2.2 for instance...


Have you tried compiling it for your achitechture? Dirty way to do this would be
```

sudo apt-get build-dep *package*
apt-get source -b *package*

```


> **Saubazi said:**
> 
It is also not recommended to get a source from "breezy" or something and compiling?

This is probably the best way to do it, if you need a library which is not in the official repositories.

---

