---
title: "problem while installing amsn"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by alket on 2007-06-14
Checking for required C library versions ... OK
Checking for X ... OK
Checking for TCL Scripting Language ... failed
-------------------------------
Error: Could not find 'TCL Scripting Language'. Try using the native package manager for Ubuntu 7.04 (apt-get) to install a package with similar name to 'tcl'. 

Error: Unable to prepare package AMSN MSN client.

**HOW CAN I FIX IT ???**

---

### Post by shae on 2007-06-14
Try opening terminal and running:
```
sudo apt-get install amsn
```

---

### Post by alket on 2007-06-14
doesn't work !!! :S

---

### Post by shae on 2007-06-14
what is the output of ```
cat /etc/apt/sources.list
```

---

### Post by alket on 2007-06-14
i dont know ... thats why im asking for ..

---

### Post by shae on 2007-06-14
Open terminal and run that command(in post 4).  Then copy the output into a post.

---

### Post by zvacet on 2007-06-14
system>administration>software source>chek all boxes>reload

```
sudo aptitude install amsn
```

---

### Post by dave-ubu on 2007-06-14
Hi

I guess you used Automatix to install AMSN ? if so - theres a known problem with it with installing TCL 

use this to fix it 

wget [http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz](http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz)
tar xvzf tls-1.5.0-linux-x86.tar.gz
sudo cp -f ~/tls1.50/* /usr/lib/tls1.50/

source: [http://www.getautomatix.com/forum/lofiversion/index.php/t1182.html](http://www.getautomatix.com/forum/lofiversion/index.php/t1182.html)

Regards

Dave

---

