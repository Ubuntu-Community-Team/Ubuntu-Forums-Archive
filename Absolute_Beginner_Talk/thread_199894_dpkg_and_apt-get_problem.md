---
title: "dpkg and apt-get problem"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by kingmonkey on 2006-06-19
I installed xubuntu-desktop on top of my ubuntu. I think it had some problems installing and I now get the following error messages:

```
$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 28045:
 `binst' is not allowed for first (want) word in `status' field

```

and 

```
~$ sudo apt-get upgrade
Reading package lists... Error!
E: Malformed 1st word in the Status line
E: Error occurred while processing libgwrapguile1 (UsePackage3)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

Please help. What do I have to do to get apt-get working again?

---

### Post by kingmonkey on 2006-06-19
Easily fixed, but don't know whether the statuses of some of my packages are wrong now.

There are of backups of /var/lib/dpkg/status at:

/var/lib/dpkg/status-old

and

/var/backups/dpkg.status*

---

### Post by cibara on 2007-03-06
I just experienced nearly the exact same problem with in Edgy with an update over the weekend. My error:

Reading package lists... Error!
E: Malformed 1st word in the Status line
E: Error occurred while processing jfsutils
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

So i just moved the damaged status file to name status-damaged and moved *-old to current. The date stamp of the "status-old" file corresponds to when the error began, so perhaps this will repair the issue. But, like the original poster here, i hope and wonder that there will be no damaged dependencies from this action.

---

