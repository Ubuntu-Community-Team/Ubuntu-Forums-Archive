---
title: "Can't install PHP - xml2-config not present"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by smith.norton on 2007-03-21
I am trying to install PHP on Ubuntu 6.06 using the following command:-

```
./configure --with-apxs2=/usr/local/apache2/bin/apxs
```

But, I get this error:-

```
configure: error: xml2-config not found. Please check your libxml2 installation.
```

After a little debugging I found that, the configure script tries to find the file xml2-config in the following locations:-

```
/usr/lib/bin/xml2-config
/usr/local/bin/xml2-config
/usr/bin/xml2-config
```

In my system, this file is not present anywhere in the hard disk. But I have the latest libxml2. Proof:-

```
smith@everest:~/kitchen/php-5.2.1$ sudo apt-get install libxml2
Reading package lists... Done
Building dependency tree... Done
libxml2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Reading package lists... Done
Building dependency tree... Done
libxml2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

So, how can I correct this error and continue with my PHP installation?

---

### Post by smith.norton on 2007-03-22
Please help!

---

### Post by nihil on 2007-03-26
Try:
```
 sudo apt-get install libxml2-dev
```

---

