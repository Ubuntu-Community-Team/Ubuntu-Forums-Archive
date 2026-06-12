---
title: "add application manager problem"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by Hotchilli on 2005-12-19
I have been waiting for sometime foradd aplication manager to start

the application is initializing please wait--2 hours already
var/lib/dpkg/status

if I close the program down and start synaptic manager
error message reads

1) unable to parse package file /var/lib/dpkg/status(1)
2)the package list or status file could not be pased or opened


thanks

nc:smile: :smile:

---

### Post by bscbrit on 2005-12-19
When you tried to start the Add Applications, did you see a dialogue asking for a password?

However, this looks like a corrupted file.  See this link:

[http://www.debian.org/doc/manuals/quick-reference/ch-package.en.html](http://www.debian.org/doc/manuals/quick-reference/ch-package.en.html)

and in particular this bit (type any commands **exactly** as seen here):

3.3.4 Recover package selection data

If /var/lib/dpkg/status becomes corrupt for any reason, the Debian system loses package selection data and suffers severely. Look for the old /var/lib/dpkg/status file at /var/lib/dpkg/status-old or /var/backups/dpkg.status.*.

Keeping /var/backups/ in a separate partition may be a good idea since this directory contains lots of important system data.

If no old /var/lib/dpkg/status file is available, you can still recover information from directories in /usr/share/doc/.

     # ls /usr/share/doc | \
       grep -v [A-Z] | \
       grep -v '^texmf$' | \
       grep -v '^debian$' | \
       awk '{print $1 " install"}' | \
       dpkg --set-selections
     # dselect --expert # reinstall system, de-select as needed

---

### Post by Hotchilli on 2005-12-19
It looks very complicated I am not sure if I am in a position to make
the changes But if help was at hand then perhaps I could:


here is what is in the directory lets take it step by step
what happens next

total 3988
drwxr-xr-x  2 root root    4096 2005-12-14 11:11 alternatives
-rw-r--r--  1 root root  905150 2005-12-16 20:05 available
-rw-r--r--  1 root root  904584 2005-12-16 17:42 available-old
-rw-r--r--  1 root root       8 2005-11-26 01:20 cmethopt
-rw-r--r--  1 root root    2988 2005-11-26 02:25 diversions
-rw-r--r--  1 root root    3072 2005-11-26 02:25 diversions-old
drwxr-xr-x  2 root root  131072 2005-12-16 20:05 info
-rw-r-----  1 root root       0 2005-12-19 22:09 lock
drwxr-xr-x  5 root root    4096 2005-11-26 02:09 methods
drwxr-xr-x  2 root root    4096 2005-09-24 18:39 parts
-rw-r--r--  1 root root      30 2005-11-26 02:21 statoverride
-rw-r--r--  1 root root       0 2005-11-26 01:19 statoverride-old
-rw-r--r--  1 root root 1042264 2005-12-16 20:05 status
-rw-r--r--  1 root root 1041801 2005-12-16 20:05 status-old
drwxr-xr-x  2 root root    4096 2005-12-16 20:05 updates


hc:smile: :smile:

---

### Post by bscbrit on 2005-12-20
Ok, it is possible that I can see the problem from the directory listing you have posted.  

Close down synaptic and/or any other applications e.g. aptitude etc.

Change to the directory from which the listing is made.

Open a terminal window and type

sudo rm -f lock

Try using synaptic again.

Let me know what happens please.

---

### Post by Hotchilli on 2005-12-20
Thankyou for your post


YES I removed lock but still the same error as before.

andy108@heis:~$ cd /var/lib/dpkg
andy108@heis:/var/lib/dpkg$ ls -l
total 3988
drwxr-xr-x  2 root root    4096 2005-12-14 11:11 alternatives
-rw-r--r--  1 root root  905150 2005-12-16 20:05 available
-rw-r--r--  1 root root  904584 2005-12-16 17:42 available-old
-rw-r--r--  1 root root       8 2005-11-26 01:20 cmethopt
-rw-r--r--  1 root root    2988 2005-11-26 02:25 diversions
-rw-r--r--  1 root root    3072 2005-11-26 02:25 diversions-old
drwxr-xr-x  2 root root  131072 2005-12-16 20:05 info
-rw-r-----  1 root root       0 2005-12-20 22:35 lock
drwxr-xr-x  5 root root    4096 2005-11-26 02:09 methods
drwxr-xr-x  2 root root    4096 2005-09-24 18:39 parts
-rw-r--r--  1 root root      30 2005-11-26 02:21 statoverride
-rw-r--r--  1 root root       0 2005-11-26 01:19 statoverride-old
-rw-r--r--  1 root root 1042264 2005-12-16 20:05 status
-rw-r--r--  1 root root 1041801 2005-12-16 20:05 status-old
drwxr-xr-x  2 root root    4096 2005-12-16 20:05 updates
andy108@heis:/var/lib/dpkg$ sudo rm -f lock
Password:
andy108@heis:/var/lib/dpkg$ ls -l
total 3988
drwxr-xr-x  2 root root    4096 2005-12-14 11:11 alternatives
-rw-r--r--  1 root root  905150 2005-12-16 20:05 available
-rw-r--r--  1 root root  904584 2005-12-16 17:42 available-old
-rw-r--r--  1 root root       8 2005-11-26 01:20 cmethopt
-rw-r--r--  1 root root    2988 2005-11-26 02:25 diversions
-rw-r--r--  1 root root    3072 2005-11-26 02:25 diversions-old
drwxr-xr-x  2 root root  131072 2005-12-16 20:05 info
drwxr-xr-x  5 root root    4096 2005-11-26 02:09 methods
drwxr-xr-x  2 root root    4096 2005-09-24 18:39 parts
-rw-r--r--  1 root root      30 2005-11-26 02:21 statoverride
-rw-r--r--  1 root root       0 2005-11-26 01:19 statoverride-old
-rw-r--r--  1 root root 1042264 2005-12-16 20:05 status
-rw-r--r--  1 root root 1041801 2005-12-16 20:05 status-old
drwxr-xr-x  2 root root    4096 2005-12-16 20:05 updates
andy108@heis:/var/lib/dpkg$
[CENTER][/CENTER]

---

