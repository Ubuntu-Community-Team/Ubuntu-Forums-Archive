---
title: "New repositories"
date: 2005-07-07
forum: Absolute Beginner Talk
---

### Post by filemanager on 2005-07-07
Last night when I was downloading new repositories (sudo apt-get update), I got knocked offline. So when I ran it again, I get this error at the end:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

What do I do!?  ](*,)

---

### Post by Lord Illidan on 2005-07-07
Do as it tells you...

run:

sudo apt-get update

---

### Post by filemanager on 2005-07-07
[QUOTE=Lord Illidan]Do as it tells you...

run:

sudo apt-get update[/QUOTE]
 That's what I was running originally, so when I do that I just get the same error again!

---

### Post by filemanager on 2005-07-07
bump

---

### Post by ozzie123 on 2005-07-07
sudo apt-get update works just fine here. Probably it's your connection problem?

---

### Post by filemanager on 2005-07-07
[QUOTE=ozzie123]sudo apt-get update works just fine here. Probably it's your connection problem?[/QUOTE]
 I reinstalled Linux and now it's working fine. Weird!

---

