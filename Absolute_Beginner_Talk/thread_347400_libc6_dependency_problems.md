---
title: "libc6 dependency problems"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by quercusrobur2002 on 2007-01-27
I was originally posting under the thread 'Broken Package manager', however I seem to have whittled down the issue to something more specific...

when i  try to install a program using Package Manager I get this error message;

"E: locales: subprocess post-installation script returned error exit status 139
E: libc6: dependency problems - leaving unconfigured"

Also got the same message complaining about libc6 when I tried to use the update manager from the top panel...

Any suggestions??? What is libc6 and how do I fix it???

I'm using Dapper Drake btw.

---

### Post by SSupport on 2007-01-27
Here is a link for info on the libc6 package, and the download links. 
Hope this helps.

[http://packages.debian.org/stable/libs/libc6](http://packages.debian.org/stable/libs/libc6)

---

### Post by quercusrobur2002 on 2007-01-27
> **SSupport said:**
> Here is a link for info on the libc6 package, and the download links. 
Hope this helps.

[http://packages.debian.org/stable/libs/libc6](http://packages.debian.org/stable/libs/libc6)

 Hi there, thanks for this link but I'm not sure where to progress from here, should I download something from this page, and how would I then install it as package Manager isn't working? I sort of feel in a chicken and egg situation, and don't want to make matters worse... sorry to appear ignorant...

---

### Post by cjssmo on 2007-01-27
I havn't read this yet but it might help

[http://www.ubuntuforums.org/showthread.php?t=345446](http://www.ubuntuforums.org/showthread.php?t=345446)

Going to go read it myself.

---

### Post by quercusrobur2002 on 2007-01-27
Checked this thread out but it didn't really seem to help, TBH I didn't really understand most of it. As before, it seems a chicken and egg situation, that thread seemed to suggest downloading and installing a difernt version of libc6, but whatever the problem is with libc6, it is preventing me downlaoding or installing anything at the moment. 

How it seems to me is that Synatpic won't work until the issue with libc6 has been resolved, but the issue with libc6 won't be resolved until Synaptic is working and able to download and install a different version of libc6??? Or have I completely misunderstood things???

I did look at removing libc6 via synaptic, but that would also have meant removing just about everything else from my system as well so I didn't continue down that particular pathway...

Is there not something I can just type in the terminal that will sort it all out or is that just wishful thinking???

---

### Post by SSupport on 2007-01-27
Does the "Add/Remove.." under your  Applications menu work to install?
If so, Add the package Gdebi Package Installer, then download the libc6 .deb file I mentioned before.  The Gdebi will install the files for you like Synaptic does.

I have used Gdebi a few times, and love it. It will tell me if I am missing dependencies so I can go online to find them.

I'm fairly new at Ubuntu as well, so please post back if that works for you.

---

### Post by quercusrobur2002 on 2007-01-27
> **SSupport said:**
> Does the "Add/Remove.." under your  Applications menu work to install?
If so, Add the package Gdebi Package Installer, then download the libc6 .deb file I mentioned before.  The Gdebi will install the files for you like Synaptic does.

I have used Gdebi a few times, and love it. It will tell me if I am missing dependencies so I can go online to find them.

I'm fairly new at Ubuntu as well, so please post back if that works for you.

Add/remove doesn't work at the moment, but luckily I already had Gdebi installed... However when i attempted to install the file you pointed me to using Gdebi I got an error message that "a later version is already installed!"

So still stuck...

---

