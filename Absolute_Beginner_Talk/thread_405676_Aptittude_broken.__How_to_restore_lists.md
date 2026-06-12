---
title: "Aptittude broken.  How to restore lists?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by brn on 2007-04-10
Synaptic Package Manager has come up lame.  All fields are blank and an unfamiliar error message declares the following problems:
> E: Dynamic MMap ran out of room
E: Error occurred while processing language-pack-gnome-ur (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
W: Duplicate sources.list entry [http://http.us.debian.org](http://http.us.debian.org) stable/main Packages (/var/lib/apt/lists/http.us.debian.org_debian_dists_stable_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://http.us.debian.org](http://http.us.debian.org) stable/contrib Packages (/var/lib/apt/lists/http.us.debian.org_debian_dists_stable_contrib_binary-i386_Packages)
W: Duplicate sources.list entry [http://http.us.debian.org](http://http.us.debian.org) stable/non-free Packages (/var/lib/apt/lists/http.us.debian.org_debian_dists_stable_non-free_binary-i386_Packages)

The first error (Dymamic MMap ran out of room) can't be referring to RAM or disk, plenty of both are available.
I think I need to completely re-install the package list but can't figure out how.  Appreciate any advice.
-Thanks-

---

### Post by justleen on 2007-04-10
try this tread [http://ubuntuforums.org/showthread.php?p=2125618](http://ubuntuforums.org/showthread.php?p=2125618)

---

### Post by akudewan on 2007-04-10
This error has something to do with the cache limit. Have a look at this page to fix it: [http://www.yak.net/fqa/416.html](http://www.yak.net/fqa/416.html)

I also notice that you have a debian repository in your sources.list. This is not at all recommended. You should remove it. Infact, it may be the cause of the cache getting full

---

### Post by dragomirov on 2007-04-10
> **brn said:**
> Synaptic Package Manager has come up lame.  All fields are blank and an unfamiliar error message declares the following problems:

The first error (Dymamic MMap ran out of room) can't be referring to RAM or disk, plenty of both are available.
I think I need to completely re-install the package list but can't figure out how.  Appreciate any advice.
-Thanks-

the DYnamic MMap means that you've reached the limit of memory for apt-get to work (not your physical RAM).
Then you can try increasing the value of memory allocated for apt-get 
```
sudo gedit /etc/apt/apt.conf 
```
then put
```
APT::Cache-Limit 12582912;
```
in the first line available.

Fo r the duplicated entry lists look in your /etc/apt/sources.list file then remove the duplicated repositories, I mean those repositories writtem twice

bye

---

### Post by brn on 2007-04-10
Deleting the debian repositories appears to have done the trick.  I think they have been there for quite awhile wihout previously causing problems.  Anyway, everything seems normal again. - My thanks to all -

---

