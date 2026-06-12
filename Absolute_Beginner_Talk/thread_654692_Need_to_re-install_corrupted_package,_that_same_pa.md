---
title: "Need to re-install corrupted package, that same package preventing my re-install"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by abben on 2007-12-31
Would greatly appreciate any help as to how I can re-install libavahi-core5, it's missing newline is getting in the way of literally every package change I try to make, including it's own!

[HTML]abben@abben-desktop:~$ sudo apt-get remove libavahi-core5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  avahi-daemon libavahi-core5 libnss-mdns xubuntu-desktop
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 848kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing xubuntu-desktop (--remove):
 files list file for package `libavahi-core5' is missing final newline
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly[/HTML]

---

### Post by abben on 2007-12-31
Bump. Thanks for any help.

---

### Post by charleseddy on 2008-01-15
This usually happens after filesystem corruption, when fsck removes or changes things that corrupt dpkg/info.  This solution should work:

1. sudo gedit /var/lib/dpkg/status
2. Delete the section for libavahi-core5.
3. sudo mv /var/lib/dpkg/info /var/lib/dpkg/info_old
4. sudo mkdir /var/lib/dpkg/info
5. sudo apt-get update
6. sudo apt-get -f install

Also, I apologize for the fact that it took so long for a response.  If you need anything else, feel free to ask.

---

### Post by hamzamusa on 2008-02-14
Thanks Charles it works for me .

---

