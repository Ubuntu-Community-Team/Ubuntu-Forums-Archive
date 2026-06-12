---
title: "broken packages!"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by cAllison on 2007-09-17
Will someone explain this to me and let me know how to fix it please?

```
admin@fs1:/$ sudo apt-get install krb5-user
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  krb5-user: Depends: libkrb53 (= 1.4.3-5) but 1.4.3-5ubuntu0.6 is to be installed
             Depends: libkadm55 (= 1.4.3-5) but 1.4.3-5ubuntu0.6 is to be installed
E: Broken packages
```

I think I reinstalled those 2 packages using:
```
admin@fs1:/$ sudo apt-get install libkrb53 --reinstall
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0B/381kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libkrb53.
(Reading database ... 18484 files and directories currently installed.)
Preparing to replace libkrb53 1.4.3-5ubuntu0.6 (using .../libkrb53_1.4.3-5ubuntu0.6_i386.deb) ...
Unpacking replacement libkrb53 ...
Setting up libkrb53 (1.4.3-5ubuntu0.6) ...
```

and
```
admin@fs1:/$ sudo apt-get install libkadm55
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libkadm55
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/166kB of archives.
After unpacking 426kB of additional disk space will be used.
Selecting previously deselected package libkadm55.
(Reading database ... 18484 files and directories currently installed.)
Unpacking libkadm55 (from .../libkadm55_1.4.3-5ubuntu0.6_i386.deb) ...
Setting up libkadm55 (1.4.3-5ubuntu0.6) ...
```

But I'm still not able to install krb5-user :confused:

TIA for any help.

---

### Post by deadgobby on 2007-09-17
Use the super cow powers of aptitude instead of apt-get so your install line will look like this

sudo aptitude install krb5-user

This tell the the system to get the depends to install the program.
Try and see


Gobby

---

### Post by cAllison on 2007-09-17
```
admin@fs1:~$ sudo aptitude install krb5-user
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are BROKEN:
  krb5-user
The following NEW packages will be automatically installed:
  krb5-config
The following packages have been kept back:
  linux-image-server
The following NEW packages will be installed:
  krb5-config
0 packages upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 118kB/129kB of archives. After unpacking 389kB will be used.
The following packages have unmet dependencies:
  krb5-user: Depends: libkrb53 (= 1.4.3-5) but 1.4.3-5ubuntu0.6 is installed.
             Depends: libkadm55 (= 1.4.3-5) but 1.4.3-5ubuntu0.6 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
krb5-user [Not Installed]

Score is -1

Accept this solution? [Y/n/q/?] y
The following packages are unused and will be REMOVED:
  libkadm55
The following packages have been kept back:
  linux-image-server
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 426kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 18497 files and directories currently installed.)
Removing libkadm55 ...
admin@fs1:~$ sudo aptitude install krb5-user
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  krb5-user
The following NEW packages will be automatically installed:
  krb5-config libkadm55
The following packages have been kept back:
  linux-image-server
The following NEW packages will be installed:
  krb5-config libkadm55
0 packages upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 118kB/294kB of archives. After unpacking 815kB will be used.
The following packages have unmet dependencies:
  krb5-user: Depends: libkrb53 (= 1.4.3-5) but 1.4.3-5ubuntu0.6 is installed.
             Depends: libkadm55 (= 1.4.3-5) but 1.4.3-5ubuntu0.6 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
krb5-user [Not Installed]

Score is -1

Accept this solution? [Y/n/q/?] y
The following packages have been kept back:
  linux-image-server
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
```

Not exactly sure what happen here.... but this is all that it did... dont think it installed it though.

---

### Post by deadgobby on 2007-09-17
It did not. Do you have to install the server first before installing a user?
Gobby

---

