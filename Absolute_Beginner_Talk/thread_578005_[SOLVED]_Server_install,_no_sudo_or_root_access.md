---
title: "[SOLVED] Server install, no sudo or root access"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by nowhere@cox.net on 2007-10-16
Hi everyone,
I did a Gutsy Server installation on a clean machine, Everything went find and I can log in with my user name the install process set up. BUT:
sudo vi phpinfo.php
[sudo] password for dauser:
dauser is not in the sudoers file.  This incident will be reported.

Also, I never had any opportunity to set up a root password. Now what do I do?

Thanks!
Eric

---

### Post by 5-HT on 2007-10-16
Booting up into recovery mode will give you root access where you can add yourself to the sudoers file and set up a root password if wanted.
Otherwise, append init=/bin/bash to your boot options to get a full root shell, mount any needed drives, and fix things from there (or just append 'single' to your boot options).

cheers,

---

### Post by nowhere@cox.net on 2007-10-17
Hi thanks,

Recovery mode is what I needed.  Once in I had to edit the group and sudoers file to create an "admin" group, give it sudo root priviledges and add the user to that group. Good learning experience but I'm confused why server install didn't do it by default. 

Now that I know how to do it, I don't want to do it when i install a new server. Should be part of the install.

Anyway.

Thanks for the tip!
Eric

---

### Post by az on 2007-10-17
> **nowhere@cox.net said:**
> Hi thanks,

Recovery mode is what I needed.  Once in I had to edit the group and sudoers file to create an "admin" group, give it sudo root priviledges and add the user to that group. Good learning experience but I'm confused why server install didn't do it by default. 

Now that I know how to do it, I don't want to do it when i install a new server. Should be part of the install.

Anyway.

Thanks for the tip!
Eric

It is part of the install.  Perhaps your install disk is corrupt?

---

### Post by nowhere@cox.net on 2007-10-17
Yah it's weird for sure. I don't think there is anything wrong with the disk. The install works perfectly except that the admin group was missing. I bet it was a bug or oversight that has been corrected (nor not). 

Anyway. Fixed now!

:)

Eric

---

