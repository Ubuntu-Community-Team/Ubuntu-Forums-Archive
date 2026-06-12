---
title: "installing c compiler and wineHQ"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-05-25
i am quite new to ubuntu almost one weak old

i want to install c compiler which one is the smartest way to do this.
i also need wineHQ to be installed to enable my self to install some smaller .exe softwares.
how can i do so????????????????
plz tell me

---

### Post by Jagot on 2006-05-25
To get compilers:

```
sudo aptitude install build-essential
```

To get Wine:

```
sudo aptitude install wine
```

To configure Wine:

```
winecfg
```

---

### Post by Sef on 2006-05-25
> i want to install c compiler which one is the smartest way to do this.

From the terminal (Applications > Accessories > Terminal)

sudo apt-get update

sudo apt-get install build-essential

You need build-essential to compile

---

### Post by u04f061 on 2006-05-25
[QUOTE=Sef]From the terminal (Applications > Accessories > Terminal)

sudo apt-get update

sudo apt-get install build-essential

You need build-essential to compile[/QUOTE]

plz give me some alternative to this.there is a problem with my apt-get command since installed ubuntu
it completes to 40% and hives a large number of errors

---

### Post by Sutekh on 2006-05-25
This is the best way to install the C compiler.  If you are getting errors from the apt-get commands, then we should sort them out first.

Can you post the errors from the suggested commands?

---

### Post by u04f061 on 2006-05-26
[QUOTE=Sutekh]This is the best way to install the C compiler.  If you are getting errors from the apt-get commands, then we should sort them out first.

Can you post the errors from the suggested commands?[/QUOTE]

