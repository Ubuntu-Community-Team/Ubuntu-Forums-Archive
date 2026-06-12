---
title: "Can't Download A Thing"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-10-07
I get this every time I try to install ANYTHING:

dpkg: error processing liblog4j1.2-java-doc (--configure):
subprocess post-installation script returned error exit status 2
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
liblog4j1.2-java-doc
clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)
--23:06:04-- [http://ubuntu.secs.oakland.edu/pool/..._1-3_amd64.deb](http://ubuntu.secs.oakland.edu/pool/..._1-3_amd64.deb)
=> `linux32_1-3_amd64.deb'


Any idea on how to fix any of this? Sometimes the thing I am downloading really works. But most of the time it just gives me this error, and well...doesn't.

---

### Post by OptimusPrime on 2006-10-07
Heck, just tell me to pick up my laptop, and throw it against the wall while screaming the lyrics to "Come sail away".  Anything is better than nothing.

---

### Post by slimdog360 on 2006-10-07
is this from apt-get is it?

---

### Post by OptimusPrime on 2006-10-07
Yes, and from Add/Remove.  And anyware else you can (and can't) think of](*,)  It makes me hate me.

---

### Post by Dinerty on 2006-10-07
A user had the same problem as you and managed to solve it by:

[http://ubuntuforums.org/showthread.php?t=186356](http://ubuntuforums.org/showthread.php?t=186356)

---

