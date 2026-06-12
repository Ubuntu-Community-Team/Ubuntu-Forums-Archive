---
title: "what are these partitions"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2006-12-06
hello when I run df -h

I got the following result:

mozkaynak@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             897M  795M   55M  94% /
varrun                506M   60K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  136K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-27-386/volatile
/dev/hda5             3.7G   84M  3.4G   3% /home
/dev/hda1              55G   16G   39G  29% /media/hda1
/dev/hda7             449M  8.1M  417M   2% /tmp
/dev/hda8              14G  2.8G   10G  22% /usr
/dev/hda9             924M  720M  205M  78% /windows
mozkaynak@ubuntu:~$


can someone tell me what are varrun, varlock, udev, devshm and lrm.
I dont remember creating these partitions but they are there.

Thank you.

---

### Post by Sef on 2006-12-06
They are files, not partitions.   Varrun is where the PID files are located.  A PID file is used in Unix and in Linux.  

[Dictionary By LaborLawTalk]("http://dictionary.laborlawtalk.com/Process_identifier") definition:

> In computing, the process identifier (normally referred to as the process ID or just PID) is a number used by some operating system kernels (such as that of UNIX or Windows NT) to uniquely identify a process.

Under Unix, the PID is returned by the fork() system call to both the parent and child processes, so that a process can tell which it is.

The PID can be passed to wait() or kill() to perform actions on the given process.

This article was originally based on material from the Free On-line Dictionary of Computing, which is licensed under the GFDL.


---

