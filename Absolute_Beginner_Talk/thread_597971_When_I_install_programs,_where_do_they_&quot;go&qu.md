---
title: "When I install programs, where do they &quot;go&quot;?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by rolheika on 2007-10-30
This is a very general question that can probably be answered easily.

Anyway, I installed Nicotine and I am using it successfully.  I simply used apt-get to install it, and I also run it from the command line.

But let's say that I wanted to find it among the folders in my system?  I never specified a folder when I installed it, so where would the default location be?

---

### Post by kevdog on 2007-10-30
Do this (although most go in /usr/bin -- the executables, and the config files are in /etc)

sudo updatedb
locate nicotene

---

### Post by rolheika on 2007-10-30
Ah, thanks, they actually appeared in the /usr/share/app-install/ folder.

---

### Post by FXEF on 2007-10-30
> **rolheika said:**
> This is a very general question that can probably be answered easily.

Anyway, I installed Nicotine and I am using it successfully.  I simply used apt-get to install it, and I also run it from the command line.

But let's say that I wanted to find it among the folders in my system?  I never specified a folder when I installed it, so where would the default location be?

Most likely the /bin, /usr/bin directories. 

The /bin directory contains the most important programs that the system needs to operate. 

The /usr/bin contains applications for the users.

---

