---
title: "can't install anything"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by number1pbefan on 2007-09-08
I just installed Ubuntu 7.04 64-bit version today, I got it from a friend, decided to finally try it out...and the problem is, I can install any of the files I've downloaded.  I downloaded Mozilla Thunderbird 2.0.0.6 and was attempting to create a folder in the / directory...but it wouldn't let me.

Is the / directory protected? if so...is there a way to move the partitions around without damaging my installation of Ubuntu? or is there something I'm missing...

---

### Post by chrome307 on 2007-09-08
The root directory is protected, if you want to create a folder use the HOME folder instead.

The reason for this is that the OS resides in the root folder.

---

### Post by philinux on 2007-09-08
Go to System > Admin > then click on synaptic package manager. Search for thunderbird and let it install it for you.

Its like add and remove programs in windoze.

---

### Post by number1pbefan on 2007-09-08
> **philinux said:**
> Go to System > Admin > then click on synaptic package manager. Search for thunderbird and let it install it for you.

Its like add and remove programs in windoze.

I guess I'll follow chrome307's advice...because in synaptic package manager it's only got thunderbird 1.5.0.3, and I would like thunderbird 2...

---

### Post by southernman on 2007-09-08
You only have permission to write files to these two directories by default:

/home/yourusername
/tmp

That is all... root owns everything else. Securely speaking. ;)

---

### Post by luisromangz on 2007-09-08
Well, can still install the version of Thunderbird outside your /home folder, so you get a system wide installation of the software, not only for your user. I don't know which contents has the file you downloaded from Thunderbird's site, but you can always move the folder to /opt and then create a symlink in /usr/bin.

To move the folder to /opt, you will need to use sudo

```
sudo mv /home/<your username>/<thunderbird's folder> /opt
```

To make the symlink, you will need to use sudo again, for example

```
sudo ln -s /opt/<thunderbird's folder>/<thunderbird executable file path> /usr/bin
```

---

### Post by philinux on 2007-09-08
Try following this 

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Works a treat.

---

### Post by por100pre1 on 2007-09-08
+1 for Ubuntuzilla. Very easy. :)

---

