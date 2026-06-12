---
title: "Constant Kopete Crashs"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by jokerjake on 2007-11-05
Hey i need help with a problem i've been getting after just newly dual booting Kubuntu.

The problem is, i put in my msn details, and try to log on, and it instantly crashes, and gives me the code:

Following code is what i get when the kopete crashes :::
 
 Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)

Any ideas guys?

---

### Post by Matakoo on 2007-11-05
> **jokerjake said:**
> Hey i need help with a problem i've been getting after just newly dual booting Kubuntu.

The problem is, i put in my msn details, and try to log on, and it instantly crashes, and gives me the code:

Following code is what i get when the kopete crashes :::
 
 Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)

Any ideas guys?

Not on top of my head, but a suggestion...you say msn details. Do you use only msn? If so, I would recommend Kmess instead. [www.kmess.org](www.kmess.org) (there is a version available through adept, but rather old).

---

### Post by jokerjake on 2007-11-05
i've just downloaded the installer version of that kmess you just told me to download, i went into the file i'd saved it too, and when i open it, its in binary codes, it wont install or anything!

is there like some coding i need to do with linux because i've just came off windows full graphical interface and i need to be told. 

or is it just my system is not up to date with stuff?

---

### Post by jokerjake on 2007-11-05
The message i was getting was as follows:

The application Kopete crashed and caused the signal 11 (SIGSEGV)

in Backtrace i get rows upon rows of:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)

does this mean i don't have a debugger or something?

help please!

---

### Post by Matakoo on 2007-11-05
> **jokerjake said:**
> i've just downloaded the installer version of that kmess you just told me to download, i went into the file i'd saved it too, and when i open it, its in binary codes, it wont install or anything!

is there like some coding i need to do with linux because i've just came off windows full graphical interface and i need to be told. 

or is it just my system is not up to date with stuff?

Sounds like the executable flag is not set. If you don't know, Linux does not use the file extension to figure out if a file is a program or not. 

In order to make Linux see that downloaded installer as a program, do like this:

1. Right-click on the file and select properties.
2. Click on the permissions tab.
3. Click the "is executable" flag.
4. Click ok

Now you should be able to run it. For further instructions, check:
[http://www.autopackage.org/docs/howto-install/index.html](http://www.autopackage.org/docs/howto-install/index.html)

---

