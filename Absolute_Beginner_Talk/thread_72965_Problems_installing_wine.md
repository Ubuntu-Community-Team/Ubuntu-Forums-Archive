---
title: "Problems installing wine"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by bmarilena on 2005-10-07
I have some problems installing wine...

After 

 dpkg -i wine*.deb

I got

[I]Unpacking wine-utils (from wine-utils_0.0.20050310-1.1_i386.deb) ...
dpkg: dependency problems prevent configuration of wine:
 wine depends on libwine (= 0.0.20050310-1.1); however:
  Version of libwine on system is 0.0.20050725-winehq-1.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
Setting up wine-doc (0.0.20050310-1.1) ...

dpkg: dependency problems prevent configuration of wine-utils:
 wine-utils depends on libwine (= 0.0.20050310-1.1); however:
  Version of libwine on system is 0.0.20050725-winehq-1.
 wine-utils depends on wine; however:
  Package wine is not configured yet.
dpkg: error processing wine-utils (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine
 wine-utils
[/I]

Have no idea what should I do next

Can you help me?

Marilena

---

### Post by Ampersand on 2005-10-07
Hi 
Have you added all of the apt repositories? If not, follow the instructions in [http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories) and [https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports), then try again.

It looks like you should be able to install wine from the Universe repository

---

### Post by bmarilena on 2005-10-07
:) thanks!

I added all the repos... and until here everything went smooth.

I'll try youre suggestion.

---

### Post by hayward room on 2007-05-05
> **bmarilena said:**
> :) thanks!

I added all the repos... and until here everything went smooth.

I'll try youre suggestion.

I have added all required repos but still got this error message: 
[I][B]
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
  wine: Depends: libasound2 (> 1.0.12) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.4 is to be installed
        Depends: libgcc1 (>= 1:4.1.2) but 1:4.0.3-1ubuntu5 is to be installed
        Depends: libgphoto2-2 (>= 2.3.0) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libgphoto2-port0 (>= 2.3.0) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libstdc++6 (>= 4.1.2) but 4.0.3-1ubuntu5 is to be installed
        Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is to be installed
        Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages[/B][/I]

Any ideas on how to resolve this? Thnx! :confused:

---

