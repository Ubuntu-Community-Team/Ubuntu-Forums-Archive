---
title: "[SOLVED] Can't see info at website"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by MountainX on 2008-01-31
I'm trying to view the graph (Death and Taxes 2008 Poster) at [http://www.thebudgetgraph.com/site/index.php?main_page=product_info&products_id=1](http://www.thebudgetgraph.com/site/index.php?main_page=product_info&products_id=1)

I have flash install (and YouTube videos play correctly). Any idea what the issue with the above site could be? And how would I determine this on my own? Thanks.

---

### Post by jan quark on 2008-01-31
perhaps you need to install java

try this code
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by MountainX on 2008-01-31
thank you. Is it better to use Synaptics PM to install this? I see java6-bin and sun-java6-jre listed in Synaptics, but I don't see sun-java6-plugin listed.


sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

---

### Post by jan quark on 2008-01-31
puuh
i dunno just copy and paste this into the terminal hit enter and thats it :)

---

### Post by shad0w_walker on 2008-01-31
It shouldn't really make a difference which tool you use to install the packages, they all use the same back-end at the end of the day. Just use whatever you feel comfortable with.

---

### Post by MountainX on 2008-02-03
This solved it for me:
[http://ubuntuforums.org/showpost.php?p=4253178&postcount=760](http://ubuntuforums.org/showpost.php?p=4253178&postcount=760)

It was flash-related.

---

