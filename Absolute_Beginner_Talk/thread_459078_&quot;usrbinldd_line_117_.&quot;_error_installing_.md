---
title: "&quot;/usr/bin/ldd: line 117: ./&quot; error installing tar.gz file"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by ammmom on 2007-05-30
I'm trying to install a tar.gz file and I'm having great difficulty.  TIA to anyone who can help me.
> -desktop:~$ sudo aptitude install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
-desktop:~$ cd Desktop/acllinux.smotif.tar.gz_FILES
-desktop:~/Desktop/acllinux.smotif.tar.gz_FILES$ ldd acrossl
/usr/bin/ldd: line 117: ./acrossl: No such file or directory


The directions from the readme file are
> 
2.1 Dynamic libraries

	The program is dynamically linked to the following libraries which
must exist in a path searched by the loader in order to run the program:

	libXt.so.6		(X11R6 tested with 6.0 libraries)
	libXext.so.6
	libX11.so.6
	libc.so.5		(tested with 5.2.18)
	libSM.so.6
	libICE.so.6

	libXpm.so.4		(tested with 4.7)
	libg++.so.27		(tested with 27.1.0 which is actually 2.7.1.0)
	libstdc++.so.27			"
	libm.so.5		(tested with 5.0.5)

in the statically linked to Motif version and additionally to

	libXm.so.2.0

in the dynamically linked version. Due to the way, the Motif library was created
by our vendor, the loader will not look in /usr/X11R6/lib for the Motif
library where it is usually installed. The library (or a symbolic link to it)
must be present in /usr/lib.

All the above libraries except for libXm.so.2.0 are part of standard Linux
installations. The executable is in ELF format and will only run on ELF
linux distributions with appropriate ELF shared libraries.

The paths to all directories in which the above libraries are placed must be
searchable by the loader either as a default or through a specification of
the path in the LD_LIBRARY_PATH environment variable. Please consult a
Linux FAQ or guide and/or your shell documentation for details.

To check that all libraries are installed and accessible, type

	ldd acrossl

There should not be a (not found) entry in the list of dynamically linked
entries.

If the libraries can be found, then you are ready to run Across Lite except
for on-line help.

---

### Post by Cypher on 2007-05-30
In the **Desktop/acllinux.smotif.tar.gz_FILES** directory show us the output of
```

ls -l

```

---

### Post by ammmom on 2007-05-30
> **Cypher said:**
> In the **Desktop/acllinux.smotif.tar.gz_FILES** directory show us the output of
```

ls -l

``` 
Thank you Cypher.  Sorry, I don't understand what I'm suppose to do.  Would you break it down for me a bit? Is my next step to go to terminal and enter ```

ls -l

```
and then, in the file directory ask for ```

 ldd acrossl

```

TIA

---

### Post by ammmom on 2007-05-30
Can anyone tell me what to do next?


> -desktop:~/Desktop/acllinux.smotif.tar.gz_FILES$ ls -l
total 1264
-rwxr-xr-x 1  1266040 1997-01-09 13:18 acrossl
-rw-r--r-- 1 t    4006 1995-12-18 02:35 LICENSE
drwxr-xr-x 2    4096 1997-01-06 00:13 man
drwxr-xr-x 2    4096 1997-01-06 00:12 Puzzles
-rw-r--r-- 1     5210 1997-01-09 20:09 README


---

### Post by Cypher on 2007-05-30
OK, it looks like the file you need is there. In the same terminal type
```

which ldd
file `which ldd`

```
Those are "back-ticks" on the second line.

Either way, try executing the program with
```

./acrossl

```
from that directory and see what happens..

---

### Post by ammmom on 2007-06-01
> **Cypher said:**
> OK, it looks like the file you need is there. In the same terminal type
```

which ldd
file `which ldd`

```
Those are "back-ticks" on the second line.

Either way, try executing the program with
```

./acrossl

```
from that directory and see what happens..

Thank you so much.  I think that the package must hate me.  I still don't have any luck. :( :confused:

> -desktop:~$ cd Desktop/acllinux.smotif.tar.gz_FILES
-desktop:~/Desktop/acllinux.smotif.tar.gz_FILES$ which ldd
/usr/bin/ldd
-desktop:~/Desktop/acllinux.smotif.tar.gz_FILES$ file /usr/bin/ldd
/usr/bin/ldd: Bourne-Again shell script text executable
-desktop:~/Desktop/acllinux.smotif.tar.gz_FILES$ ./acrossl
bash: ./acrossl: No such file or directory
-desktop:~/Desktop/acllinux.smotif.tar.gz_FILES$ 
any other thoughts???? TIA

---

