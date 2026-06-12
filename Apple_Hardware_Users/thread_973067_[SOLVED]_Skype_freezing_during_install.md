---
title: "[SOLVED] Skype freezing during install"
date: 2008-11-06
forum: Apple Hardware Users
---

### Post by PartisanEntity on 2008-11-06
I downloaded the Ubuntu version of Skype and proceeded to install it as I always used to do by double clicking on the .deb file.

However it just freezes upon trying to download the dependencies and from that point on every time I try to repeat the process I get an error message about a failure to get a lock on the package manager.

I have rebooted three times and tried to install skype always with the same freeze and error messages.

Has anyone experienced this too?

The laptop is a MacBook.

---

### Post by cyberdork33 on 2008-11-06
Are you running 64bit Ubuntu?

Make sure all package management apps are closed and run from the commandline:

```
sudo dpkg -i skype-debian_2.0.0.72-1_i386.deb
```

after you have navigated to the directory were the deb file resides. If there are errors then, please post them.

---

### Post by PartisanEntity on 2008-11-07
Thanks this solved it, for some reason the package manager needed me to manually install the libqt package, I was then able to install Skype normally.

---

