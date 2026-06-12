---
title: "Error with libgtk1.2-common"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Bladze DCOTL on 2008-03-12
I just reinstalled Ubuntu, first 7.04, installed gimp, xine, wine, etc. then upgraded to 7.10, but since the upgrade, i have been getting an error "unable to open files list file for package 'libgtk1.2-common'."  I was hoping that I could find some help, but searching the forums has proved unfruitful.  Perhaps I missed something, or perhaps someone knows a work around, already tried force replacing package, but it says it doesn't exist in the cache.

Thanks in advance,
John

---

### Post by Oldsoldier2003 on 2008-03-12
> **Bladze DCOTL said:**
> I just reinstalled Ubuntu, first 7.04, installed gimp, xine, wine, etc. then upgraded to 7.10, but since the upgrade, i have been getting an error "unable to open files list file for package 'libgtk1.2-common'."  I was hoping that I could find some help, but searching the forums has proved unfruitful.  Perhaps I missed something, or perhaps someone knows a work around, already tried force replacing package, but it says it doesn't exist in the cache.

Thanks in advance,
John

try this in a command terminal

```
sudo apt-get update
sudo apt-get upgrade
 sudo apt-get install --reinstall libgtk1.2-common
```

---

### Post by Bladze DCOTL on 2008-03-12
Thank you for the quick response, but when I ran the commands I received the error:

(Reading database ... dpkg: error processing /var/cache/apt/archives/libgtk1.2-common_1.2.10-18_all.deb (--unpack):
 unable to open files list file for package `libgtk1.2-common': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libgtk1.2-common_1.2.10-18_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

John

---

### Post by Oldsoldier2003 on 2008-03-12
> **Bladze DCOTL said:**
> Thank you for the quick response, but when I ran the commands I received the error:

(Reading database ... dpkg: error processing /var/cache/apt/archives/libgtk1.2-common_1.2.10-18_all.deb (--unpack):
 unable to open files list file for package `libgtk1.2-common': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libgtk1.2-common_1.2.10-18_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

John
okay looks to be a problem with your actual package... try clearing the cache:
```

sudo apt-get clean

```
then try reinstalling it as above:
```
sudo apt-get install --reinstall libgtk1.2-common
```

---

### Post by Bladze DCOTL on 2008-03-12
This is getting funny, same error again.  I appreciate the help.  Anything else that might fix this aside from a full reload.  I really don't want to have to do that again.

John

---

### Post by Oldsoldier2003 on 2008-03-12
> **Bladze DCOTL said:**
> This is getting funny, same error again.  I appreciate the help.  Anything else that might fix this aside from a full reload.  I really don't want to have to do that again.

John

well we could try working the other angle, try this..

```
sudo dpkg --configure -a
```

---

### Post by Bladze DCOTL on 2008-03-12
Tried and failed.  Believe it or not I'm kinda enjoying this. 

 > sudo dpkg --configure -a
 sudo apt-get install --reinstall libgtk1.2-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtk1.2 libglib1.2 liblzo-dev libgtk1.2-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/158kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/libgtk1.2-common_1.2.10-18_all.deb (--unpack):
 unable to open files list file for package `libgtk1.2-common': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libgtk1.2-common_1.2.10-18_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

You are being very helpful, and I hope I'm not burdening you badly.

John

---

### Post by Oldsoldier2003 on 2008-03-12
> **Bladze DCOTL said:**
> Tried and failed.  Believe it or not I'm kinda enjoying this. 

 

You are being very helpful, and I hope I'm not burdening you badly.

John
well apt says you don't need the library anymore... you could run apt-get autoremove and see what happens.The version of Gimp that runs in Ubuntu 7.10 uses gtk2.0 libs anyhow

---

### Post by Bladze DCOTL on 2008-03-12
> sudo apt-get autoremove
[sudo] password for jschwab:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtk1.2 libglib1.2 liblzo-dev libgtk1.2-common
The following packages will be REMOVED:
  libglib1.2 libgtk1.2 libgtk1.2-common liblzo-dev
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 3551kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing libgtk1.2 (--remove):
 unable to open files list file for package `libgtk1.2-common': Input/output error
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

Think I could get away with "sudo"ing nautilus and removing the file manually?

John

---

### Post by Oldsoldier2003 on 2008-03-12
> **Bladze DCOTL said:**
> Think I could get away with "sudo"ing nautilus and removing the file manually?

John

not a good idea to do that, give me a moment and I'll see if i can find some more help

---

### Post by Bladze DCOTL on 2008-03-12
That is greatly appreciated.

John

---

### Post by jan quark on 2008-03-12
do you have a 64 bit system ? just a wild guess have read somewhere a similar issue with this package on a 64 bit system

---

### Post by Bladze DCOTL on 2008-03-12
No, still running my 5yo prescot core.

John

---

### Post by Oldsoldier2003 on 2008-03-12
> **Bladze DCOTL said:**
> No, still running my 5yo prescot core.

John

could you post the results of uname -a ... I just have a funny feeling about this whole thing.

---

### Post by Bladze DCOTL on 2008-03-12
Now correct me if I'm wrong, but here are the results that came back from "uname -a" and my interpetation.

> Linux 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

Doesn't the i686 indicate 64 bit??

John

---

### Post by Oldsoldier2003 on 2008-03-12
> **Bladze DCOTL said:**
> Now correct me if I'm wrong, but here are the results that came back from "uname -a" and my interpetation.



Doesn't the i686 indicate 64 bit??

John

i386 or i686=32 bit
x86_64 is 64bit   so we are certain you didn't manage to end up with a 64-bit distro by some weird glitch. 

Cmon guys there's gotta be someone out there thats seen this before...

---

### Post by Bladze DCOTL on 2008-03-13
Well thank you anyway, starting my reload, this time I will wait till I upgrade to 7.10 before installing my secondary software.

Thanks for the attempt with especially Oldsoldier2003.
John

---

