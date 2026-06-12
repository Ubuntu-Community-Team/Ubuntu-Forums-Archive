---
title: "recurring error - please help"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by eekfonky on 2007-05-28
this keeps happening - please help

E: Problem parsing dependency Depends

E: Error occurred while processing thekompany-support (NewVersion1)

E: Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages

E: The package lists or status file could not be parsed or opened.

E: _cache->open() failed, please report.

What is going on, none of my updates, package manager or add/remove works
It asks me to report the error but I don't know how

---

### Post by eekfonky on 2007-05-28
problem solved. sudo apt-get update wasn't working for some reason. It does now and it solved the issue

---

