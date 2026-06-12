---
title: "bah... starting over"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-05-28
Hey guys... i think the main problem i have with my java may be because the original download may have been corrupted.


how do I uninstall all java components from my machine?

---

### Post by eapache on 2007-05-28
It depends how you installed it originally. In add/remove programs, try installing Ubuntu Restricted Extras.

---

### Post by Tyke91 on 2007-05-28
I can't install ubuntu restricted extras because every time I install something I get this error message

```

E: sun-java6-doc: subprocess post-installation script returned error exit status 1
E: msttcorefonts: subprocess post-installation script killed by signal (Interrupt)
E: ubuntu-restricted-extras: dependency problems - leaving unconfigured

```


i also get


```

Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

```


I'm seriously considering just formatting the drive and reinstalling ubuntu

---

### Post by eapache on 2007-05-28
Try the following in terminal:

```
sudo apt-get remove sun-java5-bin sun-java5-jre sun-java5-plugin
sudo apt-get reinstall sun-java6-bin sun-java6-jre sun-java6-plugin
```

The first one is to remove any older versions, if it says it's not installed it doesn't really matter. If the second one says that it isn't installed either, redo it but replace 'reinstall' with 'install'.

---

### Post by MSBF on 2008-07-14
> **eapache said:**
> Try the following in terminal:

```
sudo apt-get remove sun-java5-bin sun-java5-jre sun-java5-plugin
sudo apt-get reinstall sun-java6-bin sun-java6-jre sun-java6-plugin
```

The first one is to remove any older versions, if it says it's not installed it doesn't really matter. If the second one says that it isn't installed either, redo it but replace 'reinstall' with 'install'.

So i gave this a shot and nada. Kept getting the same error and the following:-
Errors were encountered while processing:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any other ideas? I'm on Gutsy, plus its asking me to install 751 programs in the normal update.

---------------------------------

Never mind, just had to uninstall it manually. But vmware is still being dodgy, will pretend to open, then after two seconds dissapears.......

---

