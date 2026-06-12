---
title: "Problems Installing Package"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by tlinux on 2007-05-24
I'm trying to install packages in Kubuntu 7.04 and am having troubles. I'm not connected to the Internet yet and am trying to set up such a connection. I need to use a browser and Konqueror may have a bug. I want to install Firefox and test it. I've copied the Firefox tar ball and checkinstall into Kubuntu. I was going to try anc convert the tar ball to a deb package first. This is the terminal output I got:


[INDENT][INDENT]tom@emachine:~$ cd /home/tom
tom@emachine:~$ ls -l
total 9781
-rwxr-xr-x 1 tom tom    5974 2007-05-24 18:24 aaa_base_1.0-1.deb
[COLOR="Red"]-rwxr-xr-x 1 tom tom  123138 2007-05-24 18:24 checkinstall_1.6.1-1_i386.deb[/COLOR]
-rw-r--r-- 1 tom tom    2117 2007-05-20 08:44 copy2
drwxr-xr-x 2 tom tom     456 2007-05-20 23:12 debPackages
drwx------ 3 tom tom     296 2007-05-24 19:12 Desktop
-rwxr-xr-x 1 tom tom  184731 2007-05-20 18:57 dldrinstall.run
drwxr-xr-x 3 tom tom      72 2007-05-24 18:59 firefox-2.0.0.3
-rwxr-xr-x 1 tom tom 9651693 2007-05-24 18:08 firefox-2.0.0.3.tar.gz
drwxr-xr-x 3 tom tom     224 2007-05-19 21:49 ndiswrapper
-rw-r--r-- 1 tom tom       0 2007-05-24 18:38 pkgsone
-rw-r--r-- 1 tom tom   21999 2007-05-20 08:33 print.pdf
drwxr-xr-x 4 tom tom     352 2007-05-20 19:28 WG121V200
tom@emachine:~$
tom@emachine:~$ sudo apt-get install checkinstall_1.6.1-1_i386.deb
Reading package lists... Done
Building dependency tree
Reading state information... Done
[COLOR="Red"]E: Couldn't find package checkinstall_1.6.1-1_i386.deb[/COLOR][/INDENT][/INDENT]

The error says it can't find the checkinstall package when it's clearly shown to be in that directory by the listing above. Why can't it find the package?

Next I tried to uppack the tar ball. It contained a firefox-bin file. I tried to execute it and got this error message:

[INDENT][INDENT][COLOR="Red"]./firefox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

[/COLOR][/INDENT][/INDENT]

Again, it says it can't find a file (libmozjs.so) although that file was in the tar ball and is in the same directory as firefox-bin.

I'm obviously confused about why these files can't be found. What am I doing wrong and what do I need to do to solve this problem?

Thank you.

---

