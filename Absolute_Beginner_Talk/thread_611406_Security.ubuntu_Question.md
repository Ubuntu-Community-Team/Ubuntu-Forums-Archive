---
title: "Security.ubuntu Question"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by gatoruss on 2007-11-12
New (again) to ubuntu...just downloaded and installed Gusty on an old windows machine...seems to be ok so far....

Here's my question....when loading the OS from the iso disk I burned, near the end of the install a dialogue box popped up telling me that the security files at "security.ubuntu.com" could not be accesses (probably because I did not have a wifi at that time)....dialogue boxed suggested that I deal with this later...Now that I have ubuntu 7.10 installed, how do I deal with that issue?

Thanks.

---

### Post by jfinkels on 2007-11-12
Make sure to update and upgrade all your packages by typing the following in the terminal (Applcations > Accessories > Terminal):```
sudo aptitude update && sudo aptitude safe-upgrade
```

This will update the list of packages available and upgrade all your installed packages to the most up-to-date version.

---

### Post by FuturePilot on 2007-11-12
> **gatoruss said:**
> New (again) to ubuntu...just downloaded and installed Gusty on an old windows machine...seems to be ok so far....

Here's my question....when loading the OS from the iso disk I burned, near the end of the install a dialogue box popped up telling me that the security files at "security.ubuntu.com" could not be accesses (probably because I did not have a wifi at that time)....dialogue boxed suggested that I deal with this later...Now that I have ubuntu 7.10 installed, how do I deal with that issue?

Thanks.

Go to System>Preferences>Software Sources and make sure all of the the boxes are checked in the first tab. You also might want to uncheck the one for the CD-ROM if it is checked. Then go to the updates tab and check the first two boxes. Optionally you can check the last one to enable the backports if you wish. Then click Reload when prompted.

---

### Post by gatoruss on 2007-11-12
Thank you!

---

### Post by MrFSL on 2007-11-13
Sounds like an update issue.

Running the Update manager should fix this.

Or you can open a terminal and type:```
sudo apt-get update
sudo apt-get upgrade

```

---

