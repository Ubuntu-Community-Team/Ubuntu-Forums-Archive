---
title: "VMWare Server"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2007-01-14
I am trying to install VMWARE Server using this guide.  I was all right installing right away and then decided I wanted to change a directory half way through and decided to start the install over.  Now I get this error

caippers@caippers-desktop:~/vmware$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/home/caippers/vmware/vmware-uninstall.pl.

Failure

Execution aborted.

caippers@caippers-desktop:~/vmware$ 


Any ideas how I can get this to execute?

---

### Post by smoker on 2007-01-14
something similar happened to me, uninstall vmware again, and if that doesn't work, open nautilas and delete any vmware folders you find, you should then be able to reinstall.

sorry, i can't remember off-hand which folders to delete, perhaps you can do a search, and include hidden files,

best of luck

---

### Post by gentlemanmasher on 2007-01-14
How do i uninstall it.  I didn't install it with synaptic and it isn't showing there.

---

### Post by smoker on 2007-01-14
> uninstall vmware again, and if that doesn't work, open nautilas and delete any vmware folders you find

you may be better looking for and deleting any folders you find. one of them is the reason it detects a previous installation (whether installed completely or not). i'm not to up on uninstalling stuff not from synaptic, but there are commands that can 'purge' remnants of installs, you could maybe check the man page for purge.

maybe someone with more command line experience could advise better,

---

