---
title: "update manager"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by none211 on 2007-08-30
I just got my ubuntu box back on line after a few months. I see there is a distro upgrade. i would really like to check it out, but I'm getting an error from the update manager. It reads as follows


Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.89.8 80]

Can anyone help with this problem?

---

### Post by sstucke on 2007-08-30
This usually means that the package is not longer available.
You can update with this command:
sudo apt-get update

Good luck!
[http://en.tuxero.com]("http://en.tuxero.com")

---

### Post by none211 on 2007-08-30
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.6 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


still a little confused... this is what I get from

sudo apt-get update

---

### Post by Anicka on 2007-08-30
Warty is old and  unsupported. I don't think you can do on-line updates from that distro to anything, but have to consider doing a clean install of something that is supported like 6.06 or 7.10. First take a look here: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) and if you can update, good luck.

---

### Post by wing25 on 2007-08-30
i tried to update my fiesty but it appears that i cant connect to the archive..

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/universe/binary-i386/Packages.gz)  Could not resolve 'archive.ubuntu.com'

needhelp

---

### Post by Anicka on 2007-08-31
> **wing25 said:**
> i tried to update my fiesty but it appears that i cant connect to the archive..

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/universe/binary-i386/Packages.gz)  Could not resolve 'archive.ubuntu.com'

needhelp

That is probably just the server being temporarily down, try again tomorrow and it would probably work.

---

