---
title: "Unable to Upgrade to 7.04"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2007-05-24
When I run the update manager to update from 6.10 to 7.04 the process aborts with the following notification:

> Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/source/Sources.gz) 404 Not Found

If it makes a difference I also have Synaptic and EasyUbuntu installed on this system.

What could be the problem and how do I upgrade this system?

Thanks in advance!

---

### Post by dbbolton on 2007-05-24
you need to disable 3rd party repositories first.

---

### Post by chaplanger on 2007-05-24
How do I disable the third party repositories? (step-by-step) please.

---

### Post by dbbolton on 2007-05-24
go to System > Administration > Software Sources

then click the "Third-Party Software" tab

then remove those entries.

---

### Post by chaplanger on 2007-05-24
Yup -- that would have been easier.  

My route was a bit more complicated: I went to Terminal and 
> 
sudo gedit /etc/apt/sources.list

Then I remarked out (#) the lines listing the problem repositories and saved my changes.

After this the update worked flawlessly.

---

