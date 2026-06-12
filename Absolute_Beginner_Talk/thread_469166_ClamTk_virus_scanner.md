---
title: "ClamTk virus scanner"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-06-09
Unable to view ClamAV's information file.
This will affect
how ClamTk views the number of viruses and version information.
i got error like this i installed by automartix2
and  when i try to scan a file it say
You do not appear to have virus definitions!

Running "freshclam -v" as root may fix the problem.

---

### Post by tuxsoul on 2007-06-10
Hi, sorry my english is no good :(

The error in ClamTK, is why the freshclam have wrong configuration, if you don't have run clamd (daemon clamav), you need check this in console:

```

$sudo dpkg-reconfigure clamav-freshclam

```

Answer the ask, but when ask "Should clamd be notified after updates?", you will answer "no".

---

### Post by zerobinary on 2007-06-10
zerobinary@zerobinary:~$ $sudo dpkg-reconfigure clamav-freshclam
/usr/sbin/dpkg-reconfigure must be run as root
zerobinary@zerobinary:~$

---

### Post by Acglaphotis on 2007-06-10
try taking out the $ symbol before the sudo.

---

### Post by zerobinary on 2007-06-11
You must be root to install updates.

---

### Post by gatdammit on 2007-06-21
[http://ubuntuforums.org/showthread.php?t=407356&highlight=unable+to+view+clamav%27s+information](http://ubuntuforums.org/showthread.php?t=407356&highlight=unable+to+view+clamav%27s+information)

Worked for me

---

### Post by zerobinary on 2007-06-21
still no goal

---

### Post by diatribe on 2007-06-21
Running "freshclam -v" as root may fix the problem.

sudo freshclam -v

---

### Post by zerobinary on 2007-06-22
still no goal

---

### Post by gatdammit on 2007-06-23
how bout this?

[http://www.gossamer-threads.com/lists/clamav/users/31711](http://www.gossamer-threads.com/lists/clamav/users/31711)

goodluck

---

### Post by zerobinary on 2007-06-23
Some distributions do not automatically edit
freshclam.conf and clamd.conf under /etc.
Please edit those before attempting signature updates.
i got this error after trying that 
is there any good virus scanner besides that
o thx sorry
still is there any good virus scanner 
thx u guys help u a lot

---

### Post by zerobinary on 2007-06-25
probelm fix but is there any good virus scanner beside that

---

