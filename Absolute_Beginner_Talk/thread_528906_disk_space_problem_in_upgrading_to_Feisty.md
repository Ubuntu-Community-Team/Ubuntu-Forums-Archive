---
title: "disk space problem in upgrading to Feisty"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-08-18
Hi,
I would like to treat my notebook by upgrading the system on it from Edgy to  Feisty.

I did run upgrade manager and I clicked on corresponding button.
it started well but at some point I was asked to empty /var/cache/apt/achieves

the size of my /var partition is 897 M. Currently 70% of it available but the requirement is more than the whole partition. I have 3 GB space at the home partition but I dont know how to ask ubuntu to use that space instead of /var partition.
Any comment/help will highly be appreciated.

---

### Post by overdrank on 2007-08-18
> **mozkaynak said:**
> Hi,
I would like to treat my notebook by upgrading the system on it from Edgy to  Feisty.

I did run upgrade manager and I clicked on corresponding button.
it started well but at some point I was asked to empty /var/cache/apt/achieves

the size of my /var partition is 897 M. Currently 70% of it available but the requirement is more than the whole partition. I have 3 GB space at the home partition but I dont know how to ask ubuntu to use that space instead of /var partition.
Any comment/help will highly be appreciated.

Hi and my opinion is if it ain't broke don't fix it, I have tried to upgrade twice before and they failed if you want to continue to upgrade I would do a clean install. Just my thoughts :guitar:

---

### Post by randomnote1 on 2007-08-18
why do you have /var on a separate partition?  Unless you have a separate hard drive for each directory, there's really no reason to have it on another partition.  Anyway, you can try using gparted to resize the partitions, but your best bet it to do a clean install.

---

