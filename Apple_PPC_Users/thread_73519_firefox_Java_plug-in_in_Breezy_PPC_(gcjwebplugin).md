---
title: "firefox Java plug-in in Breezy PPC? (gcjwebplugin)"
date: 2005-10-09
forum: Apple PPC Users
---

### Post by Entity on 2005-10-09
[B]Hello, 

I followed these steps :[/B]

[http://ubuntuppc.info/index.php?node=18](http://ubuntuppc.info/index.php?node=18)

**So I have Java installed :**

[FONT="Lucida Console"]$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.[/FONT]

**gcjwebplugin also :**

[FONT="Lucida Console"]$ apt-cache showpkg gcjwebplugin
Package: gcjwebplugin
Versions:
0.3.2-1(/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-powerpc_Packages)(/var/lib/dpkg/status)[/FONT]

**And when I look at about:plugins in firefox it shows that it is install correctly :**

[FONT="Lucida Console"]GCJ web browser plug-in 0.3.2

    File name: libgcjwebplugin.so
    The GCJ web browser plug-in executes Java applets in Mozilla and other web browsers.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	GCJ 	class,jar 	Yes
application/x-java-applet 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.3 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	GCJ 	class,jar 	Yes
application/x-java-applet;jpi-version=1.4.2_01 	GCJ 	class,jar 	Yes
application/x-java-bean 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.3 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	GCJ 	class,jar 	Yes
application/x-java-bean;jpi-version=1.4.2_01 	GCJ 	class,jar 	Yes[/FONT]

**But it still doesn't work when I try to use it. For example, when I try to play a game at pogo.com I get the following error from the site :**

[FONT="Lucida Console"]Java Not Found or Not Working[/FONT]

**Does someone successfully run this java plug-in?**

---

