---
title: "dpkg error..."
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by ARandomKid on 2007-07-10
Whenever I try to unpackage and install a .deb file or use apt-get to install someting, I get this error after everything's been downloaded (if using apt-get), or jjust using dpkg:

> Fetched 85.3MB in 12m22s (115kB/s)
Preconfiguring packages ...

dpkg: parse error, in file `/var/lib/dpkg/status' near line 7529 package `kde-i18n-fr':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by Happy_Man on 2007-07-10
What were you doing immediately prior to when this message started appearing?

---

### Post by ARandomKid on 2007-07-10
I had just installed Knoppix 3.8 while waiting for my Ubuntu 7.04 CD to be shipped...so this is hopefully just a  temporary version. It's been going on ever since I installed Knoppix.

---

### Post by KIAaze on 2007-07-10
Maybe this might help you:
[http://www.linuxquestions.org/questions/showthread.php?t=155478]("http://www.linuxquestions.org/questions/showthread.php?t=155478")

I found it by googling for /var/lib/dpkg/status.

All the persons from the thread seem to have solved their problem, so it sounds rather promising. :)
From what I understood, your problem comes from a corrupted /var/lib/dpkg/status file.
(I can't imagine how this could be related to the installation of another OS...)

The two main solutions seem to be:
-Replace status with status-old (the automatic backup of status)
-Search manually for the corrupted line in the status file and correct/remove it. The "dpkg -l" command seems helpful to find it.

---

