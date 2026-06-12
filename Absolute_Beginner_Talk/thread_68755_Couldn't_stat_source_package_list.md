---
title: "Couldn't stat source package list"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by 117 on 2005-09-24
Recently installed Ubuntu, and am getting a load of the above errors whenever I run Synaptic Package Manager or use the apt-get command, they all refer to backports.ubuntuforums, example:

> W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)

it always ends with > W: You may want to run apt-get update to correct these problems but if I do that then I just get the same errors again, help!

---

### Post by tehwa on 2005-09-24
I think it's having trouble resolving the host. Try editing /etc/apt/sources.list and removing the source that's giving you trouble.

From my understanding the forums are great for information, not so good for packages. 

```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by papangul on 2005-09-24
You might want to take a look in the [http://ubuntuguide.org/](http://ubuntuguide.org/) (again :) )

---

### Post by 117 on 2005-09-25
[QUOTE=papangul]You might want to take a look in the [http://ubuntuguide.org/](http://ubuntuguide.org/) (again :) )[/QUOTE]

ubuntuguide is for hoary, and all the repository addresses are for hoary, if i edited the word hoary to breezy in each line you reckon it'd work?

---

### Post by wkh on 2005-09-25
Disregard the people giving you veiled "RTFM/STFW" replies.

archive.ubuntu.com is down, it seems.

I used this for my /etc/apt/sources.list (you'll need to invoke your editing application with sudo -- e.g., sudo get /etc/apt/sources.list):

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted



deb [http://mirror.cs.umn.edu/ubuntu](http://mirror.cs.umn.edu/ubuntu) breezy main restricted universe multiverse

deb-src [http://mirror.cs.umn.edu/ubuntu](http://mirror.cs.umn.edu/ubuntu) breezy main restricted universe multiverse



deb [http://mirror.cs.umn.edu/ubuntu](http://mirror.cs.umn.edu/ubuntu) breezy-updates main restricted universe multiverse

deb-src [http://mirror.cs.umn.edu/ubuntu](http://mirror.cs.umn.edu/ubuntu) breezy-updates main restricted universe multiverse



deb [http://mirror.cs.umn.edu/ubuntu](http://mirror.cs.umn.edu/ubuntu) breezy-security main restricted universe multiverse

deb-src [http://mirror.cs.umn.edu/ubuntu](http://mirror.cs.umn.edu/ubuntu) breezy-security main restricted universe multiverse

```

that'll let you get unkosher/non "free" stuff like mp3 players  :roll: :roll:

---

### Post by 117 on 2005-10-03
wkh cheers, that seems t've worked now :)

---

