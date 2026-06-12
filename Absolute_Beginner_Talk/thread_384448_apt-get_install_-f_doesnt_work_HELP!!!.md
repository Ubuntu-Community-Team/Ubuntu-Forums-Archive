---
title: "apt-get install -f doesnt work HELP!!!"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by goodbyewindows on 2007-03-14
I was trying to install conky when a message about dependencies and how I should run "apt-get install -f". It didnt work and now Synaptic and the ubuntu update dont work either telling me ro run "apt-get install -f"
If i type that into a terminal I get:
> me@LAPTOP:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libfontconfig1: Depends: fontconfig-config (= 2.3.2-7ubuntu2) but 2.4.2-1.2 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


---

### Post by goodbyewindows on 2007-03-14
All fine now, Google pulled up a great HOWTO on this forum. [http://www.ubuntuforums.org/showthread.php?t=186672]("http://www.ubuntuforums.org/showthread.php?t=186672")

---

