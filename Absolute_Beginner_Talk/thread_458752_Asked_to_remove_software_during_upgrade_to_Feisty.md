---
title: "Asked to remove software during upgrade to Feisty"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by bananabob on 2007-05-29
During my upgrade to Feisty I was presented with a list of software packages, and asked if I wanted to remove them as they were "obsolete". I noticed on the list that there was software I was using, being Postgres 8.1.

I know that Postgres 8.1 has been replaced by 8.2 in Feisty, so I knew that I would eventually have to migrate to 8.2, but I didn't want to delete 8.1 yet. So I answered "NO".

What will happen if I remove packages on this list? Obviously if I had deleted Postgress I would have no database server.

Is there a way, using say Synaptic, to determine what the other packages on this list are for, and what is dependent on them.

I am further concerned because the list include things like linuxheaders-2.6.17-10 and 11.

 :confused:

---

### Post by pbw on 2007-05-30
In terminal enter apt-cache show "packagename" to give you a description of the package, and apt-cache showpkg "packagename" will show depends, reverse depends, provides etc. (without quotes btw)

-- pbw

---

### Post by bananabob on 2007-05-30
@pbw
So for instance **libapr0**

> 
bananabob@thorium:~$ apt-cache show libapr0
Package: libapr0
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 324
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Architecture: i386
Source: apache2
Version: 2.0.55-4ubuntu4
Replaces: libapr
Provides: libapr
Depends: libc6 (>= 2.4-1), libdb4.3 (>= 4.3.28-1), libexpat1 (>= 1.95.8)
Conflicts: libapr
Description: the Apache Portable Runtime
 APR is Apache's Portable Runtime Library, designed to be a support library to
 enable programmers to easily write platform independent programs and know that
 they'll work.
 .
 It is currently used by Apache2, Subversion, and Samba-TNG, among others.
Original-Maintainer: Debian Apache Maintainers <debian-apache@lists.debian.org>



So I now know that this is for Apache programmers. No idea why I have it installed then!

> 
bananabob@thorium:~$ apt-cache showpkg libapr0
Package: libapr0
Versions: 
2.0.55-4ubuntu4 (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/dpkg/status
                  MD5: 5f91eb1d4ea0373492292245a358bbf7


Reverse Depends: 
Dependencies: 
2.0.55-4ubuntu4 - libc6 (2 2.4-1) libdb4.3 (2 4.3.28-1) libexpat1 (2 1.95.8) libapr (0 (null)) libapr (0 (null)) 
Provides: 
2.0.55-4ubuntu4 - libapr 
Reverse Provides: 
 


And I assume that because there are no entries under *Reverse Depends:*  that it is safe to remove?

**But wait!** What does the *Provides:*  entry mean? and also *Reverse Provides:* ?

---

### Post by pbw on 2007-05-31
If you go to apt-get remove a package, and something depends on it, it'll warn you and ask. So don't worry, try a package and you'll see.

Provides means whether it provides another package, and reverse provides means whether another package provides the one you entered i would imagine.

---

