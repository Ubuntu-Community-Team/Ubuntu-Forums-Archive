---
title: "Intrducing a friend to Ubuntu - Please help."
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by camz on 2007-03-24
Hey guys, the noob is back with another question, I'm introducing a friend to the great Ubuntu, and we are having a bit of trouble getting it on his laptop. It is quite an old computer, a Sony PCG-9G2M, and it has 256MB RAM, a 30GB Hard Drive (2 15GB drives, C: and D:), and a 1.30 GHz processor (not sure what kind). Windows is installed on the C Drive, and the D Drive is totally empty, nothing inside at all. How can we install Ubuntu as a dual boot system, so that Ubuntu goes to D drive and occupies all that space itself, and Windows is on the C Drive. When we turn the computer on we would like to be able to select which operating system to load. How can we tell Ubuntu to go to the D Drive, as when we try to install there doesn't seem to be an option. I'm familiar with the Terminal, so is there any way to do this via the terminal window inside the Live CD.

Thank you in advance:
Camz

---

### Post by mikewhatever on 2007-03-24
Delete the D partition and in the unallocated space create the Ubuntu ones (root,swap), format them and install.
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

Note that Ubuntu partitioner does not call partitions C or D, but rather /dev/hda1, /dev/hda2 etc.

---

