---
title: "[SOLVED] Cannot remove linux-386 without upgrading it (but I already have linux-686!!"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by catanzag on 2006-10-21
Hi folk,

I've a little trouble with removal an old kernel. When I installed Dapper, kernel 2.6.15-23-386 was installed, then I installed 2.6.15-23-686, which I currently use and is fully configured. So I don't need old 386 kernel, but, when I try to uninstall it (with restricted modules and headers), Synaptic wants to install the new 2.6.15-27-386: but I don't need it, I don't want it, I've still a 686 working version!!!

Is there a way to force the removal of the old kernel without updating?

Thank you in advance and best regards

catanzag

---

### Post by catanzag on 2006-11-02
Hi all,

at the end I found a solution on myself; probably a better one is possible, but it works, it leaves apt database consistent and free 108MB of wasted space, so I would like to share with all the community.

What I did is to remove all the repositories, apart installation dvd, and then remove unused kernel. Operatively, first I backupped the repository list

```
$ sudo cp -p /etc/apt/sources.list /etc/apt/sources.list.bck
```

then I edit the file

```
$ sudo vi /etc/apt/sources.list
```

(or with any other editor) and commented out ALL the lines except the one starting with deb cdrom; then

```
$ sudo apt-get update
$ sudo apt-get remove linux-386 linux-restricted-modules-2.6.15-23-386 linux-headers-2.6.15-23-386 linux-image-2.6.15-23-386
```

make the rest. At the end

```
$ sudo cp -p /etc/apt/sources.list /etc/apt/sources.list.bck
$ sudo apt-get update
```

reset the initial status.

regards

catanzag

---

