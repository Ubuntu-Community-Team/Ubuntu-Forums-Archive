---
title: "[SOLVED] Plshelp me installing wxdfast 0.6.0 downloadmanager"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by iClouseau88 on 2007-11-05
Hi,
I have a tough time installing wxdfast 0.6.0 in Gutsy.  I downloaded the pkg to /usr/local/src and installed all required dependencies like python and libwxgtk, etc.  Here are the terminal entries:

hoe1@hoe1-laptop:~$ cd wxdfast 0.6.0
bash: cd: wxdfast: No such file or directory
hoe1@hoe1-laptop:~$ cd /usr/local/src
hoe1@hoe1-laptop:/usr/local/src$ cd 
hoe1@hoe1-laptop:~$ sudo apt-get install build-essential checkinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
checkinstall is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hoe1@hoe1-laptop:~$ sudo apt-get install wx-common libwxbase2.8-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wx-common is already the newest version.
libwxbase2.8-dev is already the newest version.
libwxbase2.8-dev set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hoe1@hoe1-laptop:~$ libwxgtk2.8-dev
bash: libwxgtk2.8-dev: command not found
hoe1@hoe1-laptop:~$ tar -zxvf wxdfast_0.6.0.tar.gz
tar: wxdfast_0.6.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
hoe1@hoe1-laptop:~$ cd /usr/local/src
hoe1@hoe1-laptop:/usr/local/src$ ./configure
bash: ./configure: No such file or directory
hoe1@hoe1-laptop:/usr/local/src$ ls
wxdfast-0.6.0
hoe1@hoe1-laptop:/usr/local/src$ 

Any suggestion?

:confused::(

---

### Post by The Tronyx on 2007-11-05
> 
tar -zxvf wxdfast_0.6.0.tar.gz


Are you running that command in the directory where wxdfast_0.6.0.tar.gz is located?  I am far from an expert but you said you downloaded the package to /usr/local/src but that command was run from your home directory.

Towards the bottom...
> 
hoe1@hoe1-laptop:~$ cd /usr/local/src
hoe1@hoe1-laptop:/usr/local/src$ ./configure
bash: ./configure: No such file or directory
hoe1@hoe1-laptop:/usr/local/src$ ls
wxdfast-0.6.0
hoe1@hoe1-laptop:/usr/local/src$


Looks like you tried to ./configure in the parent directory of wxdfast-0.6.0 so maybe 
> 
cd wxdfast-0.6.0
./configure


---

### Post by iClouseau88 on 2007-11-05
Hi all,

Finally I was able to install wxdfast using the deb package for edgy, not feisty, and via Synaptic.  I am able to invoke it via the terminal.  However, I can't integrate it as a download option in Firefox's Flashgot because it's greyed out.  This happens even if I open wxdfast  and see wxdfast icon in the "taskbar"

I would much appreciate your help.

:confused:

---

### Post by iClouseau88 on 2007-11-05
Problem solved after Synbaptic updates of libwxbase, libwxgtk and associated dev packages.

;-))

---