### Post by BarfBag on 2007-05-24
It's probably a dependency problem.  That's all I can say on the matter.  I suck at compiling things.  :(

What trouble is Konqueror causing you?

---

### Post by tlinux on 2007-05-24
I'm trying to install Linuxant's DriverLoader so that I can connect wirelessly to the Internet. I concluded that I don't have the skills needed to use ndiswrapper. I've had problems with the installation and have worked with the Linuxant people to correct problems. By now almost everything has been checked out on my Kubuntu setup and they can't find any more problems. However, one of the last steps in this installation process is to go to [http://127.0.0.1:18020/](http://127.0.0.1:18020/)  Knoqueror can't find that address and the Linuxant people suspect there may be a bug in Konqueror. That's why I'm trying to install Firefox.

---

### Post by ramjet_1953 on 2007-05-25
Have you installed[COLOR="Red"] build-essential[/COLOR] ?

Without this, you will get nowhere.

The full procedure is :

[COLOR="Red"]./configure
make
sudo make install[/COLOR]

I like to use [COLOR="Blue"]sudo checkinstall[/COLOR] instead of [COLOR="Blue"]sudo make instal[/COLOR]l, as it produces a deb package, which you can then install with the package manager. This makes it easier to un-install the package later, as it appears in Synaptic.

However, you also need to check the site where you downloaded the package and make sure that you have all of the dependancies installed.

If you follow these steps, all should work fine.

Regards,
Roger :cool:

---

### Post by Ek0nomik on 2007-05-25
To install a .deb file, use the command:

```
dpkg -i filename.de
```

---

### Post by ramjet_1953 on 2007-05-25
Also, have you enabled the extra repositories in [COLOR="Blue"]Synaptic[/COLOR]?

Many of the packages are not in the standard package lists.

Use synaptic and do a search for [COLOR="Blue"]checkinstal[/COLOR]l, to see if it is listed there. If not, you need to enable the extra repositories, go, on-line and refresh.

You should then be able to download [COLOR="Blue"]checkinstal[/COLOR]l.

Like I said before, also make sure that you have installed [COLOR="Red"]build-essential[/COLOR]

Regards,
Roger :cool:

---

### Post by tlinux on 2007-05-25
I've tried before and failed to get build-essential to install. I tried again and here's the terminal output:

[INDENT][INDENT]tom@emachine:~$ cd /home/tom
tom@emachine:~$ ls -l
total 9782
-rwxr-xr-x  1 tom tom    5974 2007-05-24 18:24 aaa_base_1.0-1.deb
-rwxr-xr-x  1 tom tom  123138 2007-05-24 18:24 checkinstall_1.6.1-1_i386.deb
-rw-r--r--  1 tom tom    2117 2007-05-20 08:44 copy2
drwxr-xr-x  2 tom tom     456 2007-05-20 23:12 debPackages
drwx------  3 tom tom     344 2007-05-24 23:39 Desktop
-rwxr-xr-x  1 tom tom  184731 2007-05-20 18:57 dldrinstall.run
drwxr-xr-x 12 tom tom    1232 2007-03-09 20:43 firefox
drwxr-xr-x  3 tom tom      72 2007-05-24 18:59 firefox-2.0.0.3
-rwxr-xr-x  1 tom tom 9651693 2007-05-24 18:08 firefox-2.0.0.3.tar.gz
drwxr-xr-x  3 tom tom     224 2007-05-19 21:49 ndiswrapper
-rw-r--r--  1 tom tom       0 2007-05-24 18:38 pkgsone
-rw-r--r--  1 tom tom   21999 2007-05-20 08:33 print.pdf
drwxr-xr-x  4 tom tom     352 2007-05-20 19:28 WG121V200
tom@emachine:~$ cd /debPackages
bash: cd: /debPackages: No such file or directory
tom@emachine:~$ cd /home/tom/debPackages
tom@emachine:~/debPackages$ ls -l
total 11258
-r-xr-xr-x 1 tom tom 2512860 2007-05-19 22:33 binutils_2.17cvs20070426-6_i386.deb
[COLOR="Red"]-rwxr-xr-x 1 tom tom    6982 2007-05-20 07:24 build-essential_11.3_i386.deb[/COLOR]
-r-xr-xr-x 1 tom tom 3136984 2007-05-19 22:35 coreutils_5.97-5.3_i386.deb
-rwxr-xr-x 1 tom tom  154532 2007-05-20 15:29 dpkg-dev_1.14.3_all.deb
-rwxr-xr-x 1 tom tom  456340 2007-05-10 15:39 driverloader_2.37_i386.deb
-rwxr-xr-x 1 tom tom    1372 2007-05-20 15:29 g++_4.1.2-2_i386.deb
-rwxr-xr-x 1 tom tom    5058 2007-05-20 15:30 gcc_4.1.2-2_i386.deb
-rwxr-xr-x 1 tom tom 1927704 2007-05-20 15:30 libc0.3-dev_2.5-4_hurd-i386.deb
-rwxr-xr-x 1 tom tom 3300706 2007-05-20 15:31 libc6-dev_2.5-7_i386.deb
[COLOR="Red"]tom@emachine:~/debPackages$ sudo dpkg -i build-essential_11.3_i386.deb
Password:[/COLOR]
(Reading database ... 77223 files and directories currently installed.)
Preparing to replace build-essential 11.3 (using build-essential_11.3_i386.deb) ...
Unpacking replacement build-essential ...
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on libc6-dev | libc-dev; however:
  Package libc6-dev is not configured yet.
  Package libc-dev is not installed.
  Package libc6-dev which provides libc-dev is not configured yet.
 build-essential depends on gcc (>= 4:4.1.1); however:
  Package gcc is not configured yet.
 build-essential depends on g++ (>= 4:4.1.1); however:
  Package g++ is not configured yet.
dpkg: error processing build-essential (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 build-essential
tom@emachine:~/debPackages$ tom@emachine:~$ cd /home/tom
bash: tom@emachine:~$: command not found
tom@emachine:~/debPackages$ tom@emachine:~$ ls -l
bash: tom@emachine:~$: command not found
tom@emachine:~/debPackages$ total 9782
bash: total: command not found
tom@emachine:~/debPackages$ -rwxr-xr-x  1 tom tom    5974 2007-05-24 18:24 aaa_base_1.0-1.deb
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -rwxr-xr-x: command not found
tom@emachine:~/debPackages$ -rwxr-xr-x  1 tom tom  123138 2007-05-24 18:24 checkinstall_1.6.1-1_i386.deb
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -rwxr-xr-x: command not found
tom@emachine:~/debPackages$ -rw-r--r--  1 tom tom    2117 2007-05-20 08:44 copy2
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -rw-r--r--: command not found
tom@emachine:~/debPackages$ drwxr-xr-x  2 tom tom     456 2007-05-20 23:12 debPackages
bash: drwxr-xr-x: command not found
tom@emachine:~/debPackages$ drwx------  3 tom tom     344 2007-05-24 23:39 Desktop
bash: drwx------: command not found
tom@emachine:~/debPackages$ -rwxr-xr-x  1 tom tom  184731 2007-05-20 18:57 dldrinstall.run
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -rwxr-xr-x: command not found
tom@emachine:~/debPackages$ drwxr-xr-x 12 tom tom    1232 2007-03-09 20:43 firefox
bash: drwxr-xr-x: command not found
tom@emachine:~/debPackages$ drwxr-xr-x  3 tom tom      72 2007-05-24 18:59 firefox-2.0.0.3
bash: drwxr-xr-x: command not found
tom@emachine:~/debPackages$ -rwxr-xr-x  1 tom tom 9651693 2007-05-24 18:08 firefox-2.0.0.3.tar.gz
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -rwxr-xr-x: command not found
tom@emachine:~/debPackages$ drwxr-xr-x  3 tom tom     224 2007-05-19 21:49 ndiswrapper
bash: drwxr-xr-x: command not found
tom@emachine:~/debPackages$ -rw-r--r--  1 tom tom       0 2007-05-24 18:38 pkgsone
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -rw-r--r--: command not found
tom@emachine:~/debPackages$ -rw-r--r--  1 tom tom   21999 2007-05-20 08:33 print.pdf
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -rw-r--r--: command not found
tom@emachine:~/debPackages$ drwxr-xr-x  4 tom tom     352 2007-05-20 19:28 WG121V200
bash: drwxr-xr-x: command not found
tom@emachine:~/debPackages$ tom@emachine:~$ cd /debPackages
bash: tom@emachine:~$: command not found
tom@emachine:~/debPackages$ bash: cd: /debPackages: No such file or directory
bash: bash:: command not found
tom@emachine:~/debPackages$ tom@emachine:~$ cd /home/tom/debPackages
bash: tom@emachine:~$: command not found
tom@emachine:~/debPackages$ tom@emachine:~/debPackages$ ls -l
bash: tom@emachine:~/debPackages$: No such file or directory
tom@emachine:~/debPackages$ total 11258
bash: total: command not found
tom@emachine:~/debPackages$ -r-xr-xr-x 1 tom tom 2512860 2007-05-19 22:33 binutils_2.17cvs20070426-6_i386.deb
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -r-xr-xr-x: command not found
tom@emachine:~/debPackages$ -rwxr-xr-x 1 tom tom    6982 2007-05-20 07:24 build-essential_11.3_i386.deb
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -rwxr-xr-x: command not found
tom@emachine:~/debPackages$ -r-xr-xr-x 1 tom tom 3136984 2007-05-19 22:35 coreutils_5.97-5.3_i386.deb
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -r-xr-xr-x: command not found
tom@emachine:~/debPackages$ -rwxr-xr-x 1 tom tom  154532 2007-05-20 15:29 dpkg-dev_1.14.3_all.deb
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -rwxr-xr-x: command not found
tom@emachine:~/debPackages$ -rwxr-xr-x 1 tom tom  456340 2007-05-10 15:39 driverloader_2.37_i386.deb
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -rwxr-xr-x: command not found
tom@emachine:~/debPackages$ -rwxr-xr-x 1 tom tom    1372 2007-05-20 15:29 g++_4.1.2-2_i386.deb
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -rwxr-xr-x: command not found
tom@emachine:~/debPackages$ -rwxr-xr-x 1 tom tom    5058 2007-05-20 15:30 gcc_4.1.2-2_i386.deb
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -rwxr-xr-x: command not found
tom@emachine:~/debPackages$ -rwxr-xr-x 1 tom tom 1927704 2007-05-20 15:30 libc0.3-dev_2.5-4_hurd-i386.deb
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -rwxr-xr-x: command not found
tom@emachine:~/debPackages$ -rwxr-xr-x 1 tom tom 3300706 2007-05-20 15:31 libc6-dev_2.5-7_i386.deb
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -r
bash: -rwxr-xr-x: command not found
tom@emachine:~/debPackages$ tom@emachine:~/debPackages$ sudo dpkg -i build-essential_11.3_i386.deb
bash: tom@emachine:~/debPackages$: No such file or directory
tom@emachine:~/debPackages$ Password:
bash: Password:: command not found
tom@emachine:~/debPackages$ (Reading database ... 77223 files and directories currently installed.)
bash: Reading: command not found
tom@emachine:~/debPackages$ Preparing to replace build-essential 11.3 (using build-essential_11.3_i386.deb) ...
bash: syntax error near unexpected token `('
tom@emachine:~/debPackages$ Unpacking replacement build-essential ...
bash: Unpacking: command not found
tom@emachine:~/debPackages$ dpkg: dependency problems prevent configuration of build-essential:
bash: dpkg:: command not found
tom@emachine:~/debPackages$  build-essential depends on libc6-dev | libc-dev; however:
bash: build-essential: command not found
bash: libc-dev: command not found
bash: however:: command not found
tom@emachine:~/debPackages$   Package libc6-dev is not configured yet.
bash: Package: command not found
tom@emachine:~/debPackages$   Package libc-dev is not installed.
bash: Package: command not found
tom@emachine:~/debPackages$   Package libc6-dev which provides libc-dev is not configured yet.
bash: Package: command not found
tom@emachine:~/debPackages$  build-essential depends on gcc (>= 4:4.1.1); however:
bash: syntax error near unexpected token `('
tom@emachine:~/debPackages$   Package gcc is not configured yet.
bash: Package: command not found
tom@emachine:~/debPackages$  build-essential depends on g++ (>= 4:4.1.1); however:
bash: syntax error near unexpected token `('
tom@emachine:~/debPackages$   Package g++ is not configured yet.
bash: Package: command not found
tom@emachine:~/debPackages$ dpkg: error processing build-essential (--install):
bash: syntax error near unexpected token `('
tom@emachine:~/debPackages$  dependency problems - leaving unconfigured
bash: dependency: command not found
tom@emachine:~/debPackages$ Errors were encountered while processing:
bash: Errors: command not found
tom@emachine:~/debPackages$  build-essential
bash: build-essential: command not found
tom@emachine:~/debPackages$                         
[/INDENT][/INDENT]


Synaptic isn't available on this copy of Kubuntu. The package manager is Adept. I'll have to go on line and search for it. However, I wonder if it will install given all the other difficulties getting packages to install.

---

### Post by tlinux on 2007-05-25
I can't get on the Internet until I get some of these packages installed. However, I don't seem to be able to install the packages via the command line because of missing dependencies. Finding and then installing the dependencies seems like a never-ending process. Every dependency I find and try to install fails because it also needs some missing dependencies. 

What to do?

Thank you!](*,)]

---

### Post by Terl on 2007-05-25
> **tlinux said:**
> I'm trying to install Linuxant's DriverLoader so that I can connect wirelessly to the Internet. I concluded that I don't have the skills needed to use ndiswrapper. I've had problems with the installation and have worked with the Linuxant people to correct problems. By now almost everything has been checked out on my Kubuntu setup and they can't find any more problems. However, one of the last steps in this installation process is to go to [http://127.0.0.1:18020/](http://127.0.0.1:18020/)  Knoqueror can't find that address and the Linuxant people suspect there may be a bug in Konqueror. That's why I'm trying to install Firefox.

In a terminal, can you ping that address?

---

### Post by tlinux on 2007-05-25
I've never used **ping** so I just did what I tought should be done to use it. Here's the terminal output:

tom@emachine:~$ ping 127.0.0.1:18020/
ping: unknown host 127.0.0.1:18020/
tom@emachine:~$

What is this telling me? :confused:

Thank you.

---

