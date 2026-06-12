---
title: "Help, My system cannot update"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by honor on 2008-01-11
Everytime I run update, the following errors occured:

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Anyone can help me? thanks

---

### Post by blueridgedog on 2008-01-11
I searched the web and found:

"I commented out the offending repo (including the src repo). Made synaptic update. Then uncommented the repos. made synaptic update again. As luck would have it, then no error!. Mysterious."

So, perhaps you can edit /etc/apt/sources.list

gksudo gedit /etc/apt/sources.list

and comment out those lines, try updating, then repeat to uncomment, then try again.  Also you can try taking out the us and just using archive.ubuntu.com.

---

