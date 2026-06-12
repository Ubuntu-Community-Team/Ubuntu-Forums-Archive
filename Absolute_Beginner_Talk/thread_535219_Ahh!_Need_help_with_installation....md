---
title: "Ahh! Need help with installation..."
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Magneticgravity on 2007-08-26
OK, i wanna install the SimDock thing, and ive been using this guys guide for help:

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)


I unzip the folder, go on to terminal and do the following:

will@Will-Desktop:~$ cd /home/will/Desktop/simdock_1.2.tar.gz_FILES
[email]will@Will-Desktop:~/Desktop/simdock_1.2.tar.gz[/email]_FILES$ ./configure
bash: ./configure: No such file or directory
[email]will@Will-Desktop:~/Desktop/simdock_1.2.tar.gz[/email]_FILES$ make
make: *** No targets specified and no makefile found. Stop.
[email]will@Will-Desktop:~/Desktop/simdock_1.2.tar.gz[/email]_FILES$

---

### Post by AlexenderReez on 2007-08-26
try to rename the folder name to other like whatever..then cd ,./configure it again...by the way...not all application provided check dependency (./configure).....something you need to straight away 'make'

---

### Post by Magneticgravity on 2007-08-26
If i try it with the 'trunk' folder, i get this:

will@Will-Desktop:~$ cd /home/will/Desktop/trunk
will@Will-Desktop:~/Desktop/trunk$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for dup2... yes
checking for sqrt... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (
        gconf-2.0 >= 2.18.0,
        libwnck-1.0 >= 2.18.0
) were not met:

No package 'gconf-2.0' found
No package 'libwnck-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

will@Will-Desktop:~/Desktop/trunk$ make
make: *** No targets specified and no makefile found. Stop.
will@Will-Desktop:~/Desktop/trunk$

---

### Post by Paul820 on 2007-08-26
Looks like you are missing two dependencies, from the terminal:

> sudo apt-get install gconf2
sudo apt-get install libwnck18

---

### Post by Magneticgravity on 2007-08-26
> **Paul820 said:**
> Looks like you are missing two dependencies, from the terminal:

Thx for your help though it says ive already got the latest versions, i tried again to find the same screen with those two missing packages.

---

### Post by aninaiian on 2007-08-26
do you have libwnck-dev and libgconf2-dev installed?

---

### Post by Paul820 on 2007-08-26
Yes, i just noticed that, you need the dev files. :(
> 
sudo apt-get install gconf2-dev
sudo apt-get install libwnck-dev

It should work with them.

---

### Post by Magneticgravity on 2007-08-26
OK guys, i download some more stuff which looked similiar to the packages i needed now:

will@Will-Desktop:~$ cd /home/will/Desktop/trunk
will@Will-Desktop:~/Desktop/trunk$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for dup2... yes
checking for sqrt... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (
        gconf-2.0 >= 2.18.0,
        libwnck-1.0 >= 2.18.0
) were not met:

No package 'gconf-2.0' found
Requested 'libwnck-1.0 >= 2.18.0' but version of libwnck is 2.14.2

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

will@Will-Desktop:~/Desktop/trunk$

---

### Post by Steveway on 2007-08-26
Simdock is on getdeb.net
You don't need to compile it yourself.

---

### Post by Magneticgravity on 2007-08-26
Yes, ive tried that, i get an error.

---

### Post by Paul820 on 2007-08-26
Read above, you need the dev files. It works because i have just built and installed it. Quite pleased aswell because it's the only dock i have managed to get working correctly on ubuntu. All the others are just black boxes. :)

---

### Post by Magneticgravity on 2007-08-26
Those dev files: the first one terminal dosent find it.
The second one ive already got.

If i try to run the .deb installer it says: Error: Dependency is not satisfiable: libatk1.0-0

---

### Post by aninaiian on 2007-08-26
Are you running Dapper (Ubuntu 6.06 LTS)?

---

### Post by Magneticgravity on 2007-08-26
yeh.....

---

### Post by mysticmatrix on 2007-08-26
> **Magneticgravity said:**
> Those dev files: the first one terminal dosent find it.
The second one ive already got.

If i try to run the .deb installer it says: Error: Dependency is not satisfiable: libatk1.0-0

On Terminal type this

```
sudo apt-get install libatk1.0-0
```

and then try to install the package.

As you use a older version of Ubuntu, this is necessary. On Feisty Fawn, this is preinstalled. (Although the command might fail if there is no repository holding this package in your version of Ubuntu)

---

### Post by Magneticgravity on 2007-08-26
OK:

will@Will-Desktop:~$ sudo apt-get install libatk1.0-0
Password:
Reading package lists... Done
Building dependency tree... Done
libatk1.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
will@Will-Desktop:~$

Should i upgrade to Feisty?

---

### Post by mysticmatrix on 2007-08-26
> **Magneticgravity said:**
> OK:

will@Will-Desktop:~$ sudo apt-get install libatk1.0-0
Password:
Reading package lists... Done
Building dependency tree... Done
libatk1.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
will@Will-Desktop:~$

Should i upgrade to Feisty?

Well then it might be the package is an older one and the program you need requires a newer one which is not included in your version just for compatibility reason.

Remember that error

> Requested 'libwnck-1.0 >= 2.18.0' but version of libwnck is 2.14.2

This is due to older versions :)

