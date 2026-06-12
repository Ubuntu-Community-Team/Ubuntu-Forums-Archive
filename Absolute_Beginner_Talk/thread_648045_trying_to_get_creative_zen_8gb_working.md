---
title: "trying to get creative zen 8gb working"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by thelegionnaire on 2007-12-23
so i found a tutorial on how to do it:[HERE]("http://ubuntuforums.org/showthread.php?p=3991040")

the problem comes when i get to the step:
> 
./autogen.sh

the terminal spits out:

> Removing libtool cruft
Running libtoolize
./autogen.sh: 19: libtoolize: not found
Last command failed with status 127 in directory /home/m/libmtp.
Aborting



I was wondering if anyone could help me, it'd be sweet to get this thing running. :guitar:

---

### Post by PeterJS on 2007-12-23
Have you tried Amarok or Gnomad yet? If one of those works no reason to put yourself through the pain of a compile.

Edit:

To specifically address the error message you're getting, do you have build-essential installed?

---

### Post by thelegionnaire on 2007-12-23
this is supposedly to get it working in amarok, did you check out the tutorial?

---

### Post by thelegionnaire on 2007-12-23
dont know what build essential is, checking the synaptic package manager for it right now

---

### Post by PeterJS on 2007-12-23
> **thelegionnaire said:**
> dont know what build essential is, checking the synaptic package manager for it right now

Well reading_comprehension-- for me,but I'm going to use my time zone as an excuse for that one.

As for build essenital, it's exactly what it claims to be the tools essential for building things.

Now after actually reading the guide I would suggest installing checkinstall as well and replacing the:
```

sudo make install

```step with
```

sudo checkinstall

```What check install does is add the package management records so that you can uninstall it later if you need/want to.

And in the linking step replacing
```

sudo rm /usr/lib/libmtp.so.6

```
with
```

sudo mv /usr/lib/libmtp.so.6 /usr/lib/libmtp.so.6.old

```

Deleting a system library isn't generally a great idea, making a backup is probably a much better idea.

---

### Post by thelegionnaire on 2007-12-23
ok so i got build essential, and i tried it again, now while running the same command:

> ./autogen.sh

i get this:
> 
m@m-laptop:~/libmtp$ ./autogen.sh
Removing libtool cruft
Running libtoolize
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Removing aclocal cruft
Running aclocal -I ./m4 
./autogen.sh: 25: aclocal: not found
Last command failed with status 127 in directory /home/m/libmtp.


bit more help please?

---

### Post by PeterJS on 2007-12-23
This just isn't my night :).

You need to install automake. Which I could have sworn was part of build essential, but I guess not.

---

