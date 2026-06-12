---
title: "errors from using kdesu"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by meandstuff on 2008-02-15
Hi.  I'm just starting out with linux/kubuntu in order to do gis and database stuff.  I've installed feisty which seems to be working beautifully except for one thing.  When I use the kdesu command for anything (running adept, moving files, etc.) it spits out an error.  Here's the latest example:

my command:  kdesu  mv  /home/nathan/desktop/GIS  /home/gisdbase/GIS

and the konsole responds with 
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

However, the requested operation has been performed.  I'm just wondering if this is a fatal error that's going to bite me after I've put months of work into this.  Should I be reformatting my disk or something?

N.

---

### Post by mgranet on 2008-02-15
You want to use 'sudo' insead of 'kdesu' on the command line.

---

### Post by meandstuff on 2008-02-15
Thanks.  Problem solved.
N.

---

