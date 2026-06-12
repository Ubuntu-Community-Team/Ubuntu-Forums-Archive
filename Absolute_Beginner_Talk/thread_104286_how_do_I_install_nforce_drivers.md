---
title: "how do I install nforce drivers?"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by iand675@gmail.com on 2005-12-15
Well, that was pretty much my question

---

### Post by Arktis on 2005-12-15
Pretty much the same exact way you install the nvidia accelerated graphics drivers.
Go here:
[http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)
Click Platform nForce drivers, get the right one for your motherboard (nforce 1,2, & 3 are the ones with linux drivers), download and you'll have a *.run file.  Now you install that by first setting the compiler to gcc 3.4 and then running the installer with root privileges: 
```
export CC=gcc-3.4
sudo sh /path/to/nforceinstaller.run
```

Of course, you need to have already installed gcc 3.4.  You can do that from synaptec.

Once you've installed, give it a reboot.

---

