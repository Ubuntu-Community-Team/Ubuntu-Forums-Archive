---
title: "Need Abiword"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by vinodis on 2006-06-21
i have no x11-dev packages installed on my ubuntu as I have no internet access. So cannot compile the Abiword. Can someone give me the .DEB file it?
I am not getting comfortable migrating to OpenOffice word.
Any help. Thanks many.

---

### Post by catlett on 2006-06-21
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fa%2Fabiword%2Fabiword-gnome_2.4.4-0ubuntu5_i386.deb&md5sum=f3d123f0a5c016770f046f99194c4988&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fa%2Fabiword%2Fabiword-gnome_2.4.4-0ubuntu5_i386.deb&md5sum=f3d123f0a5c016770f046f99194c4988&arch=i386&type=main) That is the abi-word gnome download for a intel based (i386) computer. It comes from this site that has all the Ubuntu packages availabnle for download [http://packages.ubuntu.com/](http://packages.ubuntu.com/) You still need internet connection. Hopefully you can borrow someones internet connected computer and download the deb to a disk or usb flash drive.

Hope iw helps

---

### Post by vinodis on 2006-06-21
But that does not solve the problem.  It has a lot of dependency with other packages. Manually trying to download them is not just possible. :(

---

### Post by megabyte405 on 2006-08-22
AbiWord (both the GTK-only version and and abiword-gnome, if you use the gnome desktop environment default in Ubuntu) are available through apt-get in the main repositories that are set up by default.  apt-get install abiword or apt-get install abiword-gnome will do the trick.

Thanks for using AbiWord!  Please report any problems to [http://bugzilla.abisource.com](http://bugzilla.abisource.com) 
--Ryan, AbiWord Dev and Win32 Maintainer
AbiWord Community Outreach Project: [http://cleardefinition.com/oss/abi/blog/](http://cleardefinition.com/oss/abi/blog/)

---

### Post by 3rdalbum on 2006-08-22
Go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and look at the page for Abiword. It will list what packages are required to install Abiword.

Download all those other packages, and try installing them, then install Abiword. If the packages complain about dependencies of their own, then find them on the website and download them.

---

