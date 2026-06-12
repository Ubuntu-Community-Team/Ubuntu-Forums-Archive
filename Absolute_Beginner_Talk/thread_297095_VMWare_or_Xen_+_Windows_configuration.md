---
title: "VMWare or Xen + Windows configuration?"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by drx0 on 2006-11-10
We want to run Linux for file and print and Windows for SQL Server on a single server via Xen or VMWare and wanted to poll the audience (RAID 0 for Linux host OS & Windows 2003 guest, RAID 5 or 10 for data drives):

(1) Xen or VMWare Server?

---

### Post by watson540 on 2006-11-10
It All depends on the processor you have in your machine, If it is newer and has the 'VT' instruction set (i think thats the one, the one that allows windows virtualization) But you have to have the certain processor to do it. As for linux, xen would probably also be faster but it does not require the special processor with instruction sets to run.

---

