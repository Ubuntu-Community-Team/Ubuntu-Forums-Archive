---
title: "Client installed Ubuntu now OS X won't boot."
date: 2006-08-12
forum: Apple PPC Users
---

### Post by Techie on 2006-08-12
Hi all,

I'm fairly new to the forums, I've been running Unbuntu on my PC for a while. I have an Intel mini so I'm not ready to try my new Mac until there's a fully supported Intel version. I'm a certified PC tech and I'm a volunteer Mac tech. Anyway I have a current case where someone is running a G4 powerbook and had trouble getting Ubuntu installed. So I had them remove all the Linux partitions and go the 'use free space' route. Which appears to have worked fine, but now only Unbuntu boots not OS X.

I've just replied suggesting they add an OS X partition line into the yaboot config as I suspect that might be the problem. If that doesn't work is there any other tricks I can have them try ?.

Cheers,
Rick

---

### Post by Ptero-4 on 2006-08-12
The OSX line in crapboot should do it. That is, if the OSX partition is still there and you know it's number.

---

### Post by Isaac Dupree on 2006-08-15
If OS X is installed in an HFS+ filesystem (it probably is), then, in /etc/yaboot.conf, in addition to "macosx=[wherever]", you need another line containing just "brokenosx".
[quote="yaboot.conf(5)"]brokenosx
              This option causes the menu entry for MacOSX to  execute  \System\Library\CoreServices\BootX  from  the macosx=device  instead  of  the  usual  \\:tbxi.   This is    necessary if OSX is installed onto an HFS+ filesystem instead of UFS. When OSX  is  installed  on  an  HFS+ filesystem MacOS will mount and debless the OSX partition.   Add this option if the OSX menu entry breaks after booting MacOS.  You should  not              use  this  option  if  OSX  is installed on a UFS filesystem, for UFS installs you specify the OSX bootstrap partition which is protected against MacOS.  This option requires macosx= to be set.
[/quote]

---

