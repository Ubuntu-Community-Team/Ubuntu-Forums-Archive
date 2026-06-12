---
title: "installed new program, wont run, 1 week old noobie"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by zabien1970 on 2007-07-01
OK, I'm trying to run a program called bitpim, after downloading got error installing, tried redownloading, same problem, played around 'bought a small reference linux book' and tried deleting files found under bitpim then downloaded again...    tried running  'sudo apt-get install build-essential'  got this

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 7906kB of archives.
After unpacking 33.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main linux-libc-dev 2.6.20-16.29 [667kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libc6-dev 2.5-0ubuntu14 [3018kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libstdc++6-4.1-dev 4.1.2-0ubuntu4 [1632kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main g++-4.1 4.1.2-0ubuntu4 [2581kB] 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main g++ 4:4.1.2-1ubuntu1 [1428B]    
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main build-essential 11.3 [6974B]    
Fetched 7906kB in 20s (381kB/s)                                                
Selecting previously deselected package linux-libc-dev.
(Reading database ... 111471 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.20-16.29_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.5-0ubuntu14_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.1.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up bitpim (1.0.0) ...
cp: cannot stat `/usr/lib/BitPim-1.0.0/resources/60-bitpim.rules': No such file or directory
dpkg: error processing bitpim (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-libc-dev (2.6.20-16.29) ...
Setting up libc6-dev (2.5-0ubuntu14) ...
Setting up libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
Setting up g++-4.1 (4.1.2-0ubuntu4) ...
Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ...
Errors were encountered while processing:
 bitpim
E: Sub-process /usr/bin/dpkg returned an error code (1)

any help?  I truly am lost and barely know what i'm doing on the command line, but am willing to learn

---

### Post by KIAaze on 2007-07-01
Launch Synaptic (System ->Administration->Synaptic package manager)
Select "custom filters" in the bottom left.
Choose "broken" in the top left.
Now deselect the bitpim package if it is listed.
Click apply.

Now install "build essential" through synaptic. (Click "search", search for "build-essential", select it for installation, click apply)

Now you can retry installing "bitpim" through synaptic the same way.

(Note: Another command-line solution would probably be to run "sudo dpkg --configure -a". But usually, when that is necessary, you get a message telling you to do so.)

P.S:
If you want to remove a program, deleting its files manually is the last thing to do, especially if you're a newbie!
Because if you remove essential files using "sudo rm" you could break your system.
Generally, it is best to uninstall apps the way they were installed:
-If you installed with synaptic, remove with synaptic.
-If you installed with aptitude, remove with aptitude.
-If you installed with apt-get, remove with apt-get.
-If you installed with dpkg, remove with dpkg.
-If you installed with "make install", use "make uninstall".
-etc...
If you want to cleanly remove a program by deleting its files, it's better to know how the install process actually works. ("bitpim" probably left some files not containing "bitpim")

---

### Post by zabien1970 on 2007-07-01
nothing listed in the 'broken section', if I search for bitpim it says installed

---

### Post by KIAaze on 2007-07-01
Can you install other programs without errors?

Here, maybe this will work:
[QUOTE=CBlue]After you get that error, try apt-get -f install to force an install of the files that didn't get loaded because of the error. Then try apt-get upgrade again, apt-get -f install back and forth until only the package that has the error is left.[/QUOTE]
[http://www.linuxquestions.org/questions/showthread.php?s=&forumid=9&threadid=171107]("http://www.linuxquestions.org/questions/showthread.php?s=&forumid=9&threadid=171107")

So in your case:
> sudo apt-get install -f build-essential
sudo apt-get upgrade
...


---

### Post by zabien1970 on 2007-07-01
Still nothing, the site said it was a rpm package but had an unofficial deb download which I downloaded first, then tried to download the rpm to run through alien but said file already exsisted, thats when I tried erasing stuff.

here's the latest
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up bitpim (1.0.0) ...
cp: cannot stat `/usr/lib/BitPim-1.0.0/resources/60-bitpim.rules': No such file or directory
dpkg: error processing bitpim (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bitpim
E: Sub-process /usr/bin/dpkg returned an error code (1)

it seems i'm missing a file but trying to reinstall through gui and command line hasn't worked, should i reinstall linux and hope it wipes everything and try again? 
I am willing to let you try remote access if you would like to look at what i have

---

### Post by zabien1970 on 2007-07-01
Oh yeah, this is the first program i've had a problem with, all others worked

---

