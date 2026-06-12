---
title: "Upgrade Package"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by belred on 2008-01-25
if you are using for example fiesty and a package is at a version you want in gusty and you don't want or can't upgrade to gusty... how do you upgrade the package?  do you add a repository entry to sources.list, install the new package, then delete the line in sources.list?

also, is it ok to install the current version of a package via the package manager, then later manually install a .deb ?  will that confuse anything?

thanks,

bryan

---

### Post by PmDematagoda on 2008-01-25
It mostly depends on the application itself, if the application is a system component and has many other dependencies then it is not recommended, but if the application is just any other application and does not have many dependencies then you should not have much of a problem by simply installing the package and leaving the sources.list file intact.

And yes, it is ok to update the package using update-manager and then install the .deb, but once again, the type of application you are installing plays a part as mentioned previously.

---

### Post by carlossousa on 2008-03-18
Hi,

It really must be different for every application installed in ubuntu, but is it a reliable usage of linux? I have 6.10 running nicely on my system, but for works sake, I need openoffice 2.3.
Do I really have to install 7.10??? Or is there another recommended way to work?

Thanks

Carlos

---

### Post by PmDematagoda on 2008-03-18
> **carlossousa said:**
> Hi,

It really must be different for every application installed in ubuntu, but is it a reliable usage of linux? I have 6.10 running nicely on my system, but for works sake, I need openoffice 2.3.
Do I really have to install 7.10??? Or is there another recommended way to work?

Thanks

Carlos
If Ubuntu 6.10 has the dependencies required to run Open Office 2.3 then you should be able to upgrade Open Office with ease, however if Ubuntu 6.10 does not have the required dependencies then you may have to look to other methods.

---

