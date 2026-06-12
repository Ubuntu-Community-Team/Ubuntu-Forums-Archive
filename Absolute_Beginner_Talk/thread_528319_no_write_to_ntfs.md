---
title: "no write to ntfs"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by endo666 on 2007-08-17
i had installed the stuff to read and write to NTFS and it was working but now i cant write to the drive so what do i need to do. i tried to install the _sudo apt-get install ntfs-config_ and this is what i got.


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
  ntfs-config: Depends: libdbus-1-2 (>= 0.60) but it is not installable
E: Broken packages

---

### Post by bodhi.zazen on 2007-08-17
Ouch ...

Make sure your repositories are enabled and re-try

Otherwise either [file a bug report](https://bugs.launchpad.net/distros/ubuntu/+bugs) or wait.

---

### Post by AlexenderReez on 2007-08-17
i know this error...i saw a newbie in my place counter it before....you are using older repository like dapper for newer version of ubuntu like edgy or feisty..check it again...

don't worry....ntfs is not at testing stage ..it is quite difficult to get bug...

---

### Post by endo666 on 2007-08-18
> **AlexenderReez said:**
> i know this error...i saw a newbie in my place counter it before....you are using older repository like dapper for newer version of ubuntu like edgy or feisty..check it again...

don't worry....ntfs is not at testing stage ..it is quite difficult to get bug...

thank you i figured it our you were rite i was using an older repository which is strange because when i had it working the first time that is what i did. 

[here is the link to the instructions i used]("http://ubuntuforums.org/showthread.php?t=217009")

then i used this but changed it to read feisty deb [http://flomertens.free.fr/ubuntu/](http://flomertens.free.fr/ubuntu/) edgy main main-all

---

