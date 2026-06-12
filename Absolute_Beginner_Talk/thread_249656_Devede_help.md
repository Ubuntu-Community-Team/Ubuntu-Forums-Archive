---
title: "Devede help"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by HdK on 2006-09-02
How do I install Devede, I downloaded, the is a file inside the zip called install.sh I tried double clicking and it did nothing . What command do I need to use to install?

---

### Post by taurus on 2006-09-02
Open a terminal, Applications -> Accessories -> Terminal, and change directory to where you have downloaded devede22.tar.bz2 (or whatever it's called).  Then install it...

```

cd ~/Desktop/devede
sudo ./install.sh

```

---

### Post by HdK on 2006-09-02
I did what us said I downloaded to desktop, I extracted to desktop, It created a folder named devede23, I pulled up terminal gave command cd /home/hdk/Desktop/devede23, then I used code sudo ./install.sh and nuthing happens , IM stuck help

---

### Post by HdK on 2006-09-02
are there any good dvd authoring tools in the repository that I can download and install from there

---

### Post by taurus on 2006-09-02
> **HdK said:**
> I did what us said I downloaded to desktop, I extracted to desktop, It created a folder named devede23, I pulled up terminal gave command cd /home/hdk/Desktop/devede23, then I used code sudo ./install.sh and nuthing happens , IM stuck help
You are not supposed to get anything except your prompt back!  See if you can run it from a command line with

```
devede
```

---

