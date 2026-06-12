---
title: "trouble installing a run.gz file"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by mmooty.gam on 2007-02-27
I just downloaded the UT2004 demo from it's website. It is currently located on my desktop. Whenever I run a sudo apt-get install UT2004.run.gz it goes through the package lists and dependency trees, and then says that it can't find the package. Also, I have noticed that I can't extract this file. Here is the command line code that I used:

mmootygam@mmootygam-desktop:~/Desktop$ ls
UT2004.run.gz
mmootygam@mmootygam-desktop:~/Desktop$ sudo apt-get install UT2004.run.gz
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package UT2004.run.gz
mmootygam@mmootygam-desktop:~/Desktop$ ls -la
total 79244
drwxr-xr-x  2 mmootygam mmootygam     4096 2007-02-27 22:11 .
drwxr-xr-x 64 mmootygam mmootygam     4096 2007-02-27 22:25 ..
-rw-r--r--  1 mmootygam mmootygam 81049007 2007-02-27 21:43 UT2004.run.gz
mmootygam@mmootygam-desktop:~/Desktop$

I hope that code helps.

---

### Post by haricharan on 2007-02-27
use```
tar zxf UT2004.run.gz
``` to extract it. A directory named UT2004 or something wud have been created.  cd into that directory and type
```
./configure
make
make install
```

this is the default procedure to install from a tar.gz file....

---

### Post by haricharan on 2007-02-27
but wait u need to have gcc and everything installed..so before you start make type this
```
sudo apt-get install build-essential
```

---

### Post by aidanr on 2007-02-27
actually, those last commands would be to build from source, and this is a closed source game so after extracting you would type:

./UT2004.run

edit:// actually you'll probably want to stick sudo before that, and don't hit play when the installer is finished or you'll get premissions problems, just install it then exit the installer and run it as a normal user,not root
so again the commands would be 

```
cd ~/Desktop
tar -zxf UT2004.run.gz
sudo ./UT2004.run
```

---

### Post by mmooty.gam on 2007-02-27
mmootygam@mmootygam-desktop:~/Desktop$ tar zxf UT2004.run.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Archive contains obsolescent base-64 headers

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors

Hmm....why can't this run.gz file just go with the flow lol.....
Please help with this.

---

### Post by aidanr on 2007-02-27
try:

```
gunzip UT2004.run.gz
```

oh, and also after extracting:

```
chmod +x UT2004.run
```

---

### Post by haricharan on 2007-02-27
oops..sorry abt that...i was thinking it would be compile from source game... 	:-k

---

