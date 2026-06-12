---
title: "installing gftp"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by DillPill on 2006-06-13
hi, i downloaded gftp-2.0.18.tar.gz and what do i do now? i dont get the readme can someone please post a detailed tutorial on how to install it? thanks

---

### Post by dmizer on 2006-06-13
i'm not at my ubuntu box at this moment, but i believe that gftp is in the repositories (i just confirmed that gftp is in the repositories for both breezy and dapper).  no need to download it and install it from source.  just open synaptic or use apt-get to install it.  it may not be the most recent version, but it will be alot easier than trying to install from source.

here's a good how to:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_FTP_Client_.28gFTP.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_FTP_Client_.28gFTP.29)

unless there's some specific reason you need the version you've downloaded, the gftp in the ubuntu repositories should be satisfactory.

---

### Post by aysiu on 2006-06-13
The gFTP in the repositories is the same version: 2.0.18

You need to [enable extra repositories first](http://www.psychocats.net/ubuntu/sources). Then paste these two commands into the terminal: ```
sudo aptitude update
sudo aptitude install gftp
``` After that, read this: [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

