---
title: "what do i go i get the same error no matter what i try to install...."
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by amckinn072485 on 2007-10-25
antonio@antonios-computer:~$ sudo apt-get -y install xmms
[sudo] password for antonio:
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
  xmms: Depends: libmikmod2 (>= 3.1.10) but it is not installable
E: Broken packages
i was trying to install xmms but to no avail i couldnt do anything but get this error :confused: any kind of help will be greatly apperciated

---

### Post by Maestro23 on 2007-10-25
Do you have all your Repositories enabled?

System>>Admin>>Software Resources.

Also, you can try the "Fix Broken Packages" option in Synaptic.

---

### Post by amckinn072485 on 2007-10-25
hmmmmmmm it seems to be working now

---

