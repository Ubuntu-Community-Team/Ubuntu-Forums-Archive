---
title: "Printing via a Linksys Print Server"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Humph on 2006-09-30
Please forgive my extreme noobishness. I've only been using Ubuntu for a few hours!

I'm trying to install my Brother HL-1030 printer, which is attached to a Linksys PPSX1 Print Server.

When I try to print a test page nothing happens, and the status on the General tab of the printer's Properties shows:

Printing: Unable to connect to CIFS host, will retry in 60 seconds...

Would someone be kind enough to point me in the direction of a solution?

---

### Post by docshawnc on 2006-09-30
Hi - I'm not sure if this will be of help, but I was able to install my Brother network based printer/scanner/fax machine using these directions:
[http://www.linuxquestions.org/hcl/showproduct.php/product/3009/sort/2/cat/all/page/1/si/All-in-one](http://www.linuxquestions.org/hcl/showproduct.php/product/3009/sort/2/cat/all/page/1/si/All-in-one)

Previously, I had a similar error message to the one you're seeing

---

### Post by Humph on 2006-09-30
Thanks for your reply docshawnc.

I tried installing the lpr and cups driver files. The cups driver installed fine, but the lpr one complained a lot:

Preparing to replace hl1030lpr 1.1.2-1 (using ./hl1030lpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl1030lpr ...
/var/lib/dpkg/info/hl1030lpr.postrm: line 3: /etc/init.d/lpd: No such file or di rectory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing ./hl1030lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 ./hl1030lpr-1.1.2-1.i386.deb

I've no idea if this is anything to worry about or not.

But still I couldn't print. In the end I detached the printer from the Print Server and plugged it into the back of my computer. When attached directly to lpt1 it prints fine. So my guess is the problem lies with getting the correct port settings for the Linksys Print Server...

---

