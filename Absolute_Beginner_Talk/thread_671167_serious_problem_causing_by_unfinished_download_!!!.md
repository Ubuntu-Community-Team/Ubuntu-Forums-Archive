---
title: "serious problem causing by unfinished download !!!"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by ariel bebbe on 2008-01-18
[B][SIZE="4"] i have started to download jdk-6-doc.zip then i interrupt the download because the file is to big . Now i can't installanything , even if i try to install VLc i receive this message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ariel@ariel-desktop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.


what to do to completely remove jdk-6-doc.zip
[Press RETURN to try again, 'no' + RETURN to abort] 
[/SIZE][/B]

---

### Post by stoodleysnow on 2008-01-18
Do as it says. Go to that java website, download the files you need. Go to the terminal,
```
su
```, enter password and then ```
cp jdkfile1 jdkfile2 /tmp
```

Once you have installed jdk, you can ```
sudo dpkg --configure -a
``` again.

---

