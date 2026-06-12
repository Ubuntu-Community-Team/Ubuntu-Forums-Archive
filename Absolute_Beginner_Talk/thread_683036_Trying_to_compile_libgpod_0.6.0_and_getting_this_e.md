---
title: "Trying to compile libgpod 0.6.0 and getting this error message"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2008-01-30
creating test-init-ipod
make[2]: Leaving directory `/home/dan/Desktop/libgpod-0.6.0/tests'
Making all in po
make[2]: Entering directory `/home/dan/Desktop/libgpod-0.6.0/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[2]: *** [de.gmo] Error 127
make[2]: Leaving directory `/home/dan/Desktop/libgpod-0.6.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dan/Desktop/libgpod-0.6.0'
make: *** [all] Error 2

after typing

cd Desktop/libgpod-0.6.0
./configure
make

what's the problem?

---

### Post by corevette on 2008-01-30
**i** don't have an answer...but i found these online:
[http://archives.postgresql.org/pgsql-bugs/2000-12/msg00168.php](http://archives.postgresql.org/pgsql-bugs/2000-12/msg00168.php)
[https://answers.launchpad.net/awn/+question/14714](https://answers.launchpad.net/awn/+question/14714)
[http://gnomefiles.org/comment.php?soft_id=898](http://gnomefiles.org/comment.php?soft_id=898)

or just google: /bin/sh: -o: not found
[http://www.google.com/search?q=%2Fbin%2Fsh%3A+-o%3A+not+found&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=%2Fbin%2Fsh%3A+-o%3A+not+found&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

here is some support for gtkpod
[http://www.gtkpod.org/contact.html](http://www.gtkpod.org/contact.html)

---

### Post by woodsonoversoul on 2008-01-30
All right!! I got everything to compile correctly but now when I try to run

ipod-read-sysinfo-extended DEVICE MOUNTPOINT

I get

Couldn't read xml sysinfo from DEVICE


???

---

### Post by jan quark on 2008-01-30
ehhh 
why not install the package via the synaptic package manager
should be painless
and I have found it in there so
why making additional problems when we dont have to:confused:

---

### Post by woodsonoversoul on 2008-01-31
Well I went to the Syn package manager and installed from there and still have the same problem. Should I do a "complete removal" and then reinstall again? I'm frustrated because I've done this before

---

### Post by jan quark on 2008-01-31
try to remove and do a clean install of this package one more time

for compiling applications you need to have installed the build-essential package
make sure you have this one

---

### Post by woodsonoversoul on 2008-01-31
Does it matter if my ipod is connected during this?

---

### Post by woodsonoversoul on 2008-01-31
In Synaptic it says the latest version is 0.4.2 not what I've been told I need, 0.6.0

---

### Post by woodsonoversoul on 2008-01-31
completly removed and reinstalled with no luck

---

### Post by jan quark on 2008-01-31
here we go
next attempt

try this link
[http://packages.debian.org/de/sid/libgpod-dev](http://packages.debian.org/de/sid/libgpod-dev)

and select the package you need, I suppose i386 if you are running a "nornal" system and not a 64 bit one

then download it and install it by double-clicking

---

### Post by jan quark on 2008-01-31
I read now that the 060 version is a testing version and unstable do you really need this version I have the 0.5.2-2 version and no problems

[http://packages.debian.org/search?searchon=names&keywords=libgpod](http://packages.debian.org/search?searchon=names&keywords=libgpod)

I have linux mint and this package is preinstalled, so its a very drastic method but if you really need this one try linux mint

---

### Post by woodsonoversoul on 2008-01-31
When I try to install the first link/package I get an error saying "dependency not satisfied: libgpod3"

---

### Post by woodsonoversoul on 2008-01-31
bump

---

### Post by jan quark on 2008-01-31
for the missing libgpod3
[http://packages.debian.org/lenny/i386/libgpod3/download](http://packages.debian.org/lenny/i386/libgpod3/download)

I wont give up

---

### Post by woodsonoversoul on 2008-01-31
Alright. Went to download libgpod3 and it said I needed libc6, so I backtracked and found that. Now when I try to install that it says "conflicts with installed package: 'tzdata'.

Thanks for your help

PS. I've got the blue sphere over water as my background (from the link in your sig)

---

### Post by woodsonoversoul on 2008-01-31
I'm really just trying to get my iPOD to work w/ Amarok

---

### Post by shirilover on 2008-01-31
Since you're using Feisty, you could try the files I compiled using pbuilder.
You may need to link libgpod.so.0.2 to libgpod.so.0.3 for amarok versions earlier than 1.4.8 to see the newer generation iPods.

---

### Post by jan quark on 2008-01-31
well at least I could help you with your background:lolflag:

---

### Post by woodsonoversoul on 2008-01-31
Alright, I downloaded and installed the packages shirilover had put together(some of them conflicted with other ones, ie: libgpod-nogk-dev conflicted with libgpod-dev and libgpod2-nogtk conflicted with libgpod2) and I still can't get 

ipod-read-sysinfo-extended DEVICE MOUNTPOINT

to read xml sysinfo from DEVICE

Should I be restarting my system or something?

---

