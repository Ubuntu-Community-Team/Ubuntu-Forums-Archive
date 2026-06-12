---
title: "kxdocker problem"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by STiKi on 2006-11-19
Hello everybody.
I'm a little confused because I can't find answer to my weird problem.
I cannot run kxdocker on a fresh Edgy Eft install - and I dunno why.
Here's the output from console:
```
tomek@apofis:~$ kxdocker
KXDocker Will use Composite Extensions!
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources
kxdocker: WARNING: loading xml...
kxdocker: WARNING: Warning user kxdocker_conf.xml may be corrupt: loading last backup!
kxdocker: WARNING: Warning user, and backup configurations are corrupt! I'm going to load system kxdocker_conf.xml !!!
kxdocker: WARNING: Warning user, backup, system configurations are corrupt! please install right kxdocker_conf.xml
ERROR: Communication problem with kxdocker, it probably crashed.
```

---

### Post by lalakis85 on 2007-03-20
From your output no plugins are loaded. Which files of kxdocker did you install?

---

### Post by lalakis85 on 2007-03-20
And what's the version of kxdocker?

---

### Post by koshari on 2007-04-30
you need some extra kde packages see, [http://ubuntuforums.org/showthread.php?t=369353](http://ubuntuforums.org/showthread.php?t=369353)

---

### Post by rebegin on 2007-05-03
installing debian packages worked for me:
[http://packages.debian.org/testing/x11/kxdocker](http://packages.debian.org/testing/x11/kxdocker)
[http://packages.debian.org/testing/x11/kxdocker-data](http://packages.debian.org/testing/x11/kxdocker-data)

---

