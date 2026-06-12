---
title: "[SOLVED] Installing New Thunderbird"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by phil66 on 2007-04-20
Ubuntu Dapper w/ Thunderbird 1.5.0.10 currently installed

I am trying to install Thunderbird 2.0.0.0 using

"Automated Script to install the newest Thunderbird."

Downloaded script to desktop and copied command to terminal

Scripts run all the way thru the steps down to after asking to backup  profile.

Next entry is the following error

"ln: Creating symbolic link /home/ray/.thunderbird to /home/ray/.mozilla-thunderbird: file exist"

previous command did not complete successfully. exiting

Previously downloaded Thunderbird 1.5.0.10 using script without any problems

Why can i not install 2.0.0.0 using the same script when its show 2.0.0.0 as the latest version available.

Thanks
Ray

---

### Post by igknighted on 2007-04-20
It is running into the previous install.  I would simply go to the mozilla site and get the tarball with the new thunderbird and extract it to /opt.  It should then take over the old .thunderbird folder and assume all your settings.

---

### Post by phil66 on 2007-04-20
Surely their is a better easier way than using the tarball.

Nanotube and asyiu wrote the first script but I can not find it now

Thanks anyway
Ray

---

### Post by IndyBob on 2007-04-20
phil66

Here's your link for installing the new Thunderbird with the script.

[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

Hope that helps!

---

### Post by aysiu on 2007-04-20
Try this: ```
mv ~/.thunderbird ~/.thunderbird.old
``` and then run the script again.

---

### Post by igknighted on 2007-04-20
> **phil66 said:**
> Surely their is a better easier way than using the tarball.

Nanotube and asyiu wrote the first script but I can not find it now

Thanks anyway
Ray

I don't really see the purpose of the script, its just a simple extract to a directory... unless the script symlinks to /usr/bin and adds menu entries?

---

### Post by phil66 on 2007-04-21
> **aysiu said:**
> Try this: ```
mv ~/.thunderbird ~/.thunderbird.old
``` and then run the script again.

Thanks Asyiu

This worked with no hassle.

Thunderbird 2.0.0.0 now downloaded profile in tack and working fine.

Thanks again for the help

Ray

---

