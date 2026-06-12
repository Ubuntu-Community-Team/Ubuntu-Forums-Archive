---
title: "How would use a .tar.gz file in Ubuntu?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by ChristDude on 2007-11-01
I've seen a few of those files, what are they exactly, and how would you use them? Thanks :D.

---

### Post by Whiffle on 2007-11-01
Its similar to a zip file in windows, compressed data.  Often times source code is packaged in them.

---

### Post by defrex on 2007-11-01
.tar.gz it a form of compression, similar to .zip or .rar. Which means it could be a number of things. If it's a downloaded program, then it's probably source code. But tar.gz is used a lot in Linux. GTK Themes, for example.

---

### Post by Dapilot1 on 2007-11-01
This is a helpful site for installing stuff.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by kevdog on 2007-11-01
Unizp at the command line like
tar zvxf filename.tar.gz

---

### Post by Maestro23 on 2007-11-01
> **ChristDude said:**
> I've seen a few of those files, what are they exactly, and how would you use them? Thanks :D.

Installing Software:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

When you see a .tar.gz file, it is usually the source code for a program or a driver for a hardware device.  Compiling from source can be tricky and frustrating for a person new to linux.  Not advised unless you really have no other choice.

*More info can be found on he tar command, by opening a terminal and:

> man tar

---

### Post by ChristDude on 2007-11-02
Say I was installing something such as Gnomad2 to sync my Creative Zen with Ubuntu. Its download comes as a .tar.gz file. How would I go along using that? Thanks.

---

### Post by ajmorris on 2007-11-02
In the tar.gz file, there will also be a readme file, however, most source compiles go like this:

1) ./configure
2) make
3) make install

Read the readme file also to make sure there are no application specific options there. Also, be warned, removing applications compiled manually can be a little tricky.

---

### Post by Maestro23 on 2007-11-02
> **ajmorris said:**
> In the tar.gz file, there will also be a readme file, however, most source compiles go like this:

1) ./configure
2) make
3) make install

**Read the readme file also to make sure there are no application specific options there. Also, be warned, removing applications compiled manually can be a little tricky**.

Very good advice.  There will be a README/IINSTALL doc in the extracted folder containing instructions, program dependencies, etc...

---

### Post by ChristDude on 2007-11-02
OK, the README will help me, thanks for letting me know it was included :D.

---

### Post by justsomedude on 2007-11-02
Why do you want to compile Gnomad2? There's no need to compile it, it's included in the repositories (universe):

```
sudo apt-get install gnomad2
```

One of the great things about Linux is, a distribution like Ubuntu comes with a package manager that does almost everything for you, you don't have to go on the web and search for files, download, extract and then install them, apt-get will do everything for you. It will install the required dependencies and so on...

:)

---

