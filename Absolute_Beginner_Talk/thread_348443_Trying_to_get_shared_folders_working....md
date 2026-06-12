---
title: "Trying to get shared folders working..."
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by BoyBlunder on 2007-01-28
I am trying to get shared folders to work with no avail. I go to system > administration > shared folders and it asks me to installs NFS and SMB. I click install services and it tells me it could not apply changes, and to fix broken packages first.

I'm running Edgy. any ideas?

---

### Post by Blutack on 2007-01-28
open a terminal (accessories --> terminal)
and type 
sudo aptitude install -f

this will tell you what is broken and give you some possible fixes.

---

### Post by BoyBlunder on 2007-01-28
```

pat@blunderbox:~$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libberylsettings0 
The following NEW packages will be installed:
  libberylsettings-dev 
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/39.8kB of archives. After unpacking 188kB will be used.
Do you want to continue? [Y/n/?] y
(Reading database ... 89656 files and directories currently installed.)
Unpacking libberylsettings-dev (from .../libberylsettings-dev_0.1.99.2~0beryl1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libberylsettings-dev_0.1.99.2~0beryl1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libberylsettings.so', which is also in package libberylsettings0
Errors were encountered while processing:
 /var/cache/apt/archives/libberylsettings-dev_0.1.99.2~0beryl1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

is what I get. any ideas?

I see some things regarding beryl (tried installing few days ago, didn't work though :-(), but I removed that with apt-get remove beryl...

---

### Post by Blutack on 2007-01-28
Unfortunatly unless you use apt-get autoremove it doesn't remove the dependencies ( other stuff beryl installs that it needs).  Run sudo aptitude remove libberylsettings0 and see whether that does the trick.  You can check by running install -f again.  If it comes up with no errors you are ok!

---

### Post by BoyBlunder on 2007-01-28
sigh...still not working :(

```

pat@blunderbox:/$ sudo aptitude remove libberylsettings0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libberyldecoration-dev 
The following packages will be REMOVED:
  libberylsettings0 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 77.8kB will be freed.
The following packages have unmet dependencies:
  libberyldecoration-dev: Depends: libberylsettings0 but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Upgrade the following packages:
libberylsettings0 [0.1.2-0ubuntu1 (edgy, now) -> 0.1.2-0ubuntu2 (edgy)]

Score is -39

Accept this solution? [Y/n/q/?] y
The following packages will be upgraded:
  libberylsettings0 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/26.9kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 89656 files and directories currently installed.)
Preparing to replace libberylsettings0 0.1.2-0ubuntu1 (using .../libberylsettings0_0.1.2-0ubuntu2_i386.deb) ...
Unpacking replacement libberylsettings0 ...
Setting up libberylsettings0 (0.1.2-0ubuntu2) ...

