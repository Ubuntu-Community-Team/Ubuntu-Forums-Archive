---
title: "Apache2 parts missing"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by swieb on 2005-12-30
Hi,

During the install of my first ever server (5.10) I got most of the things I needed running. I only have one (as far as I can tell) problem left: For some reason mod-dir.so for apache2 is not present in the /usr/lib/apache2/modules directory.
The rest of the mod-xxx's are there.
Is there any way to pick up this missing file without a full reinstall of apache2 ?

Thanks in advance.

---

### Post by swieb on 2005-12-31
Hmmm... figured out that mod_dir is already in apache2.
But for some reason it doesn't add a slash when requesting an url that ends without a trailing slash like it is supposed to do.
Instead it starts looking for "server1" before returning a Page not found message.:confused: 

Anyone seen this before and knows where to look for the problem?

---

