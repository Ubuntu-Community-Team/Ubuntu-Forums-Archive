---
title: "[SOLVED] Install .tar.gz"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by KDE_rocks2345 on 2008-04-05
I think I am doing something wrong could you please check this:

1. Extract .tar.gz to desktop
2. Open konsole enter following script:

```
nja@nja-laptop:~$ cd /home/nja/Desktop/zhu3d-4.0.4/

nja@nja-laptop:~/Desktop/zhu3d-4.0.4$ ./configure
bash: ./configure: No such file or directory

nja@nja-laptop:~/Desktop/zhu3d-4.0.4$ make
make: *** No targets specified and no makefile found. Stop.

nja@nja-laptop:~/Desktop/zhu3d-4.0.4$ sudo make install
[sudo] password for nja:
make: *** No rule to make target `install'. Stop.

nja@nja-laptop:~/Desktop/zhu3d-4.0.4$
```
:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by tamoneya on 2008-04-05
that is probably because you do not have execute permissions on configure.```
sudo chmod +x configure
./configure
```
if that still doesnt work post the output of ```
ls -la
```

---

### Post by bumanie on 2008-04-05
Ensure you have build-essential enabled 
> sudo apt-get install build-essential
Firstly, right click on the directory on your desktop and select 'extract here'
> cd ~/Desktop --> enter
> cd <name of extracted directory> --> enter
<name of extracted directory>$>  ./configure --> enter
> make --> enter
> sudo make install  --> enter

---

### Post by joshrobinson on 2008-04-05
```
tar zxvf zhu3d-4.0.4.tar.gz
cd zhu3d-4.0.4
qmake
make
make clean
```

thats what it says in the included install.txt file
always check for readme files and install files in the tarball

---

### Post by ramjet_1953 on 2008-04-05
Have you installed [COLOR="Blue"]build-essential[/COLOR]?

If not, type this in a terminal: [COLOR="Red"]sudo apt-get install build-essential[/COLOR]

Regards,
Roger :cool:

---

### Post by KDE_rocks2345 on 2008-04-05
bumanie I still have a problem look:

[CODE]nja@nja-laptop:~$ sudo apt-get install build-essential
[sudo] password for nja:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libenchant1c2a libmono-security1.0-cil libmono0 libglade2.0-cil
  visualboyadvance libglib2.0-cil libmono-sharpzip0.84-cil
  libmono-sqlite1.0-cil vnc-common libmono-system-web1.0-cil
  libmono-corlib1.0-cil mono-common python-gtkhtml2 libvte2.0-cil libsexy2
  libmono-system1.0-cil libfltk1.1 python-sexy libgtk2.0-cil mono-gac
  python-vte libmono1.0-cil libmono-data-tds1.0-cil mono-jit
  libmono-system-data1.0-cil libgtkhtml2-0 python-launchpad-integration
  mono-runtime python-gdbm xtightvncviewer libmono-cairo1.0-cil
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc
  manpages-dev libstdc++6-4.1-doc diff-doc
The following NEW packages will be installed
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev patch
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 3940kB/7935kB of archives.
After unpacking 31.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com gutsy-updates/main linux-libc-dev 2.6.22-14.52 [653kB]
Media Change: Please insert the disc labelled
 &#8216;Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)&#8217;
in the drive &#8216;/cdrom/&#8217; and press enter

Get: 2 http://gb.archive.ubuntu.com gutsy-updates/main libc6-dev 2.6.1-1ubuntu10 [3287kB]
Fetched 3940kB in 45s (86.7kB/s)
Selecting previously deselected package linux-libc-dev.
(Reading database ... 102985 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.22-14.52_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.6.1-1ubuntu10_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-16ubuntu2_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-9ubuntu2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../p/patch/patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.5ubuntu16_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Setting up linux-libc-dev (2.6.22-14.52) ...
Setting up libc6-dev (2.6.1-1ubuntu10) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.5ubuntu16) ...
Setting up libstdc++6-4.1-dev (4.1.2-16ubuntu2) ...
Setting up g++-4.1 (4.1.2-16ubuntu2) ...
Setting up g++ (4:4.1.2-9ubuntu2) ...

Setting up build-essential (11.3ubuntu1) ...
nja@nja-laptop:~$ cd /home/nja/Desktop/zhu3d-4.0.4/
nja@nja-laptop:~/Desktop/zhu3d-4.0.4$ ./configure
bash: ./configure: No such file or directory
nja@nja-laptop:~/Desktop/zhu3d-4.0.4$ make
make: *** No targets specified and no makefile found. Stop.
nja@nja-laptop:~/Desktop/zhu3d-4.0.4$ sudo make install
make: *** No rule to make target `install'. Stop.
nja@nja-laptop:~/Desktop/zhu3d-4.0.4$[CODE/]

---

### Post by steveneddy on 2008-04-05
> **KDE_rocks2345 said:**
> [SIZE="5"]All good answers but could someone just give me *all* the scrip I need please?[/SIZE]

stop shouting!

My goodness, we are all volunteers here. There is no need for

[SIZE="6"]letters this big![/SIZE]

If you want immediate attention, please try one of the paid services offered by Ubuntu for support.

And to answer your question, chief, they already gave you the answer.

try 

 sudo ./configure

if the build-essential package doesn't do it for you.

---

### Post by steveneddy on 2008-04-05
If it fixed your problem, please mark this thread as solved.

---

### Post by KDE_rocks2345 on 2008-04-05
This thread is not solved and I give up on this some one please delete this.

---

### Post by tamoneya on 2008-04-05
```
sudo chmod +x configure
```
I think it is because you dont have permissiions to execute the file.

---

### Post by astraljava on 2008-04-05
Nope, a configure script requires no additional tools, it can be executed right away. And permissions are not the problem:

jaska@scapa:~/src/ufoai 20:31:04 $ chmod a-x configure
jaska@scapa:~/src/ufoai 20:30:58 $ ./configure
bash: ./configure: Permission denied

It's simply not there, as the error message very clearly indicates.

Didn't joshrobinson's reply bring any help? If not, then could you upload the tarball somewhere so one of us could take another closer look?

---

