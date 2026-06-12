---
title: "need help messed up my sources.list :("
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Intruder on 2007-09-26
trying to edit it so i didnt need the cd but removed a # too many i think 

#
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807)]/ dapper main restricted

[http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted


deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted


deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe


deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Cheers in advanded

Int

---

### Post by Skerit on 2007-09-26
Oh, nothing bad:

after your last "deb cdrom" line you have a "http://gb.archive..." thing, you need to put "deb" in front of it.

Here, a bit of information on the sources.list file (quite interesting if you're new)

[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-sources.list](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-sources.list)

good luck!

---

### Post by Intruder on 2007-09-26
great link mate just had a look and good read, one blumming problem sorted onto the next loool

sudo apt-get install liblua5.1-0-dev 
Password:
E: Malformed line 16 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.

just looked at link and dont really help :S  sorry and again thx for the quick reply

Int

---

### Post by Skerit on 2007-09-26
Oops,

take a good look, you got one "deb" too many :P 

One repository can't contain BOTH binarys AND sourcefiles at the same time. It's safe to say that this one is a source-repository, so just remove the deb :)

---

### Post by Intruder on 2007-09-26
damn why didnt i see that !!! thx man

Int

EDIT  Works a treat thx for the help mate your a star

---

### Post by bodhi.zazen on 2007-09-26
Yuck ....

Here is a dapper repo list :

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

---

### Post by Skerit on 2007-09-26
> **bodhi.zazen said:**
> Yuck ....

Here is a dapper repo list :

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)


Ah, there those are...

anyway, better to point to an error then to fix it for them! :)

Anyway, my pleasure!

---

### Post by Intruder on 2007-09-27
Ok guys whats the advantage of changing?  May sound daft but no idea, i have had no problem with my current repos can you explain the advantages / differances please bodhi.zazen

Thx to  you both for the help

Int

---

### Post by bodhi.zazen on 2007-09-27
> **Intruder said:**
> Ok guys whats the advantage of changing?  May sound daft but no idea, i have had no problem with my current repos can you explain the advantages / differances please bodhi.zazen

Thx to  you both for the help

Int

There is no need to change, that is not what I wanted to imply. I was just providing a link to a default listing of repos.

If you do not need to use them, \o/. My thinking is someone else may look through this thread and need such a reference.

---

### Post by hyper_ch on 2007-09-27
and here you can generate a new sources.list:

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

