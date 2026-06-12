---
title: "apt-get update trouble..."
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by grim918 on 2005-11-09
i keep getting this message everytime i try to run apt-get update. im new to linux so i would appreciate any help that i can get. this is what i get on the screen:

Failed to fetch [http://archive.ubuntu.com/dists/ubuntu/hoary-backports/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/ubuntu/hoary-backports/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.151 80]
Failed to fetch [http://archive.ubuntu.com/dists/ubuntu/hoary-backports/source/Sources.gz](http://archive.ubuntu.com/dists/ubuntu/hoary-backports/source/Sources.gz)  404 Not Found [IP: 82.211.81.151 80]
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) ubuntu/hoary-backports Packages (/var/lib/apt/lists/archive.ubuntu.com_dists_ubuntu_hoary-backports_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

I dont know what im doing wrong can someone please help me out. thank you.

---

### Post by Pablo_Escobar on 2005-11-09
AFAIK (I'm Breezy user) both Hoary and Breezy don't have backports currently running.
Try to comment them out.

---

