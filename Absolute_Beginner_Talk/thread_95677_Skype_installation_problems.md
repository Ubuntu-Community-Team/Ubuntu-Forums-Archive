---
title: "Skype installation problems"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by nortonedd on 2005-11-27
I followed the instructions from the official site:

1. As the root user, add this line to the end of your /etc/apt/sources.list file:
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
2. Then run apt-get update to sync to the latest repository and
apt-get install skype to install the latest version of Skype on your computer.



But when I go the the second step, apt-get install skype, it prompts me with: 
-------------------------------------------------
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but 3:3.3.3-7ubuntu3 is to be installed
E: Broken packages
--------------------------------------------------

Is the repository not good anymore? Thank you for your time.

---

### Post by Leif on 2005-11-27
Try adding these repos instead, and see if the install works :

```

deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

```

---

### Post by nortonedd on 2005-11-27
Thank you very much for your reply, but I've already installed it from the debian package.

---

