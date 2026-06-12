---
title: "uninstalling Adobe Acrobat Reader"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2008-04-03
I am currently running the version 8 of Adobe Acrobat Reader for Linux.

How do I **UN**INSTALL the version 8, so I can then try installing version 7 ?

I am having a printing problem and I think it has to be related to the Adobe Acrobat Reader that the Virginia Department of Taxation is running their tax forms thru (PDF).  I want to try version 7 of Adobe to see if I get the same problem that I am having with 8 installed.

Thanks.

---

### Post by warp99 on 2008-04-03
If you install the reader through the medibuntu.org repository then:

```
sudo apt-get remove acroread
```

if you installed it direct from Adobe then use the uninstall script:

```
cd <name_of_install_directory/Adobe/Reader8/bin && sudo ./UNINSTALL

```

---

### Post by wpshooter on 2008-04-03
> **warp99 said:**
> If you install the reader through the medibuntu.org repository then:

```
sudo apt-get remove acroread
```

if you installed it direct from Adobe then use the uninstall script:

```
cd <name_of_install_directory/Adobe/Reader8/bin && sudo ./UNINSTALL

```


Thanks.  I got the version 8 uninstalled and then installed version 7 instead but unfortunately that did not solve my printing problem.

---

### Post by amyst on 2008-05-17
Hi wpshooter, can you post a link where I can find and download adobe reader 7? I've been looking for it.

---

### Post by wpshooter on 2008-05-18
> **amyst said:**
> Hi wpshooter, can you post a link where I can find and download adobe reader 7? I've been looking for it.

It is on the main Adobe download page:

[http://www.adobe.com/products/acrobat/readstep2_allversions.html]("http://www.adobe.com/products/acrobat/readstep2_allversions.html")

Just change the button choice from version 8 to version 7.

---

### Post by Dale Sexton on 2008-06-30
> **warp99 said:**
> If you install the reader through the medibuntu.org repository then:

```
sudo apt-get remove acroread
```

Did not work for me. says acroread not installed.

---

