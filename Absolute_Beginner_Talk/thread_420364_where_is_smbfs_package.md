---
title: "where is smbfs package"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by dtzxdtzx on 2007-04-23
Hi,

While surfing the web and trying to fix my mount problem, I got some infor to install the smbfs package by:

apt-get install smbfs

Package smbfs is not available, but is referred to by another package. This may mena that the package is missing, has been obsoleted, or is only available from another source

What happens here? How to I install samba and how to I know I have the samba installed? my system is ubuntu 7.04.

Thanks

Frank

---

### Post by taurus on 2007-04-23
Which release are you running right now?  Sounds like you need to enable both universe and multiverse in /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```
and remove the # sign in front of all the lines in there with the word deb at the beginning.  Save the changes and run

```
sudo aptitude update
```
Now, see if you can get smbfs again.

---

### Post by dtzxdtzx on 2007-04-23
My version of ubuntu is 7.0.4 the newest release. After I uncomment the two line in source.list, I still got the same message claims that Package smbfs is not available.

Thanks

Frank

---

### Post by taurus on 2007-04-23
Are you sure it's not on your Feisty?  I just did a search on my Feisty using synaptic and found the package.  Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

