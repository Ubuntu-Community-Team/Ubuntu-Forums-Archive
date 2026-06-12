---
title: "Wired issue by trying to install legacy fglrx driver (deb packages) on 12.04"
date: 2014-01-05
forum: Any Other OS
---

### Post by michal.t on 2014-01-05
Hi all!
I am having a very strange issue by trying to install the legacy 13.1 fglrx driver on a linux mint 13 machine (based on 12.04).
I have generated the deb packages by starting the installer with the "buildpkg Ubuntu/precise " parameter.
Packages have been generated.
Once I am trying to install the first one (fglrx_8.970-0ubuntu1_amd64.deb) I got a very wired error...I am reporting here what really happens on my shell:

(Reading database ... 174786 files and directories currently installed.)
Unpacking fglrx (from fglrx_8.970-0ubuntu1_amd64.deb) ...
dpkg: error processing fglrx_8.970-0ubuntu1_amd64.deb (--install):
 unable to open '/usr/lib/fglrx/libXvBAW.so.1.0.dpkg-new': No such file or directory
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx_8.970-0ubuntu1_amd64.deb


I am just installing it as su so I really have no idea of what the heck is going on...
Thank you!

---

### Post by Mark Phelps on 2014-01-05
What make and model AMD video chipset are you using"? Asking because AMD dropped Linux support for their HD 2x/3x/4x-series cards last summer and, as a result, the fglrx drivers don't work on any Ubuntu version newer than 12.04.1.

---

### Post by Bucky Ball on 2014-01-05
*Thread moved to **Other OS/Distro Support**.*

You might consider posting here as well:

[http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

### Post by michal.t on 2014-01-05
My card seems to be a 4250 ...the driver however is the legacy one...it should have both the support for 4xxx adapters and linux mint 13 should fit as well.

---

### Post by michal.t on 2014-01-05
Then,,,the driver has been build from the amd installer so if some error had to be occur it had to be during the generation procedure...the issue seems to be something conflicts with the dpkg crap stuff.

---

### Post by michal.t on 2014-01-05
The same issue happens if I am trying to install the fglrx driver from official repos using both apt-get and synaptic...that wired dpkg error does occurs.

---

### Post by michal.t on 2014-01-05
> **Bucky Ball said:**
> *Thread moved to **Other OS/Distro Support**.*

You might consider posting here as well:

[http://forums.linuxmint.com/](http://forums.linuxmint.com/)


By doing that you are not helping me so much considering the nature of the issue...then mint 13 is built up on 12.04...and mint is not so diffused as ubuntu...that s why I came here.
Please use some good taste before applying strict forum rules.

---

### Post by michal.t on 2014-01-05
The solution was in removing the lib32 symbilic link to /usr/lib
I got this: /usr/lib /usr/lib32 and /usr/lib64 ...getting rid of the /usr/lib32 symbolic link finally did the trick and let me install the so long awaited fglrx driver.

---

