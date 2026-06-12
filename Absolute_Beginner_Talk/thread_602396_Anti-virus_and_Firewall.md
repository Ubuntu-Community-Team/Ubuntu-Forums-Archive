---
title: "Anti-virus and Firewall"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by dragon4021 on 2007-11-04
I am new to the Linux world too. Tired of dealing with all the Windows BS and viruses. Even though there is alot less threat of getting a virus with Linux, I would still like to have some sort of protection. There is an anti-virus I've trusted for years called Avast 4.0 that I would like to install on my Linux system. I'm just not use to the process with Linux. They offer 3 types for Linux based machines. (RPM, DEB, and TAR GZ) Which one do I use and how do I install it. I would appreciate some help. I would also appreciate if someone can point me in the direction of an effective firewall for Linux too.

---

### Post by mikewhatever on 2007-11-04
The deb file is right for Ubuntu. [http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html](http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html)
Avast on linux is just an on-demand scanner. It does not run by default or provide shields.

There is a built in firewall in Ubuntu. You do not normally need to configure it unless running a server.

Check this link for more info [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Skardal on 2007-11-04
Your choice is .deb! :)

Ubuntu is based on [Debian]("http://www.debian.org"), and deb's are Debian packages.
When you install something in Ubuntu through apt-get/synaptic, what's actually happening is that the system downloads all the needed deb's and installs them, which is really nice!

To install a single .deb file do:

```
sudo dpkg -i yourpackage.deb
```

---

### Post by ikki_72 on 2007-11-06
yeah..and use ```
avast location
``` to scan location intended
..which brings me to my question. Why in the hell I can't seem to 'really' scan my ntfs disk? What I did was:
```
sudo avast /dev/hdc
```

then came out:
```
/dev/hdc        [OK]
#
# Statistics:
#
# scanned files:        1
# scanned directories:  0
# infected files:       0
# total file size:      512.0 B
# virus database:       000714-0 15.02.2007
# test elapsed:         0s 1ms
#

```

?? Only 1 file? Look at the 2nd last line. Too conveniently fast!

Anyone know how to really scan and remove virus in ntfs partition from ubuntu? I damned know there's a virus in there since Kapersky keeps barking about trojan or something..

---

### Post by dragon4021 on 2007-11-06
Sorry for being such a noob at this. I downloaded the deb file and went to the applications tab and clicked add/remove. It didnt show up on any lists. I'm so lost,

---

### Post by Steveway on 2007-11-06
Double-clicking the .deb file should do it.
But I would advise against using it, it will only scan for windows-viruses so why bother and waste ressources?

---

### Post by oilchangeguy on 2007-11-06
> **dragon4021 said:**
> I am new to the Linux world too. Tired of dealing with all the Windows BS and viruses. Even though there is alot less threat of getting a virus with Linux, I would still like to have some sort of protection. There is an anti-virus I've trusted for years called Avast 4.0 that I would like to install on my Linux system. I'm just not use to the process with Linux. They offer 3 types for Linux based machines. (RPM, DEB, and TAR GZ) Which one do I use and how do I install it. I would appreciate some help. I would also appreciate if someone can point me in the direction of an effective firewall for Linux too.

there are no viruses for linux. and ubuntu already has a built in firewall. it's called iptables.

---

