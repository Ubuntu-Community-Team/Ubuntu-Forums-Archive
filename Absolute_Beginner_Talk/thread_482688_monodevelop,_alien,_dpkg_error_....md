---
title: "monodevelop, alien, dpkg error ..."
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-06-23
Trying to install the latest version of MonoDevelop but getting an error.

First I convert the .rpm file to .deb ....

$ sudo alien monodevelop-0.14-0.novell.noarch.rpm


Then I try to install but get the following error ...

$ sudo dpkg -i monodevelop_0.14-1_all.deb
(Reading database ... 172502 files and directories currently installed.)
Preparing to replace monodevelop 0.12+dfsg-1ubuntu1 (using monodevelop_0.14-1_all.deb) ...
Unpacking replacement monodevelop ...
dpkg: error processing monodevelop_0.14-1_all.deb (--install):
 trying to overwrite `/usr/lib/monodevelop/AddIns/MonoQuery/Mono.Data.Sql.dll', which is also in package monodevelop-query
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 monodevelop_0.14-1_all.deb


I removed the MonQuery directory but get the same error.

Any ideas?

Thanks

Carl

---

### Post by BobCFC on 2007-06-24
I would try searching for old monodevelop and monodevelop-query in Synaptic and remove it properly before installing new version.

---

### Post by cwmoser on 2007-06-24
> **BobCFC said:**
> I would try searching for old monodevelop and monodevelop-query in Synaptic and remove it properly before installing new version.


Dawg gone.  That fixed it - going to Synaptic and uninstalling the old allowed me to install the latest version.  
I feel as dumb as a stump sometimes:-)

Thanks for the help.

Carl

---

### Post by BobCFC on 2007-06-24
I had same thing with nvidia drivers don't worry

---

