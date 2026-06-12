---
title: "uninstalling application"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by redDEADresolve on 2006-09-13
I was trying to install vmware messed up, It gives me this error. I didn't install the right dependencies so when I loaded up instead of getting the setup screen i got nothing. After installing the right dependencies i can't run the install because it tells me i have vmware installed.

How do I unistall, so I can reinstall?

It gives me this error message

red@red-desktop:~/Downloads/vmware$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

red@red-desktop:~/Downloads/vmware$

---

### Post by DarkN00b on 2006-09-13
Open up Synaptic Package Manager and mark vmware for complete removal, then click 'Apply'. That sholuld remove it.

---

### Post by redDEADresolve on 2006-09-13
> **DarkN00b said:**
> Open up Synaptic Package Manager and mark vmware for complete removal, then click 'Apply'. That sholuld remove it.

When I open up Synaptic there is not vmware programs installed

Any help

---

### Post by redDEADresolve on 2006-09-13
bump

---

### Post by wilem on 2006-09-16
I am having the same issue.

---

### Post by wilem on 2006-09-16
nevermind, found the fix here

rm -rf /etc/vmware

[http://www.ubuntuforums.org/showthread.php?t=207227&highlight=previous+vmware](http://www.ubuntuforums.org/showthread.php?t=207227&highlight=previous+vmware)

---