pat@blunderbox:/$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  libberylsettings-dev 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/39.8kB of archives. After unpacking 188kB will be used.
Do you want to continue? [Y/n/?] y
(Reading database ... 89656 files and directories currently installed.)
Unpacking libberylsettings-dev (from .../libberylsettings-dev_0.1.99.2~0beryl1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libberylsettings-dev_0.1.99.2~0beryl1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libberylsettings.so', which is also in package libberylsettings0
Errors were encountered while processing:
 /var/cache/apt/archives/libberylsettings-dev_0.1.99.2~0beryl1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

---

### Post by Blutack on 2007-01-28
sudo aptitude remove -f libberylsettings0
This time, when it offers the first option (score -39) hit no.  It should give you an option to remove libberylsettings and a load of other beryl related stuff.  Hope this works...

---

### Post by BoyBlunder on 2007-01-28
```

pat@blunderbox:/$ sudo aptitude remove -f libberylsettings0 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libberyldecoration-dev 
The following packages will be REMOVED:
  libberylsettings0 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 77.8kB will be freed.
The following packages have unmet dependencies:
  libberyldecoration-dev: Depends: libberylsettings0 but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libberylsettings0 [0.1.2-0ubuntu2 (edgy, now) -> 0.1.2-0ubuntu1 (edgy)]

Score is -39

Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libberyldecoration-dev

Score is -301

Accept this solution? [Y/n/q/?] n
Resolving dependencies...
open: 6665; closed: 4803; defer: 0; conflict/break: 25                         ONo solution found within the allotted time.  Try harder? [Y/n]


```

should I try harder? :-X

---

### Post by Blutack on 2007-01-28
Choose y to the second option, thats the one you want (score -301)!  Sorry for my dodgy earlier explanation, I wasn't sure how much beryl stuff you had left installed.

---

### Post by BoyBlunder on 2007-01-28
```

pat@blunderbox:/$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libberylsettings-dev 
The following packages will be REMOVED:
  sysvinit 
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 39.8kB of archives. After unpacking 143kB will be freed.
The following packages have unmet dependencies:
  libberylsettings-dev: Depends: libberylsettings0 but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
libberylsettings-dev [Not Installed]

Score is -1

Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libberylsettings0 [0.1.2-0ubuntu2 (edgy, now)]

Score is -39

Accept this solution? [Y/n/q/?] y
The following ESSENTIAL packages will be REMOVED!
  sysvinit 

WARNING: Performing this action will probably cause your system to break!
         Do NOT continue unless you know EXACTLY what you are doing!
To continue, type the phrase "I am aware that this is a very bad idea":


```

uh-oh...

---

### Post by Blutack on 2007-01-28
Good lord what the hell have you installed?  Hehe, it is a very bad idea.  Right, run sudo aptitude remove libberylsettings-dev.  That should do the trick, your system keeps trying to forcibly install it and can't.  Sorry I appear to have been slightly useless but dependancy issues from install wierd and wonderful packages can be a total pain (as you have just discovered!)

---

### Post by BoyBlunder on 2007-01-28
seems to be getting better, but it wants me to remove sysvinit now!

```

pat@blunderbox:~$ sudo aptitude remove libberylsettings-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
pat@blunderbox:~$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  sysvinit 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 332kB will be freed.
Do you want to continue? [Y/n/?] n
Abort.

```

---

### Post by Blutack on 2007-01-28
You definatly run edgy?
I assume you upgraded from dapper?
Sysvinit was replaced in edgy by a system called upstart.
Check you have it by running

sudo aptitude show upstart
Package: upstart
**State: installed**
Automatically installed: no
Version: 0.2.7-7
Priority: required
Section: base
Maintainer: Scott James Remnant <scott@ubuntu.com>
Uncompressed Size: 307k
PreDepends: libc6 (>= 2.4-1), sysvutils (>= 2.86.ds1-14.1ubuntu11)
Recommends: upstart-compat-sysv, upstart-logd, startup-tasks, system-services
Conflicts: sysvinit
Replaces: sysvinit
Description: event-based init daemon
 upstart is a replacement for the /sbin/init daemon which handles starting of
 tasks and services during boot, stopping them during shutdown and supervising
 them while the system is running.

and look for State : Installed.
If it is you are safe to remove sysvinit.

---

### Post by BoyBlunder on 2007-01-28
ah-ha! it's not installed!

and yes, this is a complete new install (dl'ed iso from ubuntu.com and I'm running a dualboot partition with xp)

```

sudo aptitude show upstart
No candidate version found for upstart
Package: upstart
State: not installed (configuration files remain)
Version: 0.2.7-7
Priority: required
Section: base
Maintainer: Scott James Remnant <scott@ubuntu.com>
Uncompressed Size: 307k
PreDepends: libc6 (>= 2.4-1), sysvutils (>= 2.86.ds1-14.1ubuntu11)
Recommends: upstart-compat-sysv, upstart-logd, startup-tasks, system-services
Conflicts: sysvinit
Replaces: sysvinit
Description: event-based init daemon
 upstart is a replacement for the /sbin/init daemon which handles starting of tasks and services
 during boot, stopping them during shutdown and supervising them while the system is running.


```

I believe the end is near! thank you for your help so far Blutack!

---

### Post by Blutack on 2007-01-28
Ok probably best to leave alone.  If it isn't installed that means your system needs sysvinit.  Have you tried running the service install thing again?  It may well now work...

---

### Post by BoyBlunder on 2007-01-28
yes, I tried to run it again, and no dice. do I need to install upstart?

---

### Post by BoyBlunder on 2007-01-28
I'm seriously considering reformatting and starting from fresh again...

---

### Post by Blutack on 2007-01-28
Do not remove sysvinit or install upstart!
We had come to the end of the path though, for now hopefully a simple sudo aptitude keep-all will fix you up.  You can check with the install -f thing.  For some reason your system thinks sysvinit needs to go.  the keep-all will tell aptitude you want to keep it.

---

### Post by BoyBlunder on 2007-01-28
```

pat@blunderbox:~$ sudo aptitude keep-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
pat@blunderbox:~$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
pat@blunderbox:~$ 

```

seems to be OK, but I still can't install the shared folder services (NFS and SMB)!

---

### Post by Blutack on 2007-01-28
Is it still giving the same error about broken packages?  Seems wierd, cos aptitude now thinks they are fixed.  You can install them manually with synaptic.  I'm going to sleep I'm afraid, hopefully some1 can help you if you need it.

---

### Post by ftmichael on 2007-03-11
No one's touched this in a while so I thought I'd ask, in case things have been fixed up more.  (I'm using Edgy, which I upgraded to from Dapper; I haven't done a fresh install since Hoary.)

> michael@jeezychreezy:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  startup-tasks system-services upstart upstart-compat-sysv upstart-logd 
The following packages will be automatically REMOVED:
  sysvinit 
The following NEW packages will be installed:
  startup-tasks system-services upstart upstart-compat-sysv upstart-logd 
The following packages will be REMOVED:
  sysvinit 
The following packages will be upgraded:
  ubuntu-minimal 
1 packages upgraded, 5 newly installed, 1 to remove and 0 not upgraded.
Need to get 171kB of archives. After unpacking 397kB will be used.
Do you want to continue? [Y/n/?] y
The following ESSENTIAL packages will be REMOVED!
  sysvinit 

WARNING: Performing this action will probably cause your system to break!
         Do NOT continue unless you know EXACTLY what you are doing!
To continue, type the phrase "I am aware that this is a very bad idea":
n
Abort.

michael@jeezychreezy:~$ sudo aptitude show upstart
Package: upstart
New: yes
State: not installed
Version: 0.2.7-7
Priority: required
Section: base
Maintainer: Scott James Remnant <scott@ubuntu.com>
Uncompressed Size: 307k
PreDepends: libc6 (>= 2.4-1), sysvutils (>= 2.86.ds1-14.1ubuntu11)
Recommends: upstart-compat-sysv, upstart-logd, startup-tasks, system-services
Conflicts: sysvinit
Replaces: sysvinit
Description: event-based init daemon
 upstart is a replacement for the /sbin/init daemon which handles starting of
 tasks and services during boot, stopping them during shutdown and supervising
 them while the system is running.

michael@jeezychreezy:~$ sudo aptitude show upstart-compat-sysv
Package: upstart-compat-sysv
New: yes
State: not installed
Version: 0.2.7-7
Priority: required
Section: base
Maintainer: Scott James Remnant <scott@ubuntu.com>
Uncompressed Size: 160k
Depends: libc6 (>= 2.4-1), upstart (= 0.2.7-7), sysvutils (>=
         2.86.ds1-14.1ubuntu11), sysv-rc, initscripts
Replaces: upstart (< 0.2.0-1), sysvinit
Description: compatibility for System-V-like init
 This package contains compatibility tasks and utilities that emulate the
 behaviour of the original sysvinit package, including runlevels, and ensures
 that the initscripts in /etc/rc*.d are still run.

Should I leave well enough alone, even now?

Michael

---

