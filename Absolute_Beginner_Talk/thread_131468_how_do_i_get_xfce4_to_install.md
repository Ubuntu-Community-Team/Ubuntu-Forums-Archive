---
title: "how do i get xfce4 to install"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by dusty on 2006-02-16
i've been looking around for a howto.
however, every thing i found doesn't work.
i tried going to synaptic and installing it from there but it tells me some of the libs are uninstallable.

where do i turn?

---

### Post by carlosqueso on 2006-02-16
do you have the universe repository enabled? type ```
cat /etc/apt/sources.list
```  Also type ```
sudo apt-get install xubuntu-desktop
``` and post any errors that come up.

---

### Post by WolfJay_83 on 2006-02-16
Try opening a terminal and typing,
```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

IF you recieve any errors, post them on here and that will help troubleshooting.

---

### Post by dusty on 2006-02-16
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
  xubuntu-desktop: Depends: abiword but it is not going to be installed
                   Depends: graveman but it is not going to be installed
                   Depends: ivman but it is not installable
                   Depends: xfce4 but it is not going to be installed
                   Depends: xfce4-sensors-plugin but it is not going to be insta lled
                   Depends: xfmedia but it is not going to be installed
E: Broken packages


is the message i get when i type
sudo apt-get install xubuntu-desktop

---

### Post by aysiu on 2006-02-16
Something's definitely wrong with your sources.list.
See the first link of my signature to fix it.

---

