---
title: "Problems with updates"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by L.boothman on 2006-03-26
Hi Guys,


Im having a few problems, with lovely Ubuntu.

Ther first being, when ever i try and run and install the updates it downloads them then try's to install them but then throws up this error "

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"

And then it doesnt install anything??

Also im having trouble installing .deb programs, it just says not compatible but i thought Ubuntu was a Debain platform Linux?


Any help will be awesome

Cheers guys, Peace Out

---

### Post by Xian on 2006-03-26
[QUOTE=L.boothman]HW: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"

And then it doesnt install anything??[/quote]

From a terminal:

```
$ sudo gpg --keyserver subkeys.pgp.net --recv 40976EAF437D05B5
$ sudo gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
```


[QUOTE=L.boothman]Also im having trouble installing .deb programs, it just says not compatible but i thought Ubuntu was a Debain platform Linux?[/QUOTE]

Ubuntu is derived from Debian but not always package compatible.

---

### Post by Xian on 2006-03-26
* double post *

---

### Post by L.boothman on 2006-03-27
I type that all in and it says "No valid OpenPGP data found"?

---

