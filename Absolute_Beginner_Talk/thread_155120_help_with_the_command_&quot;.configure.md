---
title: "help with the command &quot;./configure"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by tikas on 2006-04-04
every time i try the "./configure" command it comes up with an error message...the same one:

 configure: error: C compiler cannot create executables
See `config.log' for more details.

my current directory is correct.....i have g++ and the supporting pagages.....
why isn't it working? please help.

thanks in advance

---

### Post by Randomskk on 2006-04-04
sudo apt-get install build-essential

---

### Post by xenmax on 2006-04-04
I did a google on your err msg and got these links:

[http://www.redhat.com/archives/rpm-list/2003-May/msg00003.html](http://www.redhat.com/archives/rpm-list/2003-May/msg00003.html)

[http://www.linuxforums.org/forum/linux-programming-scripting/90-c-compiler-cannot-create-executables-configure-error.html](http://www.linuxforums.org/forum/linux-programming-scripting/90-c-compiler-cannot-create-executables-configure-error.html)

[http://ubuntuforums.org/showthread.php?t=17033](http://ubuntuforums.org/showthread.php?t=17033)

[http://ubuntuforums.org/archive/index.php/t-91073.html](http://ubuntuforums.org/archive/index.php/t-91073.html)


I suggest you try links of ubuntuforums first - it might be more relevant. Hope this helps.

---

### Post by johnnymac on 2006-04-04
What are you trying to build??

---

### Post by tikas on 2006-04-04
humm......still not working....
@johnnymac:
trying to get; python, samba and a beep music player plugin that allowes you to play wma files to work/install

---

### Post by tikas on 2006-04-04
<name>@<comp name>:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
E: Broken packages
<name>@<comp name>:~$

is what i get when i type
"sudo apt-get install build-essential"

---

### Post by Randomskk on 2006-04-04
Try:
sudo apt-get update
sudo apt-get install libc-dev libc6-dev build-essential


If that doesn't work, search the forums for adding the Universe repositories to your sources.list..

---

### Post by tikas on 2006-04-04
humm....nope i'll try searching forums

---

### Post by catlett on 2006-04-04
try```
 sudo apt-get -f install build essential
```
The -f is for fix problem or force the install. It will try to install even though there are dependency issues.

---

### Post by tikas on 2006-04-05
ok..tried that got:

```
<user>@<computer name>:~$ sudo apt-get -f install build essential
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package build
<user>@<comp name>:~$

```

as it said:
 > You may want to run apt-get update to correct these problems

i did......then i got:

```
<user>@<computer name>:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
<user>@<computer name>:~$
```

hummm.....:-k  what now?

---

### Post by YuHoo on 2006-04-05
apt-get is a sudo program.

sudo stands for super user do, and it has taken the place of the root/administration account now (*sigh* I miss root). You need to run sudo apt-get ... to clear it up. It will also ask for a password, don't worry, you just use the same one that logs you into your account when you boot up. 

This cleared up my compiling issues 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gcc-3.4 gcc g++
sudo apt-get install build-essential
```
This will go to the sources list, download these three files (gnu c compiler) and then it will be able to turn all those .h files and what not into the program. 

As a general rule when you need to compile the source code into the program you run: 
```
make
make install
```

and if you want to uninstall it later just run make uninstall.

Welcome to the world of linux, it's like learning latin, at first you tear your hair out because it's so different, but after you master it, there is no way you go back.

P.S. Could you investigate the config.log and copy the contents if these previous steps do not clear it up? Log files are incredibly helpful sometimes because they reveal what you computer doesn't tell you.

---

### Post by catlett on 2006-04-05
Didn't see the last post. So I'm taking mine away. Sudo was already mentioned.

---

### Post by tikas on 2006-04-07
it works fine until i get to the last  stage
```
make
make install
```

i get 

