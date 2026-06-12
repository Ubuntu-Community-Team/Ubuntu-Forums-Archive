---
title: "Filesystem is NOT clean / fsck problems"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by GeneralHooHa on 2007-08-26
About have the time when I startup Ubuntu (7.04), it shows the bar for a few seconds then starts displaying text. Here is says ```
Filesystem is NOT clean
```. 

I thought it was unable to do the regular fsck check after 30 mounts or so, but I get this when I try to do it manualy:
```
nick@nick-laptop:~$ sudo fsck
fsck 1.40-WIP (14-Nov-2006)
reiserfsck 3.6.19 (2003 www.namesys.com)

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to reiserfs-list@namesys.com, **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  www.namesys.com/support.html. **
*************************************************************

Will read-only check consistency of the filesystem on /dev/sda1
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes
###########
reiserfsck --check started at Sun Aug 26 12:24:33 2007
###########
Partition /dev/sda1 is mounted with write permissions, cannot check it

```
I have 3 partitions: 2 reiserfs on sda 1 and 3 (/ and /home), and 1 swap on sda2. It never did this before I partitioned my home directory, since then has never done a normal bootup check.

---

### Post by raphha on 2007-08-26
hello!
maybe you could boot from a live cd (ubuntu-desktop installation cd or knoppix -> google) and then check your partitions from there by manually starting reiserfsck.
raph

---

