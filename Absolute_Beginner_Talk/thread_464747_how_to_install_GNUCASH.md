---
title: "how to install GNUCASH"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by hamlet32 on 2007-06-05
i was using gnucash in windows xp and was happy with it. i dont know how to install and where to find the installation file of gucash for linux

---

### Post by dpar on 2007-06-05
It's in synaptic.

---

### Post by dpar on 2007-06-05
Sorry, maybe I was being too cryptic:)

Goto System>Administration>Synaptic Package Manager
Type in your password
Do a search for gnucash

---

### Post by rocka on 2007-06-07
what do you do if it's not listed in Synaptic?

:confused:

---

### Post by Mazza558 on 2007-06-07
It should be in Add/Remove programs.

---

### Post by Inxsible on 2007-06-07
```
sudo aptitude install gnucash
```
 
Or 
 
```
 
sudo apt-get install gnucash

```

---

### Post by rocka on 2007-06-07
> **Inxsible said:**
> ```
sudo aptitude install gnucash
```
 
Or 
 
```
 
sudo apt-get install gnucash

```

Hi,
thanks for your replies.
I tried the first one and got this:
```
merlin@merlin-desktop:~$ sudo aptitude install gnucash
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "gnucash"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
merlin@merlin-desktop:~$
```
The second one returned this:
```
merlin@merlin-desktop:~$ sudo apt-get install gnucash
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gnucash
merlin@merlin-desktop:~$
```

I've been looking on the gnucash website, but couldn't find any install instructions at all. I downloaded the docs, but they start with the assumption that it's already installed.

---

### Post by rocka on 2007-06-07
> **Mazza558 said:**
> It should be in Add/Remove programs.

Where do you find this "Add/Remove programs"?
I couldn't find it in Synaptic anywhere.
Is it supposed to be in the applications menu? It's not there on my system [*Ubuntu 6.06 LTS - the Dapper Drake*]

I know where it is in XP, but although I read somewhere that the latest version of gnucash is supposed to be available for XP I couldn't see anything that resembled a .exe or .zip in the download list at [http://www.gnucash.org/pub/](http://www.gnucash.org/pub/)

---

### Post by MeeMaw on 2007-06-07
Add/Remove Programs is in the Applications menu. Assuming you have enabled all the repositories, it should be in the list of programs you can install. If you can't find it, then there is a search function in Synaptic - type in gnucash.

If you haven't enabled all the repositories, you can follow this;
[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/extra-repositories.html)

Are you sure you were using it in XP?  GnuCash's website doesn't have anything about a version for XP - only Linux and MacOS.

;)

---

