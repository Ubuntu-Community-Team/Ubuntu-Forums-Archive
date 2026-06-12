---
title: "Lenny packages"
date: 2012-06-13
forum: Any Other OS
---

### Post by Drenriza on 2012-06-13
Hey guys.

I have a problem with apt-get update, where i get the following error
W: Failed to fetch [http://ftp.dk.debian.org/debian/dists/lenny/main/binary-i386/Packages](http://ftp.dk.debian.org/debian/dists/lenny/main/binary-i386/Packages)  404 Not Found [IP: 130.225.254.116 80]

As one of many errors. And i have searched google for the archive repos but i cant find any link that works. So anyone who can point me in the right direction?

Thanks on advance.

---

### Post by zombifier25 on 2012-06-13
I guess you're using Debian Lenny, whose support has ended, and unsupported releases will have their packages removed. You should switch to a newer release.

---

### Post by Drenriza on 2012-06-13
> **zombifier25 said:**
> I guess you're using Debian Lenny, whose support has ended, and unsupported releases will have their packages removed. You should switch to a newer release.

So your saying their is nothing to do to fix this particular issue?
The main issue is that i was trying to install expect but it cant find the location of the package.

Failed to fetch [http://ftp.dk.debian.org/debian/pool/main/e/expect/expect_5.43.0-17_i386.deb](http://ftp.dk.debian.org/debian/pool/main/e/expect/expect_5.43.0-17_i386.deb)  404 Not Found [IP: 130.225.254.116 80]

So is their another way to install expect or entirely fix the issue?

---

### Post by zombifier25 on 2012-06-13
The server does have expect, but a newer version. If you can't update your sources, then I'm afraid there's nothing you can do but upgrade to a newer Debian.

---

### Post by Linux_junkie on 2012-06-13
The only other way is to go directly to the source and download the original source code and compile / install it yourself.  check for it at [www.sourceforge.net](www.sourceforge.net) or the website of the developers.

---

### Post by Drenriza on 2012-06-13
A okey.

Another issue i have discovered is the following

W: GPG error: [http://archive.debian.org](http://archive.debian.org) lenny Release: The following signatures were invalid: KEYEXPIRED

This is a error message thats new to me. I have read that it's some sort of key that needs to be updated, but how?

---

### Post by cortman on 2012-06-13
> **Drenriza said:**
> A okey.

Another issue i have discovered is the following

W: GPG error: [http://archive.debian.org](http://archive.debian.org) lenny Release: The following signatures were invalid: KEYEXPIRED

This is a error message thats new to me. I have read that it's some sort of key that needs to be updated, but how?

It means just what zombifier told you:

> I guess you're using Debian Lenny, whose support has ended, and unsupported releases will have their packages removed. You should switch to a newer release.

The repo is expired. Upgrade or do a new installation of Debian Squeeze.

---

### Post by Drenriza on 2012-06-13
> **cortman said:**
> It means just what zombifier told you:

The repo is expired. Upgrade or do a new installation of Debian Squeeze.

That makes no sense. Since some systems i have can still get in touch with the repo but this particular system gets the error.. And they are identical in installation.

---

### Post by philinux on 2012-06-13
Moved to Other OS/Distro talk forum.

---

### Post by wheeze on 2012-06-13
Since lenny is expired some sites may have stopped updating their mirrors to save bandwidth. They're not supposed to but there you go...

You might try changing the servers in your sources.list file to find mirrors that have been kept up-to-date.

---