```
<user>@<computer name>:~/Desktop/Downloads/Python-2.4.3$ make
case $MAKEFLAGS in \
*-s*)  CC='gcc -pthread' LDSHARED='gcc -pthread -shared' OPT='-DNDEBUG -g -O3 -Wall -Wstrict-prototypes' ./python -E ./setup.py -q build;; \
*)  CC='gcc -pthread' LDSHARED='gcc -pthread -shared' OPT='-DNDEBUG -g -O3 -Wall -Wstrict-prototypes' ./python -E ./setup.py build;; \
esac
running build
running build_ext
INFO: Can't locate Tcl/Tk libs and/or headers
running build_scripts
<user>@<computer name>:~/Desktop/Downloads/Python-2.4.3$ make install
/usr/bin/install -c python /usr/local/bin/python2.4
/usr/bin/install: cannot create regular file `/usr/local/bin/python2.4': Permission denied
make: *** [altbininstall] Error 1
<user>@<computer name>:~/Desktop/Downloads/Python-2.4.3$
```

its fine until there all the other parts worked, (thanks for that) but it just won't let me do: "make"
"make install"

what am i doing wrong?
(incase you hadnt guessed i'm trying to  install python, but it is not just python that it does this too)

---

### Post by jmalin on 2006-04-07
[QUOTE=Randomskk]sudo apt-get install build-essential[/QUOTE]

For me this fixed the problem.

I am a newbie, so...

Newbies, note that Ubuntu is pretty smart about installing packages during initial installation. It doesn't overwhelm your system the way that Red Hat ES3 and the like do.

This means that "out of the box" Ubuntu may not be ready for development, including building stuff you download from elsewhere. 

This actually has upsides, IMHO: You only need one CD to start, you install only the stuff you need, and you learn a bit about Un*x by running the packager, which BTW is easily available from the System > Administration menu of the Gnome main menu.:D

---

### Post by dvarsam on 2006-04-08
Hello, this is a part of what I did:

> So, here is the HowTo:

For Ubuntu v5.10 Breezy:

Note:
I assume that you have performed an Ubuntu clean/fresh Install.
But it should NOT really matter, as long as you follow the instructions below...

Step 1:
You need to install the following Packages:

a. Using "Synaptic Package Manager", install:

1. build-essential
2. gcc-4.0
3. linux-headers-2.6.12-9-386_2.6.12-9.23_i386.deb
4. cpp-3.4_3.4.4-6ubuntu8.1_i386.deb
5. gcc-3.4_3.4.4-6ubuntu8.1_i386.deb

Notes:
1. I think #2 gets auto-installed by #1, you might want to verify this...
2. Above #4 & #5 means downgrading your "gcc-4.0" but this is
a requirement if you want to compile the Intel's "e1000" LAN driver.
I also thing that if you install #5, #4 gets auto-installed, you might
want to verify this also...

OR: Alternatively:

b. Going independent & installing the packages one-by-one:

01. dpkg -i binutils_2.16.1-2ubuntu6_i386.deb
02. dpkg -i make_3.80-9_i386.deb
03. dpkg -i dpkg-dev_1.13.10ubuntu4_all.deb
04. dpkg -i gcc-4.0_4.0.1-4ubuntu9_i386.deb
05. dpkg -i linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb
06. dpkg -i gcc_4%3a4.0.1-3_i386.deb
07. dpkg -i libc6_2.3.5-1ubuntu12.5.10.1_i386.deb
08. dpkg -i libc6-dev_2.3.5-1ubuntu12.5.10.1_i386.deb
09-11: dpkg -i g++-4.0_4.0.1-4ubuntu9_i386.deb g++_4%3a4.0.1-3_i386.deb libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb
12: dpkg -i build-essential_11.1_i386.deb
13. dpkg -i linux-headers-2.6.12-9_2.6.12-9.23_i386.deb
14. dpkg -i linux-headers-2.6.12-9-386_2.6.12-9.23_i386.deb
15. dpkg -i gcc-3.4-base_3.4.4-6ubuntu8.1_i386.deb
16. dpkg -i cpp-3.4_3.4.4-6ubuntu8.1_i386.deb
17. dpkg -i gcc-3.4_3.4.4-6ubuntu8.1_i386.deb

I would suggest to you to read Article#: 154532

[http://ubuntuforums.org/showthread.php?t=154532&page=8](http://ubuntuforums.org/showthread.php?t=154532&page=8)

At least, the above files were the ones I installed to "make" a program.

Good luck!

---

### Post by tikas on 2006-04-10
lol.....nope brick wall here we come......](*,) :P
still nothing....
code and errors still the same......
what to do now.........
hummmm.........
any ideas?
is this sort of  thing common?

---

### Post by halfvolle melk on 2006-04-10
Issue the make install as root, ie:
```
sudo make install
```
That should do it.

---

### Post by kingborel on 2006-04-16
[QUOTE=jmalin]For me this fixed the problem.
[/QUOTE]

When i try to install build-essential, i get the following error:

```

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
E: Broken packages

```

I've installed all the compilers (gcc, g++, cpp, etc). The only problem i can think of is that i'm running the AMD64 version of breezy :(

---

### Post by paulyche on 2006-04-19
Running up to date Dapper. 

sudo ./configure gives 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables



I have build-essential, gcc4.0, g++

running export outputs 
declare -x cc="gcc"
so I think my gcc compiler is being used.

(Trying to compile libmtp.0.0.2 by the way)

Might be a Dapper issue mind you. I've been able to compile on earlier dapper flights.

---

### Post by paulyche on 2006-04-19
Oops didn't mean to put this this is this section. Ignore the above.

---

### Post by Bloch on 2006-04-19
I think it's fair to add, seeing as this is a beginners' thread, that compiling programs is not something a newbie is expected to do. You can happily live your entire linux life without compiling.

I just wouldn't like any beginners to get scared off by looking at this thread and seeing how many problems this guy appears to encounter. There are no real problems - he's just chosen the steep and rocky path up.
And good luck to him.

---

### Post by croak77 on 2006-04-19
> **tikas]it works fine until i get to the last  stage
```
make
make install
```

i get 

```
<user>@<computer name>:~/Desktop/Downloads/Python-2.4.3$ make
case $MAKEFLAGS in \
*-s*)  CC='gcc -pthread' LDSHARED='gcc -pthread -shared' OPT='-DNDEBUG -g -O3 -Wall -Wstrict-prototypes' ./python -E ./setup.py -q build said:**
>  Error 1
<user>@<computer name>:~/Desktop/Downloads/Python-2.4.3$
```

its fine until there all the other parts worked, (thanks for that) but it just won't let me do: "make"
"make install"

what am i doing wrong?
(incase you hadnt guessed i'm trying to  install python, but it is not just python that it does this too)

See the 'INFO: Can't locate Tcl/Tk libs and/or headers'  that usually means you're missing tcl/tk libs. You need to install tk8.4-dev and tcl8.4-dev.

And you need to run sudo make install after make.

---

