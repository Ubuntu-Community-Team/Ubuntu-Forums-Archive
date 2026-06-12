---
title: "trouble installing 'make'"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by shasan on 2007-04-07
After many hours and one nuked Windows partition later (oops) I finally have Edgy running on my T60 laptop. Problem: I'm trying to set up ntfs support so I can read data from my windows partition (linux-ntfs.org), but when I am trying to set it all up I can't get 'make' to work. I get the error:
configure: error: no acceptable C compiler found in $PATH

I did the following:
sudo apt-get update
sudo apt-get install make

I thought that would set up make... but even after running those commands I get the same errors as above. Suggestions?

EDIT: Figured that one out by installing gcc... Now I get this error when I run the config file:
configure: error: C compiler cannot create executables

---

### Post by ComplexNumber on 2007-04-07
you need the following package:
build-essential


when you get to the stage where you have installed ntfs-3g, i will mention this....
i now have read/write access to ntfs. it requires 2 components:
-the ntfs-3g packages.
-ntfs-config. [click]("http://flomertens.free.fr/ntfs-config/") for the place to download the deb from. this can be installed by going to where you downloaded it and typing the following on the commandline:
**sudo dpkg -i <name of package>**

---

### Post by Maestro23 on 2007-04-07
> sudo aptitude install build-essential

*Edit:  Already posted.

---

### Post by Aircooledmadness on 2007-04-07
There is also some nifty ntfs tools in the repos...

sudo apt-cache search ntfs

Something in there might work for you,  saving you a scratch build.

---

### Post by ComplexNumber on 2007-04-07
yup, ntfs-3g is in the repositories.

---

### Post by shasan on 2007-04-07
Thanks! Got it installed and now it's time for reboot... let's hope I didn't nuke my windows partition again! :)

---

