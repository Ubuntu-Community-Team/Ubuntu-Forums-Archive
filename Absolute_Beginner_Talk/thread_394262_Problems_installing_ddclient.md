---
title: "Problems installing ddclient"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by shanef1981 on 2007-03-26
Hi everyone,

really new to the world of *nix here, and thought I'd start with Ubuntu seeing as it has a wonderfully supportive user base :-)

Anyway, I installed the server using the LAMP option and when i try to install the ddclient package using:

sudo apt-get install ddclient

it returns an error message that no such package can be found...

So how do I get it there...


Many thanks
Shane

---

### Post by kidders on 2007-03-26
Hi there,

[http://packages.ubuntu.com/edgy/net/ddclient](http://packages.ubuntu.com/edgy/net/ddclient)

**ddclient** is in the universe repository... be sure you have it selected.

---

### Post by shanef1981 on 2007-03-27
Okay, so if i used wget to download the tar.gz package to the server, and used gzip -d to decompress the file to a .tar, where do I go from there?

Thanks :-)

---

### Post by kidders on 2007-03-27
> **shanef1981 said:**
> i used wget to download the tar.gz package to the server, and used gzip -d to decompress the file to a .tarWhere did you get the tarball from? Did you download the source?

Assuming that's what you've done, **tar xf** it into a directory, and follow the instructions provided. Most of the time, they ask you to do some variation of **./configure && make && sudo make install**.

Unless you have a specific reason for _not_ wanting to do so, you really should use Ubuntu's package manager to install all software, though.

---

