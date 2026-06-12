---
title: "Ulimit -n"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by reala on 2008-03-21
Hi,

I am having trouble making changes permanent.

I'm trying to increase ulimit for utorrent in wine.

I'm following this process

sudo su
-ulimit -n 8192

The changes are not staying permanent though. In the similar threads topic above i found the solution..

> 
I have added new limits for ulimit -n to /etc/security/limits.conf
myuser hard nofile 33554432

The problem is i do not know how to edit /etc/security/limits.conf and add that line to make it a permanent change.

Thanks in advance.

---

### Post by mattismyname on 2008-03-22
```
gedit /etc/security/limits.conf
```

Then make the edit and save the file.  The 'sudo' command will execute the editor (gedit) as root (superuser).

---

### Post by reala on 2008-03-23
Thanks

I added 

#reala           hard    nofile          8192

to /etc/security/limits.conf and saved it 

but after rebooting when i do

-ulimit -n

it still reports 1024

My limits.conf looks like this


# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4
#reala           hard    nofile          8192
# End of file

---

### Post by mattismyname on 2008-03-23
The pound sign (#) indicates that the line is a "comment".  In other words it has no effect.

Remove the pound sign from your line:

```
reala hard nofile 8192
```

---

### Post by reala on 2008-03-23
I should have known that ! :)

Thanks for the help - issue is fixed.

---

