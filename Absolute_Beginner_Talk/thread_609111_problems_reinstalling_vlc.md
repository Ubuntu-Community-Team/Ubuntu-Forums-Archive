---
title: "problems reinstalling vlc"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by jonpon on 2007-11-10
I had a system crash, after recovering and salvaging what I could Im having problems reinstalling vlc. It didnt start so I uninstalled it and then downloaded it a new. but Im getting this 

Errors were encountered while processing:
 python-pyrex
E: Sub-process /usr/bin/dpkg returned an error code (1) 
anyone any ideas?

---

### Post by llamakc on 2007-11-10
What happens if you type:

```

sudo apt-get -f install

```

---

### Post by jonpon on 2007-11-10
I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-pycurl python-pyrex
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 42 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up python-pyrex (0.9.4.1-2ubuntu1) ...
/usr/share/doc-base/python-pyrex: cannot open control file for reading: No such file or directory
dpkg: error processing python-pyrex (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python-pyrex
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

