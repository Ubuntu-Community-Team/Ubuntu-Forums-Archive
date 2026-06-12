---
title: "can't install build-essential [Resolved]"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by BJinMontreal on 2007-03-06
I had a broken build-essential package and in the process of trying to fix my problem, I've uninstalled it (and there were others which had to be removed with it), but now I can't re-install it - I get an error messages saying "it is not available, but is referred to by another package. This means the package is missing, has been obsoleted, or is only available from another source. E: Package build-essential has no installation candidate"
I tried installing the various dependant packages I had to remove but I essentially get the same type error messages.
What can I do?

---

### Post by halitech on 2007-03-06
have you tried going into synaptic and installing it from there?

---

### Post by aysiu on 2007-03-06
Your repositories list is messed up.

**[Get a new one](http://www.psychocats.net/ubuntu/sources)**

Then try again: ```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by BJinMontreal on 2007-03-06
Aysiu,
I tried the backup command but I got the following error- command not found
BJ

---

### Post by BJinMontreal on 2007-03-06
Halitech,
Yes, I tried it from there and it didn't work either.
BJ

---

### Post by aysiu on 2007-03-06
Copy and paste the commands. Don't retype them.

If you're still experiencing an error, copy and paste everything (both what you input and the exact error message you got) back here, and we'll try to sort it out.

---

### Post by BJinMontreal on 2007-03-07
brian@brian-compaq:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
mv: cannot stat '/etc/apt/sources.list': No such file or directory
brian@brian-compaq:~$

---

### Post by aysiu on 2007-03-07
Okay. I don't know why you don't have an /etc/apt/sources.list to back up, but you can just go straight to the next command, which will create a new one for you.

---

### Post by BJinMontreal on 2007-03-07
I went back and re-did the cut and paste of the sources.list file and then the install update - which seemed to work.  I think I may have got it this time, except I noticed as it was setting up it mentioned something about my 'C' locale


(gksudo:9054): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gedit:9055): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gedit:9055): Gdk-WARNING **: locale not supported by C library

(gedit:9055): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
brian@brian-compaq:~$ sudo aptitude update
....
brian@brian-compaq:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libc6-dev
The following NEW packages will be automatically installed:
  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libmudflap0 libmudflap0-dev libstdc++6-4.0-dev
  linux-kernel-headers
The following packages have been kept back:
  checkinstall kopete liblircclient0 libtag1c2a libtheora0 locales readahead
The following NEW packages will be installed:
  binutils build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libmudflap0 libmudflap0-dev libstdc++6-4.0-dev
  linux-kernel-headers
0 packages upgraded, 14 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B/12.0MB of archives. After unpacking 46.5MB will be used.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20.4) but 2.4-1ubuntu12 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libc6 [2.4-1ubuntu12 (now) -> 2.3.6-0ubuntu20.4 (dapper-updates)]

Score is -40

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev libmudflap0 libmudflap0-dev libstdc++6-4.0-dev
  linux-kernel-headers
The following packages will be DOWNGRADED:
  libc6
The following packages have been kept back:
  checkinstall kopete liblircclient0 libtag1c2a libtheora0 locales readahead
The following NEW packages will be installed:
  binutils build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev libmudflap0 libmudflap0-dev
  libstdc++6-4.0-dev linux-kernel-headers
0 packages upgraded, 14 newly installed, 1 downgraded, 0 to remove and 7 not upgraded.
Need to get 0B/16.6MB of archives. After unpacking 46.5MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_CA:en",
        LC_ALL = (unset),
        LANG = "en_CA.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
dpkg - warning: downgrading libc6 from 2.4-1ubuntu12 to 2.3.6-0ubuntu20.4.
(Reading database ... 81484 files and directories currently installed.)
Preparing to replace libc6 2.4-1ubuntu12 (using .../libc6_2.3.6-0ubuntu20.4_i386.deb) ...
Unpacking replacement libc6 ...
dpkg: warning - unable to delete old directory `/etc/ld.so.conf.d': Directory not empty
Setting up libc6 (2.3.6-0ubuntu20.4) ...
Installing new version of config file /etc/init.d/glibc.sh ...

Selecting previously deselected package binutils.
(Reading database ... 81479 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu18_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.6-0ubuntu20.4_i386.deb) ...
Selecting previously deselected package cpp-4.0.
Unpacking cpp-4.0 (from .../cpp-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package cpp.
Unpacking cpp (from .../cpp_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.11ubuntu7_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Selecting previously deselected package libmudflap0.
Unpacking libmudflap0 (from .../libmudflap0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package libmudflap0-dev.
Unpacking libmudflap0-dev (from .../libmudflap0-dev_4.0.3-1ubuntu5_i386.deb) ...
Setting up binutils (2.16.1cvs20060117-1ubuntu2.1) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu18) ...
Setting up libc6-dev (2.3.6-0ubuntu20.4) ...
Setting up cpp-4.0 (4.0.3-1ubuntu5) ...
Setting up cpp (4.0.3-1) ...

Setting up gcc-4.0 (4.0.3-1ubuntu5) ...
Setting up gcc (4.0.3-1) ...

Setting up dpkg-dev (1.13.11ubuntu7) ...
Setting up libmudflap0 (4.0.3-1ubuntu5) ...

Setting up libmudflap0-dev (4.0.3-1ubuntu5) ...
Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...
brian@brian-compaq:~$

Do I need to reset my language - I don't remember ever changing it from when I first setup the system?

---

### Post by aysiu on 2007-03-07
> **BJinMontreal said:**
> 
Do I need to reset my language - I don't remember ever changing it from when I first setup the system? You may need to, but I'm not sure how to redo your locales. It looks as if *build-essential* installed okay, though.

---

### Post by BJinMontreal on 2007-03-07
Thanks Aysiu,
You have been a great help.  I'll check my language and see what other items are in 'C' locale and then I'll get back to trying to get Gnucash to install.
BJ

---

### Post by aysiu on 2007-03-07
Well now that you have a fresh set of repositories, installing *gnucash* should be as simple as ```
sudo aptitude update && sudo aptitude install gnucash
``` Still not sure about the locale thing, though.

---

### Post by BJinMontreal on 2007-03-07
Aysiu,
Not to sound like a complete idiot ... but after I entered your last command, ubuntu went through the selecting, unpacking, reading, building and multiple other steps ... including the last step: 
Setting up gnucash (1.8.12-6ubuntu3) ... 
Now I am back to my terminal screen brian@brian-compaq:~$

I can now go to my synaptic package manager and I see gnucash and gnucash-common ... but ...

What do I do next?

---

### Post by aysiu on 2007-03-07
> **BJinMontreal said:**
> Aysiu,
Not to sound like a complete idiot ... but after I entered your last command, ubuntu went through the selecting, unpacking, reading, building and multiple other steps ... including the last step: 
Setting up gnucash (1.8.12-6ubuntu3) ... 
Now I am back to my terminal screen brian@brian-compaq:~$

I can now go to my synaptic package manager and I see gnucash and gnucash-common ... but ...

What do I do next?
No idea.

GnuCash is now installed, but I don't know how to use it.

---

### Post by BJinMontreal on 2007-03-07
Sorry,
 I meant to ask - how do I access the program (where is it?) - I see it in the synaptic manager, but not in my applications.  How do I add it to my applications?
BJ

---

### Post by aysiu on 2007-03-07
This may help:
[How to launch Gnucash?](http://ubuntuforums.org/showthread.php?t=85180)

---

### Post by BJinMontreal on 2007-03-07
Aysiu,
A thousand thank yous to you.  I tried typing gnucash in a terminal ... and voila, I'm up and running.  I tried running the tutorial, but it is telling me the specified URL can not be loaded.  But, no worries - I should be able to figure out how to use the program without the tutorials.
Thanks again, for your patience and understanding.
BJ

---

### Post by aysiu on 2007-03-07
Glad you finally got it working.

I'm going to mark this resolved. If you ever do embark on that locales configuring quest, post a new thread, and hopefully someone more knowledgeable than I can help you out.

---

### Post by BJinMontreal on 2007-03-08
Yes, ... resolved is a good thing!  
Thanks
BJ

---

