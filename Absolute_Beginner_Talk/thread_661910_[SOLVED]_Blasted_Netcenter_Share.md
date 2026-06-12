---
title: "[SOLVED] Blasted Netcenter Share"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by glefty on 2008-01-08
Hey Folks,

Let me start off by saying, I'm an absolute nube to Ubuntu, have been playing around with it, but not seriously. So go please easy on me.

I've been running a 250gb WD Netcenter from my router, and screwed up one day after panicking on a windows machine.  I bascially lost sight of the shared folder on the xp machine, and like a dummy, I re-installed the ez link software, which in turn created another share, overwriting the original.  So, you guessed it, I pooched file table.

The drive shows about 22gb of used space, but I'm unable to see the files. (pictures, and mp3s)

I've removed the drive from the enclosure, and installed into another machine as a slave.  I've tried running some windoz file utilites, but to no avail.

After lurking around here for a while, and reading up on TestDisk, and other options, I've decided Ubuntu would be my best course of action seeing how WD uses the ReiserFS file system.

When running Testdisk, it didn't find a problem with the partition, but it gave me the option to create another partition on the drive, that's where I chickened out.  Should I delete the "shared files" folder from the drive, and then try testdisk again, or is there another way to recover these files?

Any guidance would be greatly appreciated, and would help get Dad out of the doghouse!! :(

---

### Post by glefty on 2008-01-19
Howdy all,

After hunting, and searching (especially on this forum), and I've been playing around with reiserfsck, but this output has me stumped.

daddyo@daddyo-desktop:~$ sudo reiserfsck --check /dev/sdb
reiserfsck 3.6.19 (2003 [www.namesys.com](www.namesys.com))

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to [email]reiserfs-list@namesys.com[/email], **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  [www.namesys.com/support.html](www.namesys.com/support.html). **
*************************************************************

Will read-only check consistency of the filesystem on /dev/sdb
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes
###########
reiserfsck --check started at Sat Jan 19 19:08:12 2008
###########
Replaying journal..
No transactions found
Zero bit found in on-disk bitmap after the last valid bit.
Checking internal tree..

Bad root block 0. (--rebuild-tree did not complete)

Aborted (core dumped)

Any ideas?

---

