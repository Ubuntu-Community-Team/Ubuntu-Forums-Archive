---
title: "How Do I Get Cabextract and Unshield?"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by bugme on 2006-05-02
Hello,
I tried getting cabextract with this:
sudo apt-cache search cabextract
but it didn't work.
How else can I get cabextract and unshield?
Thanks.

---

### Post by aysiu on 2006-05-02
First, [make sure you have the Universe repository enabled](http://www.psychocats.net/ubuntu/sources).

```
apt-cache search cabextract
``` searches to see if the package *cabextract* is available. You want apt-get, not apt-cache: ```
sudo apt-get update
sudo apt-get install cabextract
```

---

### Post by bugme on 2006-05-02
Here is what came up:
apt-get update     (I am already in sudo -s)
apt-get install cabextract
Reading package lists.... Done
Building dependency tree.... Done
E: Couldn't find package cabextract

The same happened with unshield.

Note: I have no connection to the internet on my Ubuntu box.

---

### Post by nanotube on 2006-05-02
well, if you have no connection to the internet, you will have to find and download the cabextract.deb package on packages.ubuntu.com (using the internet from some other computer), then somehow transfer it to your ubuntu machine, and install it with
```
dpkg -i name_of_cabextract.deb
```
using ubuntu with a net connection is... much better than without. :)

---

### Post by aysiu on 2006-05-02
[Here's the package](http://archive.ubuntu.com/ubuntu/pool/universe/c/cabextract/cabextract_1.1-1_i386.deb). Good luck finding all the dependencies for it.

---

### Post by bugme on 2006-05-02
I need cabextract and unshield to get the drivers from a .exe to work my wireless adapter. Trust me, if I could I would, I just got ubuntu and am determined to get my wireless adapter, the Netgear WG111v1, to work.
BTW, if you have any good help with my wirelss adapter please tell me.

[B]Also, which of these do I have to download, none of them are .deb files.
Cabextract package page: [http://packages.ubuntu.com/breezy/utils/cabextract](http://packages.ubuntu.com/breezy/utils/cabextract)
Unshield package page:
[http://packages.ubuntu.com/breezy/utils/unshield](http://packages.ubuntu.com/breezy/utils/unshield)[/B]

---

### Post by nanotube on 2006-05-02
should be pretty easy, since according to this [http://packages.ubuntu.com/breezy/utils/cabextract](http://packages.ubuntu.com/breezy/utils/cabextract)
the only dependency is libc6. and that should be included in the default install. so... i guess you lucked out on this one. :)

libunshield ([http://packages.ubuntu.com/breezy/utils/unshield](http://packages.ubuntu.com/breezy/utils/unshield)) shows a few more deps, but not too many.

for your wg111v1, i would suggest simply searching google, or these forums, to see if there is already a howto or something for it. you might have an easier time getting unshield, etc to install, if you first connect with the wired ethernet, and get those installed with apt-get...

---

### Post by bugme on 2006-05-02
So let me get this straight,
All I have to do is download those two .deb files then download all the dependencies?
Also, how do I install .deb files?

---

### Post by aysiu on 2006-05-02
[QUOTE=bugme]
Also, which of these do I have to download, none of them are .deb files.[/QUOTE] I linked to the .deb package for cabextract.

[quote=nanotube]the only dependency is libc6. and that should be included in the default install.[/quote] [I don't see *libc6* in *ubuntu-desktop*'s dependencies](http://packages.ubuntu.com/breezy/base/ubuntu-desktop).

To install *cabextract*, copy it to your desktop and then go to the terminal and type this: ```
cd ~/Desktop
sudo dpkg -i cabextract*.deb
```

---

### Post by bugme on 2006-05-02
And I do the same thinng for the other .deb files?
Also does it matter in what order I install the dependencies?

---

### Post by nanotube on 2006-05-02
[QUOTE=aysiu]I linked to the .deb package for cabextract.
[/quote]
you can also just click on the architecture (i386, i presume for you), on the packages.ubuntu.com site, and that will download you the .deb. but aysiu's link is just as good...
 > [I don't see *libc6* in *ubuntu-desktop*'s dependencies](http://packages.ubuntu.com/breezy/base/ubuntu-desktop).

libc6 is a basic system dependency. just about every program needs libc6 to run. check description in [http://packages.ubuntu.com/breezy/base/libc6](http://packages.ubuntu.com/breezy/base/libc6)

---

### Post by aysiu on 2006-05-02
[QUOTE=bugme]And I do the same thinng for the other .deb files?
Also does it matter in what order I install the dependencies?[/QUOTE] What'll happen... is you'll try to install a .deb. If it's missing dependencies, it'll error out and tell you what dependencies are missing. This is the pain of not having an internet connection. Ordinarily, if you apt-get installed cabextract, all the dependencies would be downloaded and installed with it.

As it is, if you know what's dependent on what, you can install the base dependencies first and work your way up.

[quote=nanotube]libc6 is a basic system dependency. just about every program needs libc6 to run.[/quote] I guess you're right. Any reason why it wouldn't be listed as a dependency of *ubuntu-desktop*?
For example, if A depends on B, which depends on C, which in turn depends on D and E; then you should install D and E first, then C, then B, then A.

However, you most likely won't know about the existence of E unless you try to install A.

---

### Post by bugme on 2006-05-02
Thanks for the help,
If I encounter any more problems, I will post in this thread again.
Thanks again.

---

### Post by nanotube on 2006-05-02
[QUOTE=aysiu]
 I guess you're right. Any reason why it wouldn't be listed as a dependency of *ubuntu-desktop*?
[/QUOTE]
well, the reason it's not listed is that (afaik) the dependencies usually list only the direct dependencies. so if A depends on B, and B depends on C, the dependencies list for A will just list B, not B and C. since ubuntu-desktop is just a meta-package to pull in a bunch of desktopy stuff, and does not itself directly depend on libc6, it does not list it.

---

### Post by aysiu on 2006-05-02
[QUOTE=nanotube]well, the reason it's not listed is that (afaik) the dependencies usually list only the direct dependencies. so if A depends on B, and B depends on C, the dependencies list for A will just list B, not B and C. since ubuntu-desktop is just a meta-package to pull in a bunch of desktopy stuff, and does not itself directly depend on libc6, it does not list it.[/QUOTE] Gotcha.

---

