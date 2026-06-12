---
title: "CalmTk antivirus update"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by acpsiddhartha on 2007-05-15
Hi 
I have installed CalmTk antivirus using AutoMatix. When I open the CalmTk it says "Warning:
Your virus signatures are 33 days old!"  and if I try to update it it says "you must be a root to install update" .. how do i update then??

Thanks

---

### Post by Saphira on 2007-05-16
Maybe this will help...

1. IGNORE the use of Automatix 

Automatix does not work. Refer to these sites for more formalized documentation -- [http://wiki.ubuntu.com](http://wiki.ubuntu.com) [http://ubuntuguide.org](http://ubuntuguide.org) [http://doc.gwos.org](http://doc.gwos.org) for better help.

Automatix is known for breaking systems and you'll find that you really don't need it. It may also make upgrading your system later difficult. With Feisty most of the stuff you'll use Automatix to install is already a one click install either via add/remove applications or by referral to one of the above sources.

2. sudo apt-get install freshclam 

3.  sudo freshclam to update your clam definitions.

---

