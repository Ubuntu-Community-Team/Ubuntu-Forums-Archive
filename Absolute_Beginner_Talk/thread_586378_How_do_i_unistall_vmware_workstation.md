---
title: "How do i unistall vmware workstation?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by blop on 2007-10-22
Hi i did a failed VM ware workstation install and i have found out there is a newer version i should of installed that does not have the same error i and other experienced.


but how do i remove the faulty install?

---

### Post by realvz on 2007-10-22
how did you install is my 1st question?

---

### Post by blop on 2007-10-22
hi thanks for sucj quick reply...

i installed using the .pl script that comes with the offical installer from website and ran through the options it give you.....so not anything dodgy

---

### Post by PartisanEntity on 2007-10-22
Open up Synaptic, look for vmware and uninstall it from there.

Then in the status tab look for orphaned packages which you can delete.

---

### Post by realvz on 2007-10-22
In the temp directory you ran the install script from, run:

Code:

sudo ./vmware-uninstall.pl

that should do the job for you...

---

### Post by blop on 2007-10-22
I tried using Synaptic before posting as it seemed to be logical to me...

but there is no entries for VM in that

Realvz i will do as you say now...cheers!

---

### Post by blop on 2007-10-22
Cheers! that worked a treat!

Just out of intrest does installing and removing apps pose a similar clutter risk as in windows....such as registry entries remaining and program folders etc?

---

### Post by realvz on 2007-10-22
i dont think registry funda applies to linux...there are just files and a few xml files..

but i guess in most cases the simple answer to your question is YES...

i can say when you install from Synaptics...the answer should be YES...

manual installs can be tricky while uninstallation..try using synaptics official repos as much as possibel...if you package is not available try using a repo that has that package...

manuall installing sucks and it can hit you very hard...i try and stay away from it..

---

