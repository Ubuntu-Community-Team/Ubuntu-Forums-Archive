---
title: "WineHQ Wont install due to lack f dependencies"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by hayward room on 2007-05-04
Hi there- trying to install WineHQ but got this error: 

# apt-get install wine
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
E: Broken packages

Does any of you have an idea on how to resolve this? 

I have the latest version of build-essentials installed and all libs updated. 

Let me know. Thnx! :)

---

### Post by Campingman on 2007-05-04
Have you tried installing via add/remove or synaptic package manager?

---

### Post by hayward room on 2007-05-04
> **Campingman said:**
> Have you tried installing via add/remove or synaptic package manager?

Yes I did infact tried that but still gave me this error: 

Could not mark all packages for installation: 

The following packages have unresolved dependencies. 
Make sure that all required repositories are added and enabled in the preference. 

Any other ideas? Thnx!

---

