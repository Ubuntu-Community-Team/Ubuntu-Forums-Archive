---
title: "How the ^&amp;*( do I install a package using sudo pdkg?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by kamaboko on 2007-03-04
Hello,

This is the deal.  I'm TRYING to get my bloody wireless working, and to do that I have to install the "build-essentials".  Well, this would be fine if I had access to a hard-line, but I don't.  So, I have to download this package from another computer w/wireless and transfer the file to the computer w/o wireless.  The file in question is build-essential_11.3.tar.gz.  I've read that to install this I need to key in the following to the terminal: sudo pdkg <file name).deb.  Fine.  But where is the deb coming from?  My file ends in gz.  Is there a hidden extension that one normally doesn't see?

Thanks,
K

---

### Post by rabid9797 on 2007-03-04
well obviously there is no .deb, you have to compile it yourself...unless the deb is in size the tarball? open it and see whats inside first.

---

### Post by taurus on 2007-03-04
Build-essential package is on the install CD so insert it into a drive, open a terminal, and run

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by christhemonkey on 2007-03-04
A tar.gz file cannot be installed with dpkg (not pdkg!).

Where did u get this .tar.gz file from?

EDIT: Forgot that build-essential was on the cd! Follow taurus's advice.

You can get the actual .deb file from here:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fb%2Fbuild-essential%2Fbuild-essential_11.3_i386.deb&md5sum=9555bbff826c8f059d00a824d6285275&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fb%2Fbuild-essential%2Fbuild-essential_11.3_i386.deb&md5sum=9555bbff826c8f059d00a824d6285275&arch=i386&type=main)

You need to get all the dependencies of it though (listed here: [http://packages.ubuntu.com/edgy/devel/build-essential](http://packages.ubuntu.com/edgy/devel/build-essential) )

and then all their dependencies and then their dependencies etc...

---

### Post by kamaboko on 2007-03-04
I've opened and have not found anything that ends in .deb.

---

### Post by toasterofirony on 2007-03-04
also, when you have a .deb the command is "dpkg" not "pdkg" ;)

But sure, it sounds like you have a tarball not a .deb

---

### Post by kamaboko on 2007-03-04
> **christhemonkey said:**
> A tar.gz file cannot be installed with dpkg (not pdkg!).

Where did u get this .tar.gz file from?

EDIT: Forgot that build-essential was on the cd! Follow taurus's advice.

You can get the actual .deb file from here:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fb%2Fbuild-essential%2Fbuild-essential_11.3_i386.deb&md5sum=9555bbff826c8f059d00a824d6285275&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fb%2Fbuild-essential%2Fbuild-essential_11.3_i386.deb&md5sum=9555bbff826c8f059d00a824d6285275&arch=i386&type=main)

You need to get all the dependencies of it though (listed here: [http://packages.ubuntu.com/edgy/devel/build-essential](http://packages.ubuntu.com/edgy/devel/build-essential) )

and then all their dependencies and then their dependencies etc...

I got the tar file from your second link.  OK...now i've got the build-essentials installed, so what do I do with these dependencies or tar file?

---

