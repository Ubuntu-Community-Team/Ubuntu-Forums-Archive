---
title: "Synaptic problems"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by evilc on 2006-10-23
I am having a problem with Synaptic I tried to reload and got this E: Archive directory /var/cache/apt/archives/partial is missing. Now if I try to d/l any programs itdon't work, how can I fix it?

TIA

---

### Post by fatsheep on 2006-10-23
> **evilc said:**
> I am having a problem with Synaptic I tried to reload and got this E: Archive directory /var/cache/apt/archives/partial is missing. Now if I try to d/l any programs itdon't work, how can I fix it?

TIA

Try this:

> sudo apt-get update && sudo apt-get upgrade

If you get errors please post them, they'll probably be more informative then the one you got in synaptic.

---

### Post by Kateikyoushi on 2006-10-23
> /var/cache/apt/archives/partial/ storage area for package files in transit.

Maybe you just deleted that folder and all you need is create it again.

---

### Post by evilc on 2006-10-23
> **Kateikyoushi said:**
> Maybe you just deleted that folder and all you need is create it again.

Thanks that was it

edit:

now when I run apt-get update I get
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

---

### Post by Malakia on 2006-10-24
That because you need to run sudp apt-get update or sudo aptitude update. Thats why your getting the permission denied.

---

### Post by evilc on 2006-10-24
Did that now when I try to reload I get a box saying "Could not download all repository indexes.

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

In the info box:
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

---

