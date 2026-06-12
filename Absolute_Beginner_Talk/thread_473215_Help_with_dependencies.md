---
title: "Help with dependencies?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Destroyer14094 on 2007-06-13
How do I instal a dependency that GDebi won't install for me?

It tells me..."Error: Dependency is not satisfiable: libc6

I am running Ubuntu 6.06.

---

### Post by jfollmann on 2007-06-13
Try this page:

[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglibc%2Flibc6_2.5-10_i386.deb&md5sum=1b99a188671392dc4e6d06ad1b5d2ffd&arch=i386&type=main]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglibc%2Flibc6_2.5-10_i386.deb&md5sum=1b99a188671392dc4e6d06ad1b5d2ffd&arch=i386&type=main")

If you download the .deb file from any of those links, and open it, the debian package manager should install the libc6 package for you. Once that's done, the package you were trying to install to start with should install properly.

I'm not exactly a pro myself, so if someone with more experience wants to correct me, feel free. ;) But I'm reasonably sure that will work.

---

### Post by Destroyer14094 on 2007-06-13
ok, it worked, but now it wants a new dependency...libgcc1

Also, I am trying to install limewire... Maybe there is a dependency pack for it, idk.

---

### Post by zvacet on 2007-06-14
[http://packages.ubuntu.com/dapper/libs/libgcc1]("http://packages.ubuntu.com/dapper/libs/libgcc1")

Install one mark with red ball first(they are dependencies) and after that choose architecture and download file.

---

### Post by Gmbrdilos on 2007-06-14
this issue happens a lot with limewire. I'd suggest you try frostwire, which is basically a free clone.

---

