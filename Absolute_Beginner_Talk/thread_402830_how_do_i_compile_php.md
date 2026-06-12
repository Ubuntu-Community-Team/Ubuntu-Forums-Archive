---
title: "how do i compile php?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by ahlandberg on 2007-04-06
Hello.

I have an Ubuntu 6.10 Edgy Eft machine and am new to Linux.

I have installed PHP using the Synaptic PM. Apache2 + PHP runs well.

Now I need to compile PHP with some parameters (memcached, etc.) but I have absolutely no idea in which DIRECTORY Ubuntu has put PHP!!!

I know the question sounds rediculous, but as I said, this is my first time.

I appreciate any help!

Cheers,

Anders

---

### Post by compmodder26 on 2007-04-06
Most of the php modules are also available from the repositories.  Memcache is in there as well.  After install they should be available to you.  I can't remember, but you may need to restart apache.

---

### Post by ahlandberg on 2007-04-06
Ah okay. Thanks!! So that should be the case for all PHP extensions that I wanna include, right!?

These are the packages that are supposed to be compiled with PHP:

# zlib (on-the-fly data compression) zlib
# memcache (DB-Cache) memcache
# mbstring 


Something else:

There are three different php.ini files in the /etc/php5/apache2, /etc/php5/cgi, and /etc/php5/cli folders. Which one should I use for my CLASSPATH configuration??

---

### Post by compmodder26 on 2007-04-06
mbstring and zlib are in there by default.  The only one you'll need to install is php5-memcache.

The one to use for your CLASSPATH is in /etc/php5/apache2

---

### Post by ahlandberg on 2007-04-06
Many thanks!!!!!!!!!!!

---

