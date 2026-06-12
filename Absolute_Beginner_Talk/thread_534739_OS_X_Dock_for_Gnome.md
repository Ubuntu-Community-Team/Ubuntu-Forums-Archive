---
title: "OS X Dock for Gnome"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Magneticgravity on 2007-08-25
Umm...where do i start?

Theres a few ive seen, but have no idea how to install them.

Help?

---

### Post by Golyadkin on 2007-08-25
Well, there is AWN, SimDock, Cairo-Dock, Gnome-Dock, gdesklets, and so on. Most require you to run Beryl or Compiz, but SimDock doesn't. To find out how to install them, use the search function in this forum and search for "install awn" and so on. 

This is a handy must read guide on people new to installing software in Ubuntu: How to install ANYTHING in Ubuntu!    [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Magneticgravity on 2007-08-25
OK, if i wanna install SimDock.
I download, i drag it onto Themes but it dosent seem to work.

It seems i need to do some other stuff, i need help.

---

### Post by rkrug on 2007-08-25
SimDock isn't a theme; I believe you need to compile it.

---

### Post by Magneticgravity on 2007-08-25
> **rkrug said:**
> SimDock isn't a theme; I believe you need to compile it.

Yes, how would you do that exactly. Could you please give me a rough step by step guide?
:)

---

### Post by jrieth50 on 2007-08-25
Not to be too off topic, but I've tried a couple of the various OSX dock type applications, and I find AVN to be one of the best. 

Please note: This requires compositing - aka Compiz, etc to be running. So if you don't have Compiz or Beryl this will probably not be for you.

So if you want to try it, the instructions for installation are [here]("http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository?t=anon"):

The only thing missing will be the nice reflection effect you get. Which can be added by following[ these simple instructions]("http://njpatel.blogspot.com/2007/07/so-now-that-we-have-some-depth.html") from the author's blog. (Note: the gconf file he is referring to is located in ~/.gconf/apps/avant-window-navigator/bar)

---

### Post by rkrug on 2007-08-25
> **Magneticgravity said:**
> Yes, how would you do that exactly. Could you please give me a rough step by step guide?
:)

This is taken from [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) :

"Source Package (.tar, .tar.gz, .tgz, .tar.bz, ...)
    Note: not all files with an extension named .tar, .tar.gz, and so on are archives with source code in them - they might be precompiled! If the archive is precompiled, there should be an installer or a binary executable inside it.

    Sometimes all you've got is a package full of uncompiled source code. Luckily, you don't need to be a programmer to know how to compile and install a package with source code. Back in the old days, this was the only way to install software on Linux and there is a standard way of installing these files. It will not work in every case, but it will in most (if you have the right dependencies installed). To compile a package you must first extract it somewhere. This is easily done, simply right-click on the package and select Extract Here.
    Extracting a package

    Tango video icon See a screencast of package contents being extracted
    To proceed you must have the compiler tools installed. They all come with the package build-essential, available in Synaptic. When you're sure you have the compiler tools installed, you fire up the terminal and change directory to the one you've just extracted (if you're not sure how to do that see: Navigating the terminal.

    When you're in the correct directory you execute a configure script: ./configure. The purpose of the configure script is usually to check for dependencies and then create the makefile. If the script fails for some reason and tells you to install certain packages, look up the names in Synaptic (Important! If you find packages in Synaptic named almost the same but with a -dev extension, remember to install those as well! They're development packages and are needed for compiling). Don't worry if it complains that there is no configure script - many packages don't come with one! Then you compile it with make and after it's been compiled you can install it. There are two ways:

    Normal install: If you want to install it the normal "primitive" way, type sudo make install. To remove the temporary files you run make clean. To uninstall the program you run sudo make uninstall. These two clean-up commands don't always work, though, the programmer needs to have enabled them.

    Package manager install: If you want to install it in a way that means it can be easily removed from inside the package manager, first install the package checkinstall. To install the package type sudo checkinstall. This will take slightly longer than a normal install and quite possibly you'll have to supply a description of the application yourself (and edit the other information slightly). If the need arises, this will be easy to take care of from inside the checkinstall program."

---

### Post by Magneticgravity on 2007-08-26
Hmm, thanks alot guys, OK, i used that websites help. I get this from terminal:

will@Will-Desktop:~$ cd /home/will/Desktop/trunk
will@Will-Desktop:~/Desktop/trunk$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name...
configure: error: C++ compiler cannot create executables
See `config.log' for more details.
will@Will-Desktop:~/Desktop/trunk$

---

### Post by Dark Star on 2007-08-26
Install this. 
```
sudo apt-get install g++
```
```
 sudo apt-get install build-essential
