---
title: "Installing Open cascade"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by bac on 2007-09-21
Hello, 
I'm trying to install Open Cascade in Ubuntu Fiesta. it downloaded as a tgz file.

How do I install it?

Is the system requirement compatible with Ubuntu?

Software requirement as below
32-bit: Debian: Sarge, Woody Fedora Core 3.0 Mandrake 7.0, 7.1, 7.2, 8.0, 10.1 Red Hat 7.1, 8.0 *, Mandriva 2006 Kernel delivered with distribution 2.2.5, 2.2.17, 2.4.2, 2.6.8 Xfree delivered with distribution 3.3.3.1, 4.0.x

Thanks.

---

### Post by hyper_ch on 2007-09-21
From the french ubuntu site [http://doc.ubuntu-fr.org/opencascade](http://doc.ubuntu-fr.org/opencascade)

(1) Install c shell
```

sudo apt-get install csh

```

(2) Install Sun Java 6
```

sudo apt-get install sun-java6-jdk

```

(3) Make sure, Sun Java 6 is used:
```

sudo update-alternatives --config java

```
Set as default the one entry that contains this string:
```

java-6-sun

```

(4) Untar the tar.gz file
```

tar xfvz /path/to/file.tar.gz

```

(5) Run the installer
```

sudo java -cp /path/to/untarred/Linux/setup.jar run

```

---

### Post by bac on 2007-09-26
Alright...It works. Thanks ya.

---

### Post by rmanni on 2007-10-16
The install process was ok for me too.
But starting the Test Suite was a bit harder. In case someone needs it too:
The test suite was meant to be started with two commands:
. /opt/OpenCASCADE6.2.0/ros/env.ksh          #set up the environment variables
/opt/OpenCASCADE6.2.0/ros/lin/bin/DRAWEXE

After this it was searching for tcl and tk libraries, so I had to create some symbolic links:
sudo ln -s /usr/lib/libtk8.4.so.0 /usr/lib/libtk.so
sudo ln -s /usr/lib/libtcl8.4.so.0 /usr/lib/libtcl.so

Of course, change the version and the path to which is valid on your system.
Ps: after this program is ok, except some debugging things and the handling of utf8....

The Manni

---

