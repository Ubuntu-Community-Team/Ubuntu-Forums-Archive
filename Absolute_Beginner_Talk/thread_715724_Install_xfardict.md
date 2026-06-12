---
title: "Install xfardict"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-03-05
Hello! I wanted to install xfardict. So I downloaded the gutsy .deb package. But I got this:
[IMG]http://i25.tinypic.com/1zptr80.png[/IMG]
Then I added "http://parsix.org/packages ramon main" to my software sources. I got this:
[IMG]http://i32.tinypic.com/2ufr14k.png[/IMG]
(what does it mean?)
Then I typed "sudo apt-get install xfardic," but I got this:
```
hooman@hooman-laptop:~$ sudo apt-get install xfardic
[sudo] password for hooman:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xfardic: Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu10 is to be installed
           Depends: libespeak1 (>= 1.30) but 1.29-0ubuntu3 is to be installed
           Depends: liborbit2 (>= 1:2.14.10) but 1:2.14.9-0ubuntu1 is to be installed
           Depends: libpango1.0-0 (>= 1.18.4) but 1.18.3-0ubuntu1 is to be installed
           Depends: libwxbase2.6-0 (>= 2.6.3.2.2) but 2.6.3.2.1.5ubuntu12 is to be installed
           Depends: libwxgtk2.6-0 (>= 2.6.3.2.2) but 2.6.3.2.1.5ubuntu12 is to be installed
E: Broken packages
hooman@hooman-laptop:~$ 

```
How can I install this program and what's the problem?
+++
After I added parsix to my software sources I got a lot of updates, but I cancelled all of them because they were 55 and removed parsix from software sources. Should I install all those updates before installing this program?
____
Thank you!

---

### Post by justleen on 2008-03-05
go to system > adminitstration > Software soruces.

Make sure that multiverse and universe are selected. reload the software list (sudo apt-get update) and try to install it again.

Synaptic will always try to resolve the dependencies for you, but if you dont enable the correct repositories, it will tell you t cant install because of unresolved deps.

---

