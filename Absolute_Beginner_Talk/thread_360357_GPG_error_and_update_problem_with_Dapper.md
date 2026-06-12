---
title: "GPG error and update problem with Dapper"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by Cham on 2007-02-13
Hi,

I'm sure this has been posted elsewhere but I'm still new (VERY new) to ubuntu and can not really make sense of most of the posts.

I've just installed Ubuntu 6.06 (dapper) on my Dell 600m.  When I try to update my software packages (i've added access to the Universe and Multiverse repositories with no problem) - I get the following error:

**W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>**

All of the initial downloads worked except for 3 updates (linux-386, linux-restricted-modules-386, linux-restricted-modules-common).  I got the following error:

[B]W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-386_2.6.15.25_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-386_2.6.15.25_i386.deb)
  404 Not Found[/B]

Thanks!

---

### Post by jpeddicord on 2007-02-13
From the Update Manager (System > Administration > Update Manager) click the Check button again, and it should automatically refresh the list of packages that need updated, and it probably will fix your errors too. :)

Jacob

---

### Post by Chamith on 2007-02-13
Hi -

nope.. reloading doesn't help.  It still hangs on those three packages with the same GPG / 404 errors.

---

