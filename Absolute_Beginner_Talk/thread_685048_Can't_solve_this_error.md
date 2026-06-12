---
title: "Can't solve this error"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Azureglows on 2008-02-01
I first hit this error when I was trying to install eclipse, ended up just downloading eclipse from the site and it works, however I've run into again and I need to figure out what's causing it.  Here is the error
```
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

Now I'm getting this error while I'm trying to install ndiswrapper via Synaptic Package Manager.  I've done a few steps to try and get this error to stop while I was trying to install eclipse,  I downloaded te jdk-6-doc.zip and extracted the folder, then changed the owner to root.root, and placed a copy in the /tmp file.  Commands i used were
```
sudo jar xvf jdk-6-doc.zip
sudo chown root.root docs
sudo mv docs /tmp
```

Any help to get this error fixed would be greatful, I'm trying to get my wireless card working and can't get passed the beginning step :(

---

### Post by dcstar on 2008-02-02
> **Azureglows said:**
> 
.........
Any help to get this error fixed would be greatful, I'm trying to get my wireless card working and can't get passed the beginning step :(

Why do you think a Java Documentation package will help you get a wireless card working?

---

