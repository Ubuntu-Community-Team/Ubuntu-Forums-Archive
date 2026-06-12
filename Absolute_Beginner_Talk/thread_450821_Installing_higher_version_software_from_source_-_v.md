---
title: "Installing higher version software from source - version conflicts"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by marx2k on 2007-05-21
Sorry I couldnt make the topic clearer than that.

What I am trying to do is install beryl-plugins.  In order to do that, I need to upgrade librsvg2-2

```

 sudo aptitude install  beryl-pluginsPassword:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  beryl-plugins 
The following packages have been automatically kept back:
  beryl-settings-bindings 
1 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 414kB of archives. After unpacking 393kB will be freed.
The following packages have unmet dependencies:
  beryl-plugins: Depends: librsvg2-2 (>= 2.16.1) but 2.16.0-0ubuntu2 is installed.

```

So I compiled and installed from [http://packages.debian.org/unstable/libs/librsvg2-2](http://packages.debian.org/unstable/libs/librsvg2-2)

Everything seemed to go ok, but when I try to install beryl-plugins again, it gives me the same issue. It says I am still using 2.16.0-0ubuntu2

If I try to REMOVE 2.16.0-0ubuntu2, it warns me that it will break a number of packages so I don't try it.

Does anyone know why installing from source didn't seem tp alert my system to the newer version package? Is there a symlink I have to make somewhere?

Same issue here for a different package:

```

marx2k@Commodore-64:~/source/librsvg-2.12.5$ sudo aptitude install  beryl-settings-bindings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  beryl-settings-bindings 
The following packages have been automatically kept back:
  beryl-plugins 
1 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 37.7kB of archives. After unpacking 369kB will be freed.
The following packages have unmet dependencies:
  beryl-settings-bindings: Depends: python (< 2.5) but 2.5.1-0ubuntu3 is installed.

```

---

### Post by Happy_Man on 2007-05-21
You need to downgrade python below version 2.5 to fix this all, I think... or at least fix the beryl-settings-bindings package.

---

### Post by marx2k on 2007-05-21
Tried:

marx2k@Commodore-64:/usr/lib$ ln -s librsvg-2.so.2.16.1 /usr/local/lib/librsvg-2.so.2.16.1

Still same issue...

Also tried:

marx2k@Commodore-64:/usr/lib$ sudo ln -s /usr/local/lib/librsvg-2.so.2 librsvg-2.so.2

Still same issue...

Where does the system actually do a check to see if a version of a file is installed? Because I do have both version sitting in the same drectory..

```

marx2k@Commodore-64:/usr/lib$ ls -al librsv*
lrwxrwxrwx 1 root root     19 2006-12-03 18:44 librsvg-2.so.2 -> librsvg-2.so.2.16.0
-rw-r--r-- 1 root root 196748 2006-10-10 07:42 librsvg-2.so.2.16.0
lrwxrwxrwx 1 root root     34 2007-05-21 17:34 librsvg-2.so.2.16.1 -> /usr/local/lib/librsvg-2.so.2.16.1

```

and

```

marx2k@Commodore-64:/usr/local/lib$ ls -al librsv*
-rw-r--r-- 1 root root 1213582 2007-05-21 16:26 librsvg-2.a
-rwxr-xr-x 1 root root    1271 2007-05-21 16:26 librsvg-2.la
lrwxrwxrwx 1 root root      19 2007-05-21 16:26 librsvg-2.so -> librsvg-2.so.2.16.1
lrwxrwxrwx 1 root root      19 2007-05-21 16:26 librsvg-2.so.2 -> librsvg-2.so.2.16.1
-rwxr-xr-x 1 root root  705704 2007-05-21 16:22 librsvg-2.so.2.12.5
-rwxr-xr-x 1 root root  771710 2007-05-21 16:26 librsvg-2.so.2.16.1

```

So how do I get the system to recognize that it IS in fact installed?

---

### Post by marx2k on 2007-05-21
Couldnt I just install a python library that is below 2.5 without removing the one I have which will break a few packages?

---

### Post by marx2k on 2007-05-21
It looks to be that some of my problem (if not all of it) is that the 'make install' installed into /usr/local/lib when it shouldve installed into /usr/lib

Is there a feature with typical setups like this that will change the default install path? A flag of some sort?

I got this during installation...

```

Libraries have been installed in:
   /usr/local/lib/gtk-2.0/2.10.0/engines

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

```

So does that tell me anything?

---

### Post by marx2k on 2007-05-21
Ok apparently that didnt fix the issue... 

I did ./configure --prefix=/usr

and it seemed to install to the correct directory...

[code]
Libraries have been installed in:
   /usr/lib/gtk-2.0/2.10.0/engines

...etc etc...
[/coe]

But still it's not recognizing that the version is updated

---

### Post by Bachstelze on 2007-05-21
Of course it doesn't ! How is apt supposed to know what you installed from source ?

You can use checkinstall to build a Debian package for it instead of just installing it directly. That way, apt will recognize it.

---

### Post by marx2k on 2007-05-21
I tried that but checkinstall ran into errors... observe...
```

Selecting previously deselected package librsvg.
(Reading database ... 177143 files and directories currently installed.)
Unpacking librsvg (from .../librsvg_2.16.1-1_i386.deb) ...
dpkg: error processing /home/marx2k/source/librsvg-2.16.1/librsvg_2.16.1-1_i386.deb (--install):
 trying to overwrite `/usr/share/pixmaps/svg-viewer.svg', which is also in package librsvg2-bin
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/marx2k/source/librsvg-2.16.1/librsvg_2.16.1-1_i386.deb

```

That was actually attempted BEFORE trying all this other stuff out :( 

I dont see why it can't just overwrite the file. Should I try a manual delete of /usr/share/pixmaps/svg-viewer.svg  and try again or will this break packages depending on the previous version of that file, whatever it may do?

---

### Post by Bachstelze on 2007-05-21
You need to remove the Ubuntu package before installing your own, to avoid conflicts. Also, as you can see, your package is called librsvg, while Ubunbut's is called librsvg2-bin. If you want the package to be updated, they must have the same name.

---

### Post by marx2k on 2007-05-21
Ok this is kind of freaking me out :) 

I did  sudo mv /usr/share/pixmaps/svg-viewer.svg /usr/share/pixmaps/svg-viewer.svg.old
Tried it one more time JUST TO BE SURE..
and got mv: cannot stat `/usr/share/pixmaps/svg-viewer.svg': No such file or directory (as expected)

then tried to use checkinstall once more...

```

(Reading database ... 177143 files and directories currently installed.)
Unpacking librsvg (from .../librsvg_2.16.1-1_i386.deb) ...
dpkg: error processing /home/marx2k/source/librsvg-2.16.1/librsvg_2.16.1-1_i386.deb (--install):
 trying to overwrite `/usr/share/pixmaps/svg-viewer.svg', which is also in package librsvg2-bin
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/marx2k/source/librsvg-2.16.1/librsvg_2.16.1-1_i386.deb

```

Same error..

But the file DOES NOT EXIST!

---

### Post by Bachstelze on 2007-05-21
Whether the file exists or not doesn't matter. Apt sees you have the package librsvg2-bin installed, and that this package installs the file /usr/share/pixmaps/svg-viewer.svg. Now, you try to install librsvg, which has the same file in it. It definitely won't work. As I said, you can either remove Ubuntu's package or rename yours so both have the same name and Apt recognizes it as an upgrade, not as installation of a new package.

---

### Post by marx2k on 2007-05-21
I would try removing the old package but...

```

marx2k@Commodore-64:~/source/librsvg-2.16.1$ sudo aptitude remove  librsvg2-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  beryl-plugins compiz-plugins gdm gnome-compiz-manager libgnome-compiz-manager0 libgnome2.0-cil librsvg2-bin librsvg2-common libslab0 nautilus 
  python-gnome2-desktop 
The following packages have been automatically kept back:
  beryl-settings-bindings 
The following packages will be REMOVED:
  librsvg2-2 
0 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 307kB will be freed.
The following packages have unmet dependencies:
  libgnome-compiz-manager0: Depends: librsvg2-2 (>= 2.14.4) but it is not installable
  nautilus: Depends: librsvg2-2 (>= 2.14.4) but it is not installable
  libgnome2.0-cil: Depends: librsvg2-2 (>= 2.14.4) but it is not installable
  compiz-plugins: Depends: librsvg2-2 (>= 2.14.4) but it is not installable
  gdm: Depends: librsvg2-2 (>= 2.14.4) but it is not installable
  libslab0: Depends: librsvg2-2 (>= 2.14.4) but it is not installable
  beryl-plugins: Depends: librsvg2-2 (>= 2.14.4) but it is not installable
  librsvg2-bin: Depends: librsvg2-2 (>= 2.16.0-0ubuntu2) but it is not installable
  python-gnome2-desktop: Depends: librsvg2-2 (>= 2.14.4) but it is not installable
  gnome-compiz-manager: Depends: librsvg2-2 (>= 2.14.4) but it is not installable
  librsvg2-common: Depends: librsvg2-2 (= 2.16.0-0ubuntu2) but it is not installable
Resolving dependencies...
open: 6513; closed: 4543; defer: 0; conflict/break: 28                                                                                                    oNo solution found within the allotted time.  Try harder? [Y/n]

```

So would you be able to give some advice on this?

---

### Post by marx2k on 2007-05-21
> **HymnToLife said:**
> Whether the file exists or not doesn't matter. Apt sees you have the package librsvg2-bin installed, and that this package installs the file /usr/share/pixmaps/svg-viewer.svg. Now, you try to install librsvg, which has the same file in it. It definitely won't work. As I said, you can either remove Ubuntu's package or rename yours so both have the same name and Apt recognizes it as an upgrade, not as installation of a new package.


I would go with option #2 but how do I rename my package and install it properly for this to work?  I have never done this.

---

### Post by Bachstelze on 2007-05-21
There's an option for it in checkinstall. Or at least there is one when I use it to make Slackware packages, I think it works the same for Debian ones..

---

### Post by marx2k on 2007-05-21
Oh boy...

```

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@Commodore-64 ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ librsvg ]
3 -  Version: [ 2.16.1 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ librsvg-2.16.1 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 2
Enter new name: 
>> librsvg2-bin

This package will be built according to these values: 

0 -  Maintainer: [ root@Commodore-64 ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ librsvg2-bin ]
3 -  Version: [ 2.16.1 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ librsvg-2.16.1 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

```

And went on to try to install but now we have...

```

(Reading database ... 177143 files and directories currently installed.)
Preparing to replace librsvg2-bin 2.16.0-0ubuntu2 (using .../librsvg2-bin_2.16.1-1_i386.deb) ...
Unpacking replacement librsvg2-bin ...
dpkg: error processing /home/marx2k/source/librsvg-2.16.1/librsvg2-bin_2.16.1-1_i386.deb (--install):
 trying to overwrite `/usr/bin/ld', which is also in package binutils
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/marx2k/source/librsvg-2.16.1/librsvg2-bin_2.16.1-1_i386.deb

```

And I wonder if that issue is being hit before or after the previous issue.

---

