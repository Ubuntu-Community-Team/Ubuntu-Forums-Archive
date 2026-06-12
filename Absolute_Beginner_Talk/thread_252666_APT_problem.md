---
title: "APT problem"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Anonii on 2006-09-07
APT seems obsessed to install vim. I cant apt-get install anything, before I execute "apt-get -f install" which gives me this error:


```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  vim
Suggested packages:
  ctags vim-doc vim-scripts
The following NEW packages will be installed:
  vim
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/7323kB of archives.
After unpacking 23.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  vim
Install these packages without verification [y/N]? y
(Reading database ... 111988 files and directories currently installed.)
Unpacking vim (from .../vim_2%3a0.20060517T160422_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb (--unpack):
 trying to overwrite `/usr/bin/xxd', which is also in package vim-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Also, when I try to install vim with "sudo apt-get -f install"
I get this:

```
$ sudo apt-get install vim
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  ctags vim-doc vim-scripts
The following NEW packages will be installed:
  vim
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/7323kB of archives.
After unpacking 23.2MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  vim
Install these packages without verification [y/N]? Y
(Reading database ... 111988 files and directories currently installed.)
Unpacking vim (from .../vim_2%3a0.20060517T160422_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb (--unpack):
 trying to overwrite `/usr/bin/xxd', which is also in package vim-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Which is similar with the previous.


I'd like some help fast, because like I said, I can install _nothing_. :/

---

### Post by monktbd on 2006-09-07
if you dont mind losing all downloaded packages from the apt archive then maybe a 

> sudo apt-get clean 

will help

---

### Post by xpod on 2006-09-07
Aint it best to use "aptitude" as apose to "apt-get"......?as it removes all that it installs where as "apt-get" dont remove all the dependancies that may come with a particular package/app???

Ive noticed you having a bit of hassle with stuff not being uninstalled properly..........just a thought...good luck

---

### Post by Anonii on 2006-09-07
> **xpod said:**
> Aint it best to use "aptitude" as apose to "apt-get"......?as it removes all that it installs where as "apt-get" dont remove all the dependancies that may come with a particular package/app???

Ive noticed you having a bit of hassle with stuff not being uninstalled properly..........just a thought...good luck
I'm always using aptitude, I used apt-get to show you simple error messages and not 666lines that aptitude would give me :)
Anyway, I tried to clean aptitude but I get the same error. I dont really want to reinstall Ubuntu, so I have to fix it!
The logs:

> _$ sudo aptitude clean_
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
habeeb@habeeb:~_$ sudo aptitude -f install_
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  xmame-x
The following packages have been kept back:
  libxfont1
The following NEW packages will be installed:
  kxmame vim xmame-x
The following packages will be REMOVED:
  xmame-sdl
