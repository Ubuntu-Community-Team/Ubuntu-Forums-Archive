---
title: "Install tar.gz package in R"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by j3lps on 2008-01-26
Hi Guys,

I've just started using Linux and am using a stats program called R. To add a tar.gz package they ask me to use:
$ R CMD INSTALL /path/to/pkg_version.tar.gz

I downloaded the file to my desktop and used the sudo command but it gave me the following:

WARNING: invalid package '/path/to/spatstat_1.12-5.tar.gz'
* Installing to library '/usr/local/lib/R/site-library'
ERROR: no packages specified

Anybody any ideas?

Thanks,
Joe

---

### Post by (((X))) on 2008-01-26
R is the compiler, right?
Try to extract .tar.gz package, cd to that directory, execute commads.

---

### Post by j3lps on 2008-01-26
Thanks

I've got it to work now.

Joe

---

