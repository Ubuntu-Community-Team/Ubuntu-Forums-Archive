---
title: "problem with apt-get update"
date: 2005-07-05
forum: Absolute Beginner Talk
---

### Post by beamo on 2005-07-05
I keep getting errors when I try to use apt-get update and I have no idea how to fix this. These are the errors

```
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```


I really appreciate all the help I'm getting here.

---

### Post by Lunde on 2005-07-05
You should'nt use the marillat repositories. The backports will cover the software from there anyway.

Try sticking to these:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

