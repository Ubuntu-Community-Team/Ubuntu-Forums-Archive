---
title: "Can FreeBSD 6.1 tar.gz be used/installed on Ubuntu 7.04"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2007-06-20
Can FreeBSD 6.1 tar.gz be used/installed on Ubuntu 7.04 ?

How about cygwin.tar.gz ?

THANKS!!

---

### Post by dreadlord_chris on 2007-06-20
> **Average_Joe said:**
> Can FreeBSD 6.1 tar.gz be used/installed on Ubuntu 7.04 ?

How about cygwin.tar.gz ?

THANKS!!

FreeBSD is an opertating system, similar to Ubuntu - but not the same. You can install it **along side** Ubuntu, as a dual-boot or something. But no - you don't install it **in** Ubuntu.

Cygwin is a *Linux* compatibility layer for *Windows* - it allows you to run many Linux programs in Windows. Again, no - you don't install this in Ubuntu.

---

### Post by Average_Joe on 2007-06-20
Thanks for the information!  Also very well explained!!

---

### Post by supersonicdarky on 2007-06-20
if its source (.tar.gz) you can install in any linux distro (after compiling)

---

### Post by dreadlord_chris on 2007-06-20
> **supersonicdarky said:**
> if its source (.tar.gz) you can install in any linux distro (after compiling)

lol.... did you actually look at what the OP was asking about installing?

---

### Post by Average_Joe on 2007-06-20
Just to be more clear, I wasn't go to install any sort of OS kernel or anything.
There was a specific program I wanted (ImageMagick) and at its website
it did not have a Debian package.  

But it was offered as a tar.gz in the FreeBSD_6.1 .
And it was offered as a tar.gz for Cygwin also.

So I guess another question is in order from my perspective...
If these tar.gz binary packages are useable by Debian and 
(really) all Linux distros, then why the need to name a file
such as ImageMagick-6.3.4_FreeBSD6.1.tar.gz  etc?

THANKS!!

---

### Post by dreadlord_chris on 2007-06-20
> **Average_Joe said:**
> Just to be more clear, I wasn't go to install any sort of OS kernel or anything.
There was a specific program I wanted (ImageMagick) and at its website
it did not have a Debian package.  

But it was offered as a tar.gz in the FreeBSD_6.1 .
And it was offered as a tar.gz for Cygwin also.

So I guess another question is in order from my perspective...
If these tar.gz binary packages are useable by Debian and 
(really) all Linux distros, then why the need to name a file
such as ImageMagick-6.3.4_FreeBSD6.1.tar.gz  etc?

THANKS!!

ah ha... well why didn't you say so....
There's already an ImageMagick package for Ubuntu - it's in the repositories:
```

sudo apt-get install imagemagick

```

btw.... BSD is **not** Linux

---

