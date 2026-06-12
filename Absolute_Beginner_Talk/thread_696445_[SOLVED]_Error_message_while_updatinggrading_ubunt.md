---
title: "[SOLVED] Error message while updating/grading ubuntu"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by jpeulen on 2008-02-14
I get this error message while updating/upgrading Ubuntu 

[B]E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
[/B]

What could be the problem?

---

### Post by spiderbatdad on 2008-02-14
This looks like add/remove or synaptic was shut down somehow before finishing a requested installation.  Perhaps this will fix the problem: ```
sudo dpkg --configure -a
```

---

### Post by ashmew2 on 2008-02-14
are you using the command line to upgrade/update ? as in 

sudo apt-get update 

OR

sudo apt-get upgrade  
 ?

If you are getting the error , it means some other application is also trying to access your system files at the same time. Make sure Synaptic Package Manager is closed.

---

### Post by jpeulen on 2008-02-14
I was using the menu option in Ubuntu. I did reset the computer and everything worked normal.

---

