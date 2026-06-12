---
title: "howto install vmare 6 beta under ubuntu 6.10 ?"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by matiz on 2006-12-31
hello, I'm just trying the ubuntu for first time, and now I want to install the vmware 6 beta in it to run windows, can any one tell me how to do it?

---

### Post by benuski on 2006-12-31
I don't know what format you would get the binaries, I would assume tar.bz2 or tar.gz, but [this]("http://monkeyblog.org/ubuntu/installing/") website can tell you have to install pretty much anything in Ubuntu.  Just scroll down to the appropriate file type that you downloaded.

---

### Post by matiz on 2006-12-31
yes I'v downloaded the tar.bz2 file, but the site

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) or 
[http://monkeyblog.org/](http://monkeyblog.org/)

I can't open it!?

---

### Post by bgoody on 2006-12-31
Right click
Extract here

Brian

---

### Post by matiz on 2007-01-01
> **bgoody said:**
> Right click
Extract here

Brian
can not understand what you saying ?

---

### Post by analyzer on 2007-01-01
I think it is not easy to install vmware. I try to make a step by step guide.
1. Download WMWare [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)
2. There is a formular to get a serial number
3. Unzip the file (gunzip <file>, tar xf <file>)
4. Execute with root permission the installation *.pl file

Requirements:
- make must be installed (sudo apt-get install make)
- A C compiler must be installed e.x. gcc
- The linux kernel headers must be installed (sudo apt-get install linux-headers-2.6.x)

Sry, for my bad english.

---

