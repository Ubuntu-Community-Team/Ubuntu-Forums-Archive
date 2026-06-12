---
title: "shared libraries error"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by xstation on 2005-12-26
Can someone help me with this please:D :D :D 

andy108@heis:~$ cd /opt/kerio/mailserver
andy108@heis:/opt/kerio/mailserver$ sudo ./cfgwizard
./cfgwizard: error while loading shared libraries: libstdc++.so.5: cannot open s hared object file: No such file or directory

---

### Post by gsdefender on 2005-12-26
You should install the libstdc++5-3.3-dev package, that contains the compatibility library for your software. You should also install the C and C++ compilers if you can, because they would already be providing this file for you.

---

### Post by Hotchilli on 2005-12-26
thanks for your post

but still having dep problems see below

which comes first?:smile: :smile: 

andy108@heis:~/Desktop$ sudo dpkg -i g++-3.3_3.3.6-8ubuntu1_i386.deb
(Reading database ... 65530 files and directories currently installed.)
Preparing to replace g++-3.3 1:3.3.6-8ubuntu1 (using g++-3.3_3.3.6-8ubuntu1_i386.deb) ...
Unpacking replacement g++-3.3 ...
dpkg: dependency problems prevent configuration of g++-3.3:
 g++-3.3 depends on libstdc++5-3.3-dev (= 1:3.3.6-8ubuntu1); however:
  Package libstdc++5-3.3-dev is not configured yet.
dpkg: error processing g++-3.3 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 g++-3.3
andy108@heis:~/Desktop$ sudo dpkg -i libstdc++5-3.3-dev_3.3.6-8ubuntu1_i386.deb
(Reading database ... 65530 files and directories currently installed.)
Preparing to replace libstdc++5-3.3-dev 1:3.3.6-8ubuntu1 (using libstdc++5-3.3-dev_3.3.6-8ubuntu1_i386.deb) ...
Unpacking replacement libstdc++5-3.3-dev ...
dpkg: dependency problems prevent configuration of libstdc++5-3.3-dev:
 libstdc++5-3.3-dev depends on g++-3.3 (>= 1:3.3.6-8ubuntu1); however:
  Package g++-3.3 is not configured yet.
dpkg: error processing libstdc++5-3.3-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libstdc++5-3.3-dev

---

### Post by Perfect Storm on 2005-12-26
Don't you have internet on your ubuntu to grab these packages with synaptic packager Manager?

---

### Post by Hotchilli on 2005-12-26
what a beautiful destop number 1
answer to your question not working just yet

but  my question in last post remains:smile: :smile: :smile: :smile:

---

### Post by Perfect Storm on 2005-12-26
you could try with force. (on your own risk)

dpkg --help

---

