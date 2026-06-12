---
title: "Installing Arabic OpenOffice"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by barrack on 2007-08-14
Hello all,

I am trying to get OpenOffice.org Arabic installed for a friend. I found the install files on the OOo website ([ftp://ftp.linux.cz/pub/localization/OpenOffice.org/OLD/2.0.2/OOo_2.0.2_LinuxIntel_install_ar_deb.tar.gz](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/OLD/2.0.2/OOo_2.0.2_LinuxIntel_install_ar_deb.tar.gz))

but what it is is a .tar.gz file fll of .deb files.

There are 28 .deb files inside and when I double click on each one like normally do, it says there are some dependency issues. the deb for core01 depends on core02, but core02 depends on core01. So I'm guessing that i'm not going about this the right way. Any help will be greatly appreciated.

Thanks.

---

### Post by capink on 2007-08-14
Put all the *.deb files in one directory and type:

```
sudo dpkg -i /path/to/the/directory/*.deb
```

---

### Post by barrack on 2007-08-14
> **capink said:**
> Put all the *.deb files in one directory and type:

```
sudo dpkg -i /path/to/the/directory/*.deb
```

Awesome, thanks so much!

---

