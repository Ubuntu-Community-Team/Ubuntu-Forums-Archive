---
title: "How to remove F-Prot"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by @nguyen on 2007-10-23
Hi All,

Could you please show me how to remove F-Prot Antivirus from Ubuntu? I just installed AVG so I don't need F-Prot and would like to uninstall it!

Thanks

---

### Post by Martje_001 on 2007-10-24
You don't need antivirus for Ubuntu! Uninstall it via Synaptic.

---

### Post by erginemr on 2007-10-24
For starters, F-Prot is installed via a custom installer package from their web site and you can use the graphical XFprot frontend to use it easily (I am also using F-Prot & XFprot) AFAIK, F-Prot Debian package does not exist in the official Ubuntu repositories.

One may download the Debian package from the following site:
[http://www.f-prot.com/download/home_user/download_fplinux.html](http://www.f-prot.com/download/home_user/download_fplinux.html)

If you used this Debian package (*.deb), to install F-Prot, then you can easily uninstall it by issuing: "sudo dpkg --remove fp-linux-ws" from the console.

Otherwise, that is, if you installed it from the source package,then

- It is quite unlikely to be installed with the usual ./configure, make, make install chain of commands, since it is a commerical application). Usually, when you have the source files, you could uninstall an application by issuing "make uninstall" from the directory where the source files are. 

- It is more likely that you installed it via a compressed archive (tar.gz) which still includes the binaries. (still from the above web address) Normally, the installer in this case should be an installation script "*.sh" and chances are that there may be an uninstaller somewhere within the package. The README or INSTALL files yonder could give you more information on how to uninstall the package.

---

### Post by hyper_ch on 2007-10-24
Are you sure you need an AV?

---

