---
title: "cannot use synaptic package manager (cannot remove awcommon)"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by lian1238 on 2007-09-07
Hi all,
I've recently installed Maya 8.0 Linux, and have just removed it. But, I cannot remove awcommon. It is marked, but when I apply, I get this error message:

E: awcommon: subprocess post-removal script returned error exit status 2

Now, I cannot install or remove anything else. When I start synaptic package manager, awcommon is already applied for complete removal. How can I fix this?

Thanks in advance.

---

### Post by zvacet on 2007-09-07
```
sudo aptitude --purge remove  awcommon
```

---

### Post by lian1238 on 2007-09-07
This is what I got:

lian@lian-laptop:~$ sudo aptitude --purge remove  awcommon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  awcommon 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 4100kB will be freed.
Writing extended state information... Done
(Reading database ... 141073 files and directories currently installed.)
Removing awcommon ...
/usr/bin/test: invalid integer `remove'
exit: 26: Illegal number: -0
dpkg: error processing awcommon (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 awcommon
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
lian@lian-laptop:~$

---

### Post by philinux on 2007-09-07
Mark awcommon for reinstallation then when installed try to remove it again.

---

### Post by lian1238 on 2007-09-07
When I start synatpic package manager, awcommon is already marked for complete removal. only "Unmark", "Mark for complete removal" and "Properties" are clickable, the rest is grayed.
But when I click Unmark, it still doesn't change. I'm really stuck.

---

### Post by philinux on 2007-09-07
If its marked for complete removal what happens if you click apply?

---

### Post by lian1238 on 2007-09-07
When I apply, I get the message:
> 
E: awcommon: subprocess post-removal script returned error exit status 2

like I described in my first post.

When I run
```
sudo apt-get install -f
```
(because there is an update available, I tried to update but it says "software index is broken" and told me to run "Synaptic" or the above code)
I get this:
> 
lian@lian-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmtp5 libmpfr1 emacs21-common debhelper intltool-debian fftw3 po-debconf libcurl3-gnutls ruby1.8
  emacsen-common ruby libtunepimp5 libifp4 libgtk1.2-common html2text xaw3dg libruby1.8 libofa0
  liblockfile1 libxine1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  awcommon
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 4100kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 141073 files and directories currently installed.)
Removing awcommon ...
/usr/bin/test: invalid integer `remove'
exit: 26: Illegal number: -0
dpkg: error processing awcommon (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 awcommon
E: Sub-process /usr/bin/dpkg returned an error code (1)
lian@lian-laptop:~$ 

ultimately the same error..

---

### Post by lian1238 on 2007-09-07
I read a post, ([link here]("http://ubuntuforums.org/showthread.php?p=3310818")), and did this:
```
sudo gedit /var/lib/dpkg/status
```
found the awcommon entry and deleted it.
> 
Package: awcommon
Status: deinstall ok half-installed
Priority: extra
Section: alien
Installed-Size: 4004
Maintainer: Lian <lian@lian-laptop>
Architecture: i386
Version: 10.80-13
Config-Version: 10.80-13
Depends: libc6 (>= 2.5-0ubuntu1), libgcc1 (>= 1:4.1.2), libstdc++5 (>= 1:3.3.4-1), libx11-6, libxmu6, libxp6, libxt6
Description: AWCommon Linux 10.80 For Intel IA32
 AWCommon-10.80 for Linux
 .
 (Converted from a rpm package by alien version 8.65.)

this seems to have fixed the problem.. the update manager and synaptic package manager seems to be working now.
first, I tried changing the status to "install ok installed" but that didn't work. when I applied the update, it didn't really apply. The update kept showing again. so, I made a backup of /var/lib/dpkg/status and deleted the awcommon entry, and it worked.
but if this is not a good solution, please reply.
i'll be happy for now.:)

---

### Post by philinux on 2007-09-07
sounds like synaptic had a dicky fit when you uninstall maya 8.0.
As long as you can now use synaptic it sounds a fix to me.

---

### Post by Bubs on 2007-09-18
Wow Man thank you!  you helped me out a ton.  I just installed maya 8.5 and had the same problems as you.  Thanks for posting your solution

---

### Post by Hoaxe on 2007-11-29
> **Bubs said:**
> Wow Man thank you!  you helped me out a ton.  I just installed maya 8.5 and had the same problems as you.  Thanks for posting your solution

qudos same issue here, wth?

thanks anyways

---

### Post by Mr_Tricorder on 2007-12-19
I had the same problem with Maya 8.0, and this solution worked for me as well.

Has anyone here had any luck actually installing and using Maya on ubuntu?  I can get the Windows version working in my Windows guest OS in Virtualbox, but I would really like to run Maya natively under Linux.

---

### Post by Mr_Tricorder on 2007-12-19
nevermind.  I got Maya working :)

Just in time for me to have to leave for work too.  Oh well, at least I'll get to use it when I get back.

---