thank u for u'r kindness.this is what i want.plz help me in resolving this issue.this is the real problem of mine
there is a link to my thread which i started to resolve this issue.in it i have given much detail description of this  plus other posts with no +ve result
[http://www.ubuntuforums.org/showthread.php?t=182253](http://www.ubuntuforums.org/showthread.php?t=182253) 

this is the error message



ejaz@ejaz:~$ sudo nano /etc/apt/sources.list
Password:
ejaz@ejaz:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_bak
ejaz@ejaz:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg
Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...zy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...zy/Release.gpg) Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...es/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...es/Release.gpg) Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...ts/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...ts/Release.gpg) Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/di...ty/Release.gpg](http://security.ubuntu.com/ubuntu/di...ty/Release.gpg) Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_bin ary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restrict ed_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe _binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiver se_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe _binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
ejaz@ejaz:~$

---

### Post by bruce89 on 2006-05-26
It looks like there is no internet connection.

---

### Post by u04f061 on 2006-05-26
[QUOTE=bruce89]It looks like there is no internet connection.[/QUOTE]

then from where i am posting??????????????????

---

### Post by bruce89 on 2006-05-26
```
sudo apt-get update
```
Can you post your /etc/apt/sources.list please?

---

### Post by u04f061 on 2006-05-26
[QUOTE=Sef]From the terminal (Applications > Accessories > Terminal)

sudo apt-get update

sudo apt-get install build-essential

You need build-essential to compile[/QUOTE]

the following error was encountered by u'r command

ejaz@ejaz:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.0 libc6 libc6-dev libc6-i686 libstdc++6-4.0-dev
  linux-kernel-headers make
Suggested packages:
  debian-keyring gcc-4.0-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.0-doc stl-manual
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.0 libc6-dev libstdc++6-4.0-dev
  linux-kernel-headers make
The following packages will be upgraded:
  libc6 libc6-i686
2 upgraded, 8 newly installed, 0 to remove and 159 not upgraded.
1 not fully installed or removed.
Need to get 8673kB/14.2MB of archives.
After unpacking 34.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main libc6 2.3.5-1ubuntu12.5.10.1 [4872kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main libc6-i686 2.3.5-1ubuntu12.5.10.1 [1008kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main libc6-dev 2.3.5-1ubuntu12.5.10.1 [2792kB]
Fetched 8673kB in 39m8s (3692B/s)

Preconfiguring packages ...
(Reading database ... 58499 files and directories currently installed.)
Preparing to replace libc6 2.3.5-1ubuntu12 (using .../libc6_2.3.5-1ubuntu12.5.10.1_i386.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.3.5-1ubuntu12.5.10.1) ...
Current default timezone: 'America/New_York'.
Local time is now:      Sat May 27 02:36:00 EDT 2006.
Universal Time is now:  Sat May 27 06:36:00 UTC 2006.
Run 'tzconfig' if you wish to change it.

(Reading database ... 58472 files and directories currently installed.)
Preparing to replace libc6-i686 2.3.5-1ubuntu12 (using .../libc6-i686_2.3.5-1ubuntu12.5.10.1_i386.deb) ...
Unpacking replacement libc6-i686 ...
Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.5-1ubuntu12.5.10.1_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../archives/make_3.80-9_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.10ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up msttcorefonts (1.2ubuntu2) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--02:36:19--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
--02:36:24--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Temporary failure in name resolution.
--02:36:29--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Temporary failure in name resolution.
--02:36:34--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--02:36:44--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
--02:36:49--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Temporary failure in name resolution.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libc6-i686 (2.3.5-1ubuntu12.5.10.1) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu13) ...
Setting up libc6-dev (2.3.5-1ubuntu12.5.10.1) ...
Setting up make (3.80-9) ...

Setting up dpkg-dev (1.13.10ubuntu4) ...
Setting up libstdc++6-4.0-dev (4.0.1-4ubuntu9) ...
Setting up g++-4.0 (4.0.1-4ubuntu9) ...
Setting up g++ (4.0.1-3) ...

Setting up build-essential (11.1) ...
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
ejaz@ejaz:~$

---

### Post by Koech on 2006-05-26
From one of the posts above, it seemed like there was no internet conxn, I wonder whether you could be suffering the effects of a bad connxn, probably look into that before you retry.

---

### Post by Mustard on 2006-05-26
[QUOTE=u04f061]the following error was encountered by u'r command

ejaz@ejaz:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.0 libc6 libc6-dev libc6-i686 libstdc++6-4.0-dev
  linux-kernel-headers make
Suggested packages:
  debian-keyring gcc-4.0-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.0-doc stl-manual
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.0 libc6-dev libstdc++6-4.0-dev
  linux-kernel-headers make
The following packages will be upgraded:
  libc6 libc6-i686
2 upgraded, 8 newly installed, 0 to remove and 159 not upgraded.
1 not fully installed or removed.
Need to get 8673kB/14.2MB of archives.
After unpacking 34.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main libc6 2.3.5-1ubuntu12.5.10.1 [4872kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main libc6-i686 2.3.5-1ubuntu12.5.10.1 [1008kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main libc6-dev 2.3.5-1ubuntu12.5.10.1 [2792kB]
Fetched 8673kB in 39m8s (3692B/s)

Preconfiguring packages ...
(Reading database ... 58499 files and directories currently installed.)
Preparing to replace libc6 2.3.5-1ubuntu12 (using .../libc6_2.3.5-1ubuntu12.5.10.1_i386.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.3.5-1ubuntu12.5.10.1) ...
Current default timezone: 'America/New_York'.
Local time is now:      Sat May 27 02:36:00 EDT 2006.
Universal Time is now:  Sat May 27 06:36:00 UTC 2006.
Run 'tzconfig' if you wish to change it.

(Reading database ... 58472 files and directories currently installed.)
Preparing to replace libc6-i686 2.3.5-1ubuntu12 (using .../libc6-i686_2.3.5-1ubuntu12.5.10.1_i386.deb) ...
Unpacking replacement libc6-i686 ...
Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.5-1ubuntu12.5.10.1_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../archives/make_3.80-9_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.10ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up msttcorefonts (1.2ubuntu2) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--02:36:19--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
--02:36:24--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Temporary failure in name resolution.
--02:36:29--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Temporary failure in name resolution.
--02:36:34--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--02:36:44--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
--02:36:49--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Temporary failure in name resolution.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libc6-i686 (2.3.5-1ubuntu12.5.10.1) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu13) ...
Setting up libc6-dev (2.3.5-1ubuntu12.5.10.1) ...
Setting up make (3.80-9) ...

Setting up dpkg-dev (1.13.10ubuntu4) ...
Setting up libstdc++6-4.0-dev (4.0.1-4ubuntu9) ...
Setting up g++-4.0 (4.0.1-4ubuntu9) ...
Setting up g++ (4.0.1-3) ...

Setting up build-essential (11.1) ...
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
ejaz@ejaz:~$[/QUOTE]


The last errors are related to your proxy connection problem.  In the link that I showed you in another thread, it showed several methods of setting up your proxy connection to work with different applications, not just apt-get.  What is occuring above is that apt-get is configured to use your proxy, but then apt-get is calling **wget** to download some stuff (fonts in this instance), and your method of configuration that you chose for your proxy is not allowing wget to use your proxy.  I would go back to the link that I showed you earlier and use one of the additional methods that are shown at the bottom of the page that enable more than just apt-get to access your proxy connection.

---

