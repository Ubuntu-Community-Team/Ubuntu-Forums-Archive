---
title: "What is a manual fsck, and how do I do one?"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by buyj3llo on 2006-12-10
I was using my computer and everything was fine, but the last time I tired to start up insteasd of taking me to the login screen it gave me a an error message in command line.
```
contains a filesystem with errors, forced
```

Apparently it was working on something by itself so I let it do it's thing. But then after it's done it pops up with this:

```
UNEXEPECETED INCONSISTENCY; RUN fsck MANUALLY
  (i.e without -a or -p options)
fsck died with the exit status 4

*an automatic filesystem check (fsck) of the root filesystem failed. A manuall fsck must be freformed then the filesystem restarted. The fsck shoulbe be pre formed in maintenance mode with the root file system mounted in read-only
*root filesystem is currently mounted in read only mode. a maintenace shell will now be started. After preforming a system maintence, press Controll-D. to terminate the mainience shell and restart the system.
bash: no job control in the shell
bash: groups: command not found
bash:lesspipe: command not found
bash dirclass: commnand not found

root@ubuntu:#_

```

from the looks of all that crap I figured I just had to type "fsck", so I did and it gave me this:

```
fsck 1.39 (29-may-2006)
e2fsck 1.29 (29-may-2006
/ contains a file system with errors, check failed
pass1: checking inodes blocks, and sizes
```

after that it just sits there for like 10 minutes doing no thing. If i try to type nothing really happens. Whats going on? what am I suppose to do here?

---

### Post by max.diems on 2006-12-10
Kill the process (^Z, ps, find PID, kill -9 PID), man fsck, learn the basics, run fsck.

---

### Post by veli on 2006-12-10
It stays there because you must run the fsck manually.

fsck must be run on unmounted partition, otherwise the file system will be damaged. There is a command line for unmounting and run the fsck. I myself prefer to run fsck from a Live CD-Simply Mepis for example. So if you have a Live Cd around, boot with it and in terminal execute the command for fsck. I did that once on ext3 file system and the bad sectors were repaired. I can't remember now what was the command, but you should know the partition, it's something like hdaX (or sdaX). I'm going out right now, so search in this forum and you'll find the command line for manual check the file system.

---

### Post by P235 on 2006-12-10
Hi, I don't know the reasons why fsck began running, but if you have ever hard booted your PC (i.e. pulling the power) a few times then fsck will be necessary.  If your PC ever freezes up, consider the advice in the following thread - especially post number 9 by 3rdalbum.

[http://www.ubuntuforums.org/showthread.php?t=308748]("http://www.ubuntuforums.org/showthread.php?t=308748")

---

### Post by spanky62798 on 2006-12-11
I am having issues too.  Every time it tries to boot, it tells me the 'unexpected inconsistancy' so I run my fsck manually and it claims it fixed everything, but then it continues to do the exact same thing and says the fsck failed.  I have tried just rebooting with the cd, but it hasn't worked.  I REALLY don't want to lose any of my files.  Is there anything you can share to help me log in atleast one last time to burn my files????

Thanks,
Cristina

---

### Post by marx2k on 2006-12-11
The only thing I can suggest to you is try rebooting with "shutdown -rF now"

fsck will run during bootup on all your drives.  Im sorry if this doesn't help :(

---

### Post by xmastree on 2006-12-11
The best way to fsck your filesystem is to boot from a live CD. This ensures that your main filesystem isn't mounted. Then you can run **sudo fsck /dev/hda1** (or wherever it is).

---

### Post by spanky62798 on 2006-12-11
I'm sorry if this is a stupid question...  I put in the live cd & booted from it and it pulled up, but how do I get to my desktop & files from that point?  I don't understand the dev/hda1 part - where & how do I get the command line to do that???

---

### Post by xmastree on 2006-12-12
Your desktop and files will on the unmounted disk. You don't want to get at them just yet.
Run fsck from a terminal in the live session.
The idea is, you can't run fsck on a mounted filesystem, so you need to unmount the damaged one. If you've booted normally, you can't unmount it so you need an alternative bood disc, hence the live CD.

The /dev/hda1, that's where I'm assuming your linux installation is. Is it the only OS on the computer, or are you dual booting?

---

### Post by fredrito on 2008-02-04
Hello,

I have the same problem and have tried running fsck from a live CD (OpenSUSE, not Ubuntu, if that makes any difference?). When, in addition to a thousand other things, I try sudo fsck /dev/sda3 (it is sda3, and it is unmounted) I get sudo: fsck: command not found. 

?!

---

### Post by xmastree on 2008-02-07
Strange... I know nothing about OpenSUSE so all I can suggest is try a different distro.

---

### Post by Herman on 2008-02-08
These days we don't really need to run a manual fsck from the command line, we can do it from GParted in the Ubuntu Live CD, [                         Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_") a user freindly GUI method.

It fixes a lot of the problems that the standard fsck -C -R -A -a doesn't.

GParted runs e2fsck -f -y -v

The  CLI will still be needed sometimes if  even that doesn't do it, but e2fsck -f -y -v will fix all your ext3 problems in a big percentage of instances.

Regards, Herman :)

---

