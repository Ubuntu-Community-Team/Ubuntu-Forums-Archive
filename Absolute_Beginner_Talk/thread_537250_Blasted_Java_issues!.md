---
title: "Blasted Java issues!"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Gaius Rex on 2007-08-28
Okay so i've followed all the instructions I've found to install Java, but to no avail. The last thread I looked at gave me terminal instructions for installing it, and here's what I get:


Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse sun-java6-bin 6-00-2ubuntu2 [26.2MB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse sun-java6-jre 6-00-2ubuntu2 [6324kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse sun-java6-fonts 6-00-2ubuntu2 [1814B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse sun-java6-plugin 6-00-2ubuntu2 [1392B]
Fetched 32.5MB in 1m6s (488kB/s)                                               
Preconfiguring packages ...
Selecting previously deselected package sun-java6-bin.
(Reading database ... 126688 files and directories currently installed.)
Unpacking sun-java6-bin (from .../sun-java6-bin_6-00-2ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-00-2ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-fonts.
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6-00-2ubuntu2_all.deb) ...
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-00-2ubuntu2_i386.deb) ...
Setting up sun-java5-doc (1.5.0-11-1ubuntu2) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.




This comes up when I try to run Frostwire as well. 


I'm honestly at a loss and any help would be greatly appreciated.

---

### Post by Kralizec on 2007-08-28
Have you tried downloading the zip file and doing what it said? I had this happen to me as well and when I downloaded the file, chown'd it to root.root and moved it to /tmp everything worked smoothly.

Just follow the download link they gave you, then in a terminal:
```

sudo mv jdk-1_5_0-doc.zip /tmp
sudo chown root.root /tmp/jdk-1_5_0-doc.zip

```
and try installing again. It'll show you the EULA and make you accept the terms (If I remember right) and then it will install.

---

