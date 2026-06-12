---
title: "upgrade problems from 6.06 to 6.10"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by lavikl on 2007-05-08
Hi there
I'm trying to upgrade my 6.06 version to 6.10 by using :

> gksu "update-manager -c" 

after a few seconds i get these messsages :

> Failed to fetch [http://ubuntu.moshen.de/dists/dapper/Release](http://ubuntu.moshen.de/dists/dapper/Release) Unable to find expected entry  flash/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/main/binary-amd64/Packages.bz2](http://www.getautomatix.com/apt/dists/dapper/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/main/binary-amd64/Packages.bz2](http://www.getautomatix.com/apt/dists/dapper/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)


any ideas ?
I'm using AMD 64 bit CPU

Thanks

---

### Post by NeoLithium on 2007-05-08
Remove the automatixinstalled repost or comment thenm out from your /etc/apt/sources.list
Run sudo apt-get update
and then try again.

---

### Post by H.E. Pennypacker on 2007-05-08
Hmm, it looks like there is a problem with several repositories you have enabled.  I encourage you to use the graphical upgrade method, instead of using the terminal.   Please see this upgrade page:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Edit:  Please do not, as some recommend, use any terminal directions, because they will unnecessarily confuse you.  Stick with GUI.

---

