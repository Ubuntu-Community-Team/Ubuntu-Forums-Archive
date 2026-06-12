---
title: "Searching"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-01-25
Hi,


I was wondering if there was a better search application than the plain old "search for files"?


If possible I would quite like one that does the mac thingy were it searches as you type so when you want to search for "arctic" for example when you press the a it begins to search all the things with a in and as you continue to type it cuts the search down.

Thank you very much.

---

### Post by chimera on 2006-01-25
Click on the places menu
Click on the "search for files" button

there you go:D

---

### Post by Dr Von Bon Bon on 2006-01-25
Whoops,


Thanks for the reply but I know about that search function and I was just wondering if anyone else knew a better one than that because it's not very good.


Thanks lots anyway.

---

### Post by mustang on 2006-01-25
I've heard good things about:

[http://beaglewiki.org/Main_Page](http://beaglewiki.org/Main_Page)

and ```
slocate *filename* 
```

has helped from time to time.

---

### Post by hillbilly on 2006-01-25
you can always use the command "find" and play around with its vast array of options.

---

### Post by kaamos on 2006-01-25
Beagle is THE search application. :) Now running 0.2.0 and loving the new beagle-search gui.

---

### Post by Dr Von Bon Bon on 2006-01-25
That sounds cool,


Where do I get it from please?


A sudo-apt command would be appreciated.

---

### Post by kaamos on 2006-01-25
The beagle wiki has instructions for ubuntu. Just follow [http://beaglewiki.org/Getting_Started](http://beaglewiki.org/Getting_Started)

---

### Post by Dr Von Bon Bon on 2006-01-26
When i try and follow the first step this happens:


```
god@Callum:~$ sudo apt-get install mono mono-jit mono-utils mono-mcs mono-assemblies-arch \
> mono-assemblies-base mono-common libmono0 mono-devel
Password:
Reading package lists... Done
Building dependency tree... Done
mono-jit is already the newest version.
Package mono-assemblies-arch is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package mono-assemblies-arch has no installation candidate

```


Any help please?

---

### Post by johannes on 2006-01-27
If I remember correctly, all you have to do is:

sudo apt-get install beagle

The depending packages will be automatically installed.

---

### Post by Dr Von Bon Bon on 2006-01-27
How right you were.


Thanks.

---

