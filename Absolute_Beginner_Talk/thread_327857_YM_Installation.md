---
title: "YM Installation"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by ragadanga63 on 2006-12-29
Tried installing Yahoo Messenger for Linux.  I have satisfied all the dependencies it asked for except for xlibs (>> 3.3.6).  Googled for it but turned up dead end after dead end.  Can anyone help me find this? Thanks.

---

### Post by ciscosurfer on 2006-12-29
> **ragadanga63 said:**
> Tried installing Yahoo Messenger for Linux.  I have satisfied all the dependencies it asked for except for xlibs (>> 3.3.6).  Googled for it but turned up dead end after dead end.  Can anyone help me find this? Thanks.How are you trying to install it?  Where did you get the files from?  On the messenger.yahoo.com site, you can download Red Hat rpms, a debian file that has been tested on Debian Woody, and a FreeBSD install file.  If you can find the source for the file, then I would recommend configuring the install via ./configure, make, sudo checkinstall...otherwise, there are many other messenger clients that can take the yahoo protocal...gaim, for example is execellent.

On Edgy, when trying to install the .deb file (remember, made for Debian Woody), I get a libssl0.9.6 dependency error...on Edgy, libssl0.9.7 and libssl0.9.8 are available for download, however, they don't seem to satisfy the dependency issue for me.  If your issue is with xlibs, then you can installing one of these to see if the dependency gets solved: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=xlibs&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=xlibs&searchon=names&subword=1&version=edgy&release=all)

In other words, the .deb file on the yahoo site will not work on Ubuntu...to get it to work, you will most likely need to satisfy many dependencies that may or may not work on Ubuntu.

---

