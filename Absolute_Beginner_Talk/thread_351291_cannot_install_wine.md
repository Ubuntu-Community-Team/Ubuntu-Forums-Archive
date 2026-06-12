---
title: "cannot install wine"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by pluskwa on 2007-02-01
HEy 
i tried to install wine but sth went wrong...
now when i try i get a message:
the following packages have unresolvable dependencies
wine:
  Depends: libasound2 (>1.0.11) but 1.0.10-2ubuntu4 is to be installed
  Depends: libc6 (>=2.4-1) but 2.3.6-0ubuntu20.2 is to be installed
  Depends: libgcc1 (>=1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
  Depends: libglib2.0-0 (>=2.12.0) but 2.10.3-0ubuntu1 is to be installed
  Depends: libgphoto2-2 (>=2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
  Depends: libgphoto2-port0 (>=2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
  Depends: libstdc++6 (>=4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
  Depends: libusb-0.1-4 (>=2:0.1.12) but 2:0.1.10a-22ubuntu1 is to be installed
  Depends: libxml2 (>=2.6.26) but 2.6.24.dfsg-1ubuntu1 is to be installed
  Depends: libxslt1.1 (>=1.1.17) but 1.1.15-1ubuntu1 is to be installed

---

### Post by STREETURCHINE on 2007-02-01
what method did you use to install wine.?

and you could search synaptic and install the dependancies.

---

### Post by aktiwers on 2007-02-01
Sorry, dont know whats wrong here, but you can install wine through Automatix2.

---

### Post by pluskwa on 2007-02-02
I used console, but it wasn't working
so i try to remove it and install it from synaptic packet manager 
and than i got those errors

---

### Post by pluskwa on 2007-02-02
+ how do I install dependencies in synaptic??

---

### Post by slimdog360 on 2007-02-02
its already in the repos but... if you want to you can use this.
[http://www.winehq.com/site/download-deb]("http://www.winehq.com/site/download-deb")

---

### Post by pluskwa on 2007-02-02
nope it doesn't work, 
same problem
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
  wine: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.2 is to be installed
        Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed        Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed        Depends: libgphoto2-2 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed        Depends: libgphoto2-port0 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
        Depends: libusb-0.1-4 (>= 2:0.1.12) but 2:0.1.10a-22ubuntu1 is to be installed
        Depends: libxml2 (>= 2.6.26) but 2.6.24.dfsg-1ubuntu1 is to be installed        Depends: libxslt1.1 (>= 1.1.17) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages

---

