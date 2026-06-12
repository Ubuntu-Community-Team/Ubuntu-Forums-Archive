---
title: "Downloading Help"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Earltnm on 2007-01-14
New to Ubuntu.  Trying to download Campcaster Radio program (campcaster.org) and not sure which of the many files on offer I need.  I know I need the 386 / deb files, but do I need the lib as well as the other program files?  It looks like I need the lib files installed before it will let me install the others, is that correct?

Also, when trying to install the package, I'm getting the following error message:

"only one software management tool allowed to run at one time

Please close other application eg: Update Manager, aptitude or Synaptic first"

Not sure which of these other apps are running or how to close them.  Thanks.

---

### Post by ewankho on 2007-01-14
You don't have synaptic or update manager open? maybe you could try listing the processes running and then killing synaptic or update manager from there. not sure about the actual process name though...

---

### Post by Earltnm on 2007-01-14
Thanks, I'll check this out.  Any guidance on how to list the processes running?

---

### Post by Subetealabici on 2007-02-24
Hi you have to change the synaptic repositories 

In System -> Administration -> Synaptic Package Manager, select Settings -> Repositories -> Add -> Custom

Paste the following line:

deb [http://code.campware.org/ubuntu](http://code.campware.org/ubuntu) dapper main


You can then search Synaptic for "campcaster" and it will appear along with other available packages. In addition, Synaptic will also notify you when a new Campcaster version is available.

Then you will be ask to install another packages, but then don t now I m cant get it work so far:confused:

---

