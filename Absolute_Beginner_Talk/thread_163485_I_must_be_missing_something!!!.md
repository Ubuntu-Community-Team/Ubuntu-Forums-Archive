---
title: "I must be missing something!!!"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by gymsmoke on 2006-04-21
It would be my impression that when you "remove" a package from Ubuntu, it is removed.  I just "removed" apache2, and all of the directories, configuration files, etc, are still here!

does apt-get _not_ do what I think it should do???

It certainly installs enough secondary and tertiary parts that it needs on install (dependencies, etc) , but remove does almost nothing that i can see except remove the package from the list of installed packages!

without the assistance of some type of utility that would truely clean a package and its dependencies and related directories and files from the installation, you're only choice is to keep a constant list of every directory and file which has been installed and manually remove the ones that are connected to a particular package when it gets removed... this is really a lame solution to anything...

So, how does one _actually_ remove a package and all its baggage ?

---

### Post by ComplexNumber on 2006-04-21
> configuration files when you remove a package, it doesn't remove the configuration files in your home directory (ie the ones pertaining to personal settings).

which parts are now remaining?
> 


So, how does one _actually_ remove a package and all its baggage ? if it hasn't removed the package, there must be something that you have omitted to do or that you're overlooking.

---

### Post by nanotube on 2006-04-21
hey
if you do an "apt-get purge" then it removes the configuration files, as well.

afaik, there is no way to get apt-get to remove unneeded dependencies that were installed with your package. apt-get just doesn't keep track of that stuff.

if you really care to clean up your system of unnecessary cruft, try installing the "deborphan" package - it is capable of analyzing all your packages and showing you which ones are no longer depended on by anything - and you can decide whether to remove them.

if you are starting a system "from scratch" you could also try using aptitude instead of apt-get - aptitude does keep track of stuff and can uninstall unneeded dependencies as well. however, it only works if you /installed/ stuff with it in the first place - which is clearly not the case here. 

well, good luck. ;)

---

### Post by aysiu on 2006-04-21
[QUOTE=nanotube]
afaik, there is no way to get apt-get to remove unneeded dependencies that were installed with your package. apt-get just doesn't keep track of that stuff.[/QUOTE] That's why people who like to add and remove stuff frequently should use *aptitude* instead of *apt-get*.

```
sudo apt-get install blah1
``` also installs blah2, blah3, and blah4. ```
sudo apt-get remove blah1
``` removes only blah1. blahs 2, 3, and 4 remain installed.

```
sudo aptitude install blah1
``` installs blah2, blah3, and blah4. ```
sudo aptitude remove blah1
``` removes blah1, blah2, blahd3, and blah4.

---

### Post by gymsmoke on 2006-04-21
dpkg --purge phpmyadmin
(Reading database ... 25284 files and directories currently installed.)
Removing phpmyadmin ...
/var/lib/dpkg/info/phpmyadmin.prerm: line 12: db_get: command not found
dpkg: error processing phpmyadmin (--purge):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 phpmyadmin

---

### Post by nanotube on 2006-04-21
[QUOTE=aysiu]
```
sudo aptitude install blah1
``` installs blah2, blah3, and blah4. ```
sudo aptitude remove blah1
``` removes blah1, blah2, blahd3, and blah4.[/QUOTE]
hey aysiu,
first, just wanted to note that i already suggested aptitude in my first post there. ;)

second, i was wondering, what happens if after installing blah1, you then go to install foo1, which also happens to depend on blah 3.  if you then remove blah1, is aptitude smart enough to know to remove blah 1, 2, and 4, but leave blah3, because foo1 depends on it?

i've never used aptitude myself, i am happy enough with synaptic/apt-get, so i wonder. :)

---

### Post by aysiu on 2006-04-21
> **nanotube]hey aysiu,
first, just wanted to note that i already suggested aptitude in my first post there.  said:**
>  You're right. I missed that. Oops.

> 
second, i was wondering, what happens if after installing blah1, you then go to install foo1, which also happens to depend on blah 3.  if you then remove blah1, is aptitude smart enough to know to remove blah 1, 2, and 4, but leave blah3, because foo1 depends on it? Well, take a look at this (emphasis added): ```
user@ubuntu:~$ sudo aptitude install kword
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  mousepad
The following NEW packages will be automatically installed:
  kspread libwv2-1c2
The following NEW packages will be installed:
  kspread kword libwv2-1c2
0 packages upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/7707kB of archives. After unpacking 19.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 79108 files and directories currently installed.)
Removing mousepad ...
Selecting previously deselected package kspread.
(Reading database ... 79081 files and directories currently installed.)
Unpacking kspread (from .../kspread_1%3a1.4.2-3ubuntu11_i386.deb) ...
Selecting previously deselected package libwv2-1c2.
Unpacking libwv2-1c2 (from .../libwv2-1c2_0.2.2-5_i386.deb) ...
Selecting previously deselected package kword.
Unpacking kword (from .../kword_1%3a1.4.2-3ubuntu11_i386.deb) ...
Setting up kspread (1.4.2-3ubuntu11) ...

Setting up libwv2-1c2 (0.2.2-5) ...

Setting up kword (1.4.2-3ubuntu11) ...

user@ubuntu:~$ sudo aptitude remove kword
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
[b]The following packages are unused and will be REMOVED:
  kspread libwv2-1c2[/b]
The following packages will be REMOVED:
  kword
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 19.6MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 79863 files and directories currently installed.)
Removing kword ...
Removing kspread ...
Removing libwv2-1c2 ...
``` So it looks as if it'll remove those packages only if no other packages depend on them.

[quote]
i've never used aptitude myself, i am happy enough with synaptic/apt-get, so i wonder. :) There really isn't any reason to use *aptitude* unless you plan to do a lot of installing **and** uninstalling.

---

### Post by gymsmoke on 2006-04-21
aptitude install bind9 - produces this...

Unpacking bind9 (from .../bind9_1%3a9.3.1-2ubuntu1_i386.deb) ...
Setting up bind9 (9.3.1-2ubuntu1) ...
wrote key file "/etc/bind/rndc.key"
 * Starting domain name service... /usr/sbin/named: error while loading shared libraries: libbind9.so.0: cannot open shared object file: No such file or directory

---

### Post by nanotube on 2006-04-21
[QUOTE=aysiu]
(...more stuff...)
 There really isn't any reason to use *aptitude* unless you plan to do a lot of installing **and** uninstalling.[/QUOTE]
hmm, seems pretty cool!
the question is, then, is there any reason NOT to use aptitude in favor of apt-get? seems like there are advantages, but no disadvantages?

---

### Post by gymsmoke on 2006-04-21
OF Course There Is!
LIke, as I said in the OP, if you're on a SERVER and have no GUI

---

### Post by nanotube on 2006-04-21
[QUOTE=gymsmoke]OF Course There Is!
LIke, as I said in the OP, if you're on a SERVER and have no GUI[/QUOTE]
afaik, aptitude is a commandline tool, not a gui tool...

---

### Post by gymsmoke on 2006-04-21
nano~
sorry.  you're right... it's been a long 28 hours....

I was able to remove this finally, but only after i found out about the bug in ubuntu.

However, I did manage to figure out a work-around....

---

### Post by nanotube on 2006-04-21
np, good luck, :) sorry i could not be of more help.

---

