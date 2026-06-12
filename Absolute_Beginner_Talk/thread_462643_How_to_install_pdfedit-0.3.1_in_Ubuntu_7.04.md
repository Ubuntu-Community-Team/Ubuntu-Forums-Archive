---
title: "How to install pdfedit-0.3.1 in Ubuntu 7.04?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by chunchengch on 2007-06-02
I downloaded and extracted pdfedit-0.3.1.tar.bz2, but when I configure it with command **./configure**, an error occurred, the package **qt3-dev-tools** is already installed, while I don't know how to set the **QTDIR environment variable**. anyone can help? thanks.

/Desktop/pdfedit-0.3.1$ ./configure
configure: error: QTDIR environment variable must be set
/Desktop/pdfedit-0.3.1$

---

### Post by testube_babies on 2007-06-02
There is a 0.3.0 version at getdeb.net:
[http://www.getdeb.net/app.php?name=PDF+Editor](http://www.getdeb.net/app.php?name=PDF+Editor)

If you really MUST have the 0.3.1 version, then someone else will have to help you because I know nothing about qt :)

---

### Post by chunchengch on 2007-06-02
testube_babies,

I am a Linux newbie, and I don't know how to install **pdfedit_0.3.0-0~getdeb1_i386.deb**?

---

### Post by testube_babies on 2007-06-02
double click!  :D

or, in a terminal:
sudo dpkg -i pdfedit_0.3.0-0~getdeb1_i386.deb

After installing, you might have to do this in the terminal, also (to fix dependency issues):
sudo apt-get install -f

---

### Post by chunchengch on 2007-06-02
testube_babies,

Thanks a lot, it works!:D

---

### Post by chunchengch on 2007-06-02
testube_babies,

I can not open the file stored in NTFS media.

[ATTACH]34187[/ATTACH]

---

### Post by testube_babies on 2007-06-03
Have you tried copying the file from your NTFS disk to your linux disk?  The problem you are encountering might have something to do with the fact that Ubuntu does not natively support writing to NTFS.

If you find you need NTFS read/write support, there is a program in the Feisty repositories that can enable it for you:

```
sudo apt-get install ntfs-config
gksu ntfs-config
```

---

### Post by chunchengch on 2007-06-04
I had installed packages ntfs-3g and ntfs-config just after I installed Ubuntu 7.04, so I can always read and write files from NTFS disk without any problem since then, however, if I copy the pdf file to the desktop and then open it with PDF Editor, it works fine, so what is the exact problem you think?

---