0 packages upgraded, 3 newly installed, 1 to remove and 1 not upgraded.
Need to get 17.1MB of archives. After unpacking 24.9MB will be used.
Do you want to continue? [Y/n/?] Y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  vim

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse kxmame 1.91-0ubuntu1 [357kB]
Get:2 [http://issaris.be](http://issaris.be) ./ vim 2:0.20060517T160422 [7323kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse xmame-x 0.101-1 [9375kB]
Fetched 17.1MB in 3m55s (72.3kB/s)
Preconfiguring packages ...
(Reading database ... 111988 files and directories currently installed.)
Unpacking vim (from .../vim_2%3a0.20060517T160422_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb (--unpack):
 trying to overwrite `/usr/bin/xxd', which is also in package vim-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on vim; however:
  Package vim is not installed.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-base:
 ubuntu-base depends on ubuntu-minimal; however:
  Package ubuntu-minimal is not configured yet.
dpkg: error processing ubuntu-base (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-minimal
 ubuntu-base
      

---

### Post by monktbd on 2006-09-07
try manually renaming that vim****.deb and see what happens then

e.g.
> 
mv vim*****.deb vim****.debsav


replace the ***** accordingly of course :).

---

### Post by Anonii on 2006-09-07
> **monktbd said:**
> try manually renaming that vim****.deb and see what happens then

e.g.


replace the ***** accordingly of course :).

I have already tried this. Same error, check this:

> _$ sudo aptitude clean_
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
habeeb@habeeb:~$ _ls /var/cache/apt/archives_
**lock  partial**
habeeb@habeeb:~$ _sudo aptitude -f install_
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  xmame-x
The following packages have been kept back:
  libxfont1
The following NEW packages will be installed:
  kxmame vim xmame-x
The following packages will be REMOVED:
  xmame-sdl
0 packages upgraded, 3 newly installed, 1 to remove and 1 not upgraded.
Need to get 17.1MB of archives. After unpacking 24.9MB will be used.
Do you want to continue? [Y/n/?] Y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  vim

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse kxmame 1.91-0ubuntu1 [357kB]
Get:2 [http://issaris.be](http://issaris.be) ./ vim 2:0.20060517T160422 [7323kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse xmame-x 0.101-1 [9375kB]
Fetched 17.1MB in 4m12s (67.7kB/s)
Preconfiguring packages ...
(Reading database ... 111988 files and directories currently installed.)
Unpacking vim (from .../vim_2%3a0.20060517T160422_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb (--unpack):
 trying to overwrite `/usr/bin/xxd', which is also in package vim-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
[B]Errors were encountered while processing:
 /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb[/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on vim; however:
  Package vim is not installed.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-base:
 ubuntu-base depends on ubuntu-minimal; however:
  Package ubuntu-minimal is not configured yet.
dpkg: error processing ubuntu-base (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-minimal
 ubuntu-base


---

### Post by monktbd on 2006-09-07
trying to reinstall the ubuntu-minimal?

> sudo apt-get install ubuntu-minimal
> sudo apt-get --reinstall install ubuntu-minimal

---

### Post by Anonii on 2006-09-07
> **monktbd said:**
> trying to reinstall the ubuntu-minimal?
```
[U]
$ sudo aptitude reinstall ubuntu-minimal[/U]
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  ubuntu-minimal
The following packages have been kept back:
  libxfont1
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  ubuntu-minimal: Depends: vim but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
vim [2:0.20060517T160422 (<NULL>)]

Score is -19

Accept this solution? [Y/n/q/?] Y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  vim

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
The following NEW packages will be automatically installed:
  vim
The following packages have been kept back:
  libxfont1
The following packages will be REINSTALLED:
  ubuntu-minimal
The following NEW packages will be installed:
  vim
0 packages upgraded, 1 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0B/7323kB of archives. After unpacking 23.2MB will be used.
Do you want to continue? [Y/n/?] Y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  vim

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Writing extended state information... Done
(Reading database ... 111988 files and directories currently installed.)
Unpacking vim (from .../vim_2%3a0.20060517T160422_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb (--unpack):
 trying to overwrite `/usr/bin/xxd', which is also in package vim-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on vim; however:
  Package vim is not installed.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-base:
 ubuntu-base depends on ubuntu-minimal; however:
  Package ubuntu-minimal is not configured yet.
dpkg: error processing ubuntu-base (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-minimal
 ubuntu-base
_habeeb@habeeb:~$ sudo aptitude install ubuntu-minimal_
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  vim
The following packages have been kept back:
  libxfont1
The following NEW packages will be installed:
  vim
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/7323kB of archives. After unpacking 23.2MB will be used.
Do you want to continue? [Y/n/?] Y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  vim

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Writing extended state information... Done
(Reading database ... 111988 files and directories currently installed.)
Unpacking vim (from .../vim_2%3a0.20060517T160422_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb (--unpack):
 trying to overwrite `/usr/bin/xxd', which is also in package vim-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on vim; however:
  Package vim is not installed.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-base:
 ubuntu-base depends on ubuntu-minimal; however:
  Package ubuntu-minimal is not configured yet.
dpkg: error processing ubuntu-base (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-minimal
 ubuntu-base
_habeeb@habeeb:~$ sudo apt-get --reinstall install ubuntu-minimal_
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ubuntu-minimal: Depends: vim but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
_habeeb@habeeb:~$ sudo apt-get -f install_
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  vim
Suggested packages:
  ctags vim-doc vim-scripts
The following NEW packages will be installed:
  vim
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B/7323kB of archives.
After unpacking 23.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  vim
Install these packages without verification [y/N]? Y
(Reading database ... 111988 files and directories currently installed.)
Unpacking vim (from .../vim_2%3a0.20060517T160422_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb (--unpack):
 trying to overwrite `/usr/bin/xxd', which is also in package vim-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[U]habeeb@habeeb:~$ sudo apt-get clean
habeeb@habeeb:~$ sudo apt-get -f install[/U]
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  vim
Suggested packages:
  ctags vim-doc vim-scripts
The following NEW packages will be installed:
  vim
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 7323kB of archives.
After unpacking 23.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  vim
Install these packages without verification [y/N]? Yes
Get:1 http://issaris.be ./ vim 2:0.20060517T160422 [7323kB]
Fetched 7323kB in 2m3s (59.4kB/s)
(Reading database ... 111988 files and directories currently installed.)
Unpacking vim (from .../vim_2%3a0.20060517T160422_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb (--unpack):
 trying to overwrite `/usr/bin/xxd', which is also in package vim-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Did a couple of tries, but still the only thing I get are awful errors >:
Tried with aptitude with apt-get, with cleaned APT, with everything >:
Seems like that APT wants Vim installed, but it cant install it.
Any more suggestions? :/


(Thanks for the help btw)

---

### Post by monktbd on 2006-09-07
try to disable the not main ubuntu repos, e.g. the vim package was downloaded from
Get:1 [http://issaris.be](http://issaris.be) ./ vim 2:0.20060517T160422 [7323kB]
is that a standard repo?

---

### Post by Anonii on 2006-09-07
> **monktbd said:**
> try to disable the not main ubuntu repos, e.g. the vim package was downloaded from
Get:1 [http://issaris.be](http://issaris.be) ./ vim 2:0.20060517T160422 [7323kB]
is that a standard repo?
Damn right, how didnt I think of it... retarded automatix repo... >:
Now its fixed >:3
Thanks!

---

### Post by monktbd on 2006-09-07
> **Anonii said:**
> Damn right, how didnt I think of it... retarded automatix repo... >:
Now its fixed >:3
Thanks!

you're welcome.

glad it got sorted out :).

---

