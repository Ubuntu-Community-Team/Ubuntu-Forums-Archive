---
title: "Probelms with make install"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by Pekz0r on 2006-03-26
Hey

I'm trying to install a DNS client from no-ip.com but i have some problems

first i tried this:
make
But i got the following error message:
gcc -Wall -g -O2 -Dlinux -DPREFIX=\"/usr/local\" noip2.c -o noip2
make: gcc: Command not found
make: *** [noip2] Error 127

After som searching i found that i should type '$make'. No error mesages, so i suppose it's working like it should?

But when i try to install with '$make install' i get this error:
install: too few arguments
Try `install --help' for more information.

It looks a simple error but i don't know what to do :-k 

The i got the 'apt-get install make'-package installed

Any ideas?

---

### Post by dermotti on 2006-03-26
Looks like you need to install gcc
**sudo apt-get install gcc**

---

### Post by Pekz0r on 2006-03-26
okey, what is that?

---

### Post by dermotti on 2006-03-26
Its a C compiler. You need to to compile anything.

---

### Post by jrib on 2006-03-26
you should just install the build-essential package, it will give you the essential things taht you need to build things, gcc included

---

### Post by Sef on 2006-03-26
To compile, open the terminal and type this:

sudo apt-get install build-essential

---

### Post by Pekz0r on 2006-03-26
yea, i did that and it worked perfectly

thanks!

---

### Post by Sef on 2006-03-26
your welcome.  Glad I could help you.

---

