---
title: "Backup strategy for a Jaunty box and an IMac"
date: 2009-09-04
forum: Apple Hardware Users
---

### Post by enginuysal on 2009-09-04
I've got;
- 1 x Imac (OSX 10.5.8),
- 1 x Laptop with Ubuntu 9.04 installed,
- 1 x Airport Extreme base station connected to Imac with ethernet cable,
- 1 x 500 GB external harddrive connected to Airport Extreme base station.

I can access the harddrive from Jaunty box typing "smb://192.168.1.3/mydrive" in Nautilus.

I've got the Documents, Music, Pictures and Movies folders in both machines. Some of the files in these folders are same both in Imac and Jaunty boxes, some are different and some are unique.

What I first need is a script/software/method in Jaunty box that does below steps;
- check the files of Documents, Music, Pictures and Movies folders in computer periodically,
- connect the shared harddrive,
- if a file does not exist in its respective folder in the shared drive, copy it there,
- if it exists but is old, ask user what to do; replace or keep.
- if the same file exists, do nothing.

What I need next is something on IMac to do exact same thing.

Any ideas?

---

### Post by gotenks05 on 2009-09-04
> **enginuysal said:**
> I've got;
- 1 x Imac (OSX 10.5.8),
- 1 x Laptop with Ubuntu 9.04 installed,
- 1 x Airport Extreme base station connected to Imac with ethernet cable,
- 1 x 500 GB external harddrive connected to Airport Extreme base station.

I can access the harddrive from Jaunty box typing "smb://192.168.1.3/mydrive" in Nautilus.

I've got the Documents, Music, Pictures and Movies folders in both machines. Some of the files in these folders are same both in Imac and Jaunty boxes, some are different and some are unique.

What I first need is a script/software/method in Jaunty box that does below steps;
- check the files of Documents, Music, Pictures and Movies folders in computer periodically,
- connect the shared harddrive,
- if a file does not exist in its respective folder in the shared drive, copy it there,
- if it exists but is old, ask user what to do; replace or keep.
- if the same file exists, do nothing.

What I need next is something on IMac to do exact same thing.

Any ideas?

Reading your post, I suggest rsync.  It is installed by default in Ubuntu 8.04+, as far as I know, and Mac OS X 10.4.x+, again as far as I know. Just type up a shellscript of how you want it to work.  For your scheduling needs, cron jobs for Ubuntu and iCal for the Mac.  However, beware that if a file used to exist on the computer and is not there, rsync may delete it from the hard drive, so separate the systems to their own folder on the hard drive, but it will put whatever is on the computer to the hard drive and can backup only changed files, just like Time Machine.

---