```

btw why don't you use AWN and Kiba Dock the best in Linux :D

---

### Post by Magneticgravity on 2007-08-26
OK, got this:

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


And i could install Compiz, though after reading the thread on it in this forum, im not so sure...

---

### Post by mysticmatrix on 2007-08-26
You don't need to install Compiz. A old realease is already installed. Go to System --> Preferenes -->Desktop Effects. and enable them.
You will need to install your graohics driver though. If its intel, its already installed. If its Nvidia, Ubuntu will ask and install correct one, If its ATI........ :confused:

---

### Post by Golyadkin on 2007-08-26
YOu don't need to compiile SimDock at all, just download and run this .deb file: [http://www.getdeb.net/download.php?release=1217&fpos=0](http://www.getdeb.net/download.php?release=1217&fpos=0)

It is a precompiled installer for SimDock.

---

### Post by Dark Star on 2007-08-26
> **Golyadkin said:**
> YOu don't need to compiile SimDock at all, just download and run this .deb file: [http://www.getdeb.net/download.php?release=1217&fpos=0](http://www.getdeb.net/download.php?release=1217&fpos=0)

It is a precompiled installer for SimDock.
Second that or just pop up and read my guide [http://ubuntuforums.org/showthread.php?t=490398&page=3](http://ubuntuforums.org/showthread.php?t=490398&page=3)

---

### Post by Magneticgravity on 2007-08-26
the .deb simdock gave me: 'error: Dependency is not satisfiable: libatk.0-0'

---

### Post by Dark Star on 2007-08-26
> **Dark Star said:**
> Second that or just pop up and read my guide [http://ubuntuforums.org/showthread.php?t=490398&page=3](http://ubuntuforums.org/showthread.php?t=490398&page=3)
Do check my guide :)

---

### Post by Magneticgravity on 2007-08-26
will@Will-Desktop:~$  cd/home/will/simdock
bash: cd/home/will/simdock: No such file or directory
will@Will-Desktop:~$

---

### Post by Dark Star on 2007-08-26
Have you copied the simdock folder after unzipping it in Home folder ? :?

---

### Post by yousufinternet on 2007-08-26
try to get a .deb package from [www.getdeb.net](www.getdeb.net) :)

---

### Post by Magneticgravity on 2007-08-26
Yes.

---

### Post by walkerk on 2007-08-26
> **Magneticgravity said:**
> will@Will-Desktop:~$  cd/home/will/simdock
bash: cd/home/will/simdock: No such file or directory
will@Will-Desktop:~$

cd /home/will/simdock

or

cd ~/simdock

you need a space between cd and the directory.

---

### Post by Magneticgravity on 2007-08-26
Same thing happens :(

---

### Post by Magneticgravity on 2007-08-26
Anyone...

---

### Post by Dark Star on 2007-08-26
Can you post the output plz :) Read this post :) [http://ubuntuforums.org/showpost.php?p=3231535&postcount=23](http://ubuntuforums.org/showpost.php?p=3231535&postcount=23)

---

### Post by Magneticgravity on 2007-08-26
OK, i download that file, i unzip and it extracts a folder called 'Trunk.' I copy that into /home/will.

Then on terminal, i do what you said and i get this:

will@Will-Desktop:~$ cd /home/will/simdock
bash: cd: /home/will/simdock: No such file or directory
will@Will-Desktop:~$

---

### Post by Dark Star on 2007-08-26
Why you are creating a folder trunk ? :? It will unzip itself into a Folder called SImdock no need to unzip it in diff.. folder.. :p

---

### Post by Magneticgravity on 2007-08-26
OK, if i click 'Extract here' a folder is created called: simdock_1.2.tar.gz_FILES.

If i put that into my /home/will, then do the terminal commands, i still get 'no such file or directory.'

If i extract it by double clicking i get a folder called trunk like last time.

---

### Post by Dark Star on 2007-08-26
Dude you have to do this **cd <path of fiile/folder name>** Not necessary it is simdock only :D

---

### Post by Magneticgravity on 2007-08-26
will@Will-Desktop:~$ cd /home/will/trunk
will@Will-Desktop:~/trunk$ ./configure
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

will@Will-Desktop:~/trunk$




This help?

---

### Post by Magneticgravity on 2007-08-26
Where can i download those packages?

---

### Post by Magneticgravity on 2007-08-26
...

---

### Post by Golyadkin on 2007-08-26
Try opening a terminal and typing this:
> 
sudo apt-get install simdock libatk1.0-0


Another option might be this:
> 
sudo apt-get install gdesklets

Then add the deskbar through the desklet manager.

---

