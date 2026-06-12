---
title: "Why can't I back up MySQL databases in Ubuntu?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2008-01-16
I tried to back up two databases, with two different hosts, with MySQL Administrator, on Ubuntu 7.10.  Both times I was told I had a SQL error.  Yet I can perform this function perfectly on Windows.  Any idea what the problem might be?  Thanks.

---

### Post by frankos44 on 2008-01-17
Try using the terminal: 

$ mysql -u root -pPASSWORD -x -e -B DATABASENAME > DATABASENAME.sql

If you prefer GUI, I highly recommend the latest version of Navicat for Linux. It offers features including:

. Port 22 tunneling
. Data conversion
. Data transfer from host to host
. Backup

Does this help?

---

### Post by ukripper on 2008-02-27
> **getmeoutofhere said:**
> I tried to back up two databases, with two different hosts, with MySQL Administrator, on Ubuntu 7.10.  Both times I was told I had a SQL error.  Yet I can perform this function perfectly on Windows.  Any idea what the problem might be?  Thanks.

What SQL error you are getting?

---