I would suggest you upgrade to Feisty(that what new releases are meant for, they are obviously better), except if you run a server or some important productivity work.
Home users are just fine with latest version.

---

### Post by Magneticgravity on 2007-08-26
So, can you just upgrade from Dapper?

---

### Post by mysticmatrix on 2007-08-26
> **Magneticgravity said:**
> So, can you just upgrade from Dapper?

Well there are methods, but you might break something if you used something non-standard, like Automatix, envy,or some other stuff not from official ubuntu repository. Also the download is quite big(You are 2 versions behind), so better option would be to clean install.

---

### Post by Magneticgravity on 2007-08-26
So i need a CD and all that again?

---

### Post by Magneticgravity on 2007-08-26
OK, when i installed Dapper i wiped my HDD and made 2 partitions, one for Xp, one for Ubuntu.

How do i wipe the Dapper driver and then install Feisty onto it.

---

### Post by mysticmatrix on 2007-08-26
Yes. You might try online upgrade. If you mess up things, do a CD install.
I am not saying online upgrade won't work, it just sometimes just does not works. Not fault of Ubuntu, but due to something non-standard like Automatix.
Also I got Simdock working easily on Feisty, just a simple download from getdeb.com and install.

Also try finding a version of Simdock .deb meant for Dapper verssion, that might help.
AFAIK, getdeb.net only has the feisty version.

---

### Post by mysticmatrix on 2007-08-26
> **Magneticgravity said:**
> OK, when i installed Dapper i wiped my HDD and made 2 partitions, one for Xp, one for Ubuntu.

How do i wipe the Dapper driver and then install Feisty onto it.

Put in live CD. When it asks for partitioning, choose Manual Partition. Then select the partitions on which Dapper is installed and tick the option to Format them and install Feisty on those drive.
You'll lose any data you have in current ubuntu, so you might wish to backup your data on your windows drive and then reinstall.

NOTE: This thing might get tricky sometime. Try getting a friend who is somewhat well experienced in installing OS. Although if you previously installed Ubuntu yourself, you will be able to do things with little precautions.

---

### Post by Magneticgravity on 2007-08-26
Yes, i did install Dapper on my own last time. It seems pretty simple, just format the partition, then install Feisty.

So, i put feisty live cd in, click 'install' bla bla, and then i should be able to format the Ubuntu drive and install Feisty on that.

OK, thank a lot mate :)

---

### Post by mysticmatrix on 2007-08-26
> **Magneticgravity said:**
> Yes, i did install Dapper on my own last time. It seems pretty simple, just format the partition, then install Feisty.

So, i put feisty live cd in, click 'install' bla bla, and then i should be able to format the Ubuntu drive and install Feisty on that.

OK, thank a lot mate :)

No it won't BY DEFAULT wipe out Dapper. You have to do that MANUALLY. Thats what I meant by taking precaution. If you let it do a automatic install, you'll end up with three OS, Dapper, Feisty and Windows instead.

---

### Post by Magneticgravity on 2007-08-26
Yeh, i know, a manual partition, so thats an option when you click the install icon on the live disc then?

---

### Post by mysticmatrix on 2007-08-26
Yes it on the Partitioning disks page. That lists something like

1) Guided Partions
2) .....
3) ......
4) MANUAL PARTITION

(I am telling this out of my head, don't remember the correct spellings and order)

So you have to select your correct Dapper Partition (which would be in some coded language like /media/sda3 or other). Also remember that on live CD, the name of drives is not same as on installed OS. 

So the moral is, if you follow little precaution, you'll be all fine.
Else who knows that you select wrong partition and wipe out windows instead :)

---

### Post by Magneticgravity on 2007-08-26
OK thanks a lot, im pretty confident, hopefully tomorrow i shall be typing this on Feisty :)

---

