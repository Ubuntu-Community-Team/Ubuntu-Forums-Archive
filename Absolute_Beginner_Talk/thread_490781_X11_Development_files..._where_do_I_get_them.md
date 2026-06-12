---
title: "X11 Development files... where do I get them?"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by dwhitney67 on 2007-07-02
Hi,

I would like to build an application that requires X11 header files.  Where can I get these files?

I've tried the following already to get the libraries:

```
sudo apt-get install libx11-dev
```

When I tried the following (for the headers), I get an error indicating that the package cannot be found:

```
sudo apt-get install x11-dev
```

Is it perhaps because there is a repo entry in my /etc/apt/sources.list that is missing?

---

### Post by reset3x on 2007-07-02
[http://www.x.org/wiki/](http://www.x.org/wiki/)

---

### Post by enopepsoo on 2007-07-02
make sure that you have the source repos enabled...:KS

---

### Post by Seisen on 2007-07-02
> **dwhitney67 said:**
> Hi,

I would like to build an application that requires X11 header files.  Where can I get these files?

I've tried the following already to get the libraries:

```
sudo apt-get install libx11-dev
```

When I tried the following (for the headers), I get an error indicating that the package cannot be found:

```
sudo apt-get install x11-dev
```

Is it perhaps because there is a repo entry in my /etc/apt/sources.list that is missing?

The first way you tried is correct, you might already have them installed.

---

### Post by dwhitney67 on 2007-07-02
> **enopepsoo said:**
> make sure that you have the source repos enabled...:KS

What are the source repos?  Should I be looking for something in particular within my existing /etc/apt/sources.list file?  If so, there are only two entries commented out.  When I un-comment them, I am still unable to locate the x11-dev package with apt-get.

With Fedora I would be done with the whole enchilada with a simple yum install xorg-x11.  Why is Ubuntu so difficult (i.e. why are there two or more packages to install)?


Seisen - Trust me, the header files I need are not in the /usr/include/X11/extensions directory.  If they were, I would not have created the OP.

Reset3x- If I wanted to install the development packages manually that could easily be done.  I was hoping for a more elegant solution involving the Ubuntu package manager.

---

### Post by dwhitney67 on 2007-07-02
I found the solution the old-fashioned way... I googled for it.

Here's the last piece of the puzzle:

```
sudo apt-get install xlibs-dev
```

---

### Post by evernight on 2007-12-15
Just in case somebody comes back to this via Google, xlibs-dev is now obsolete.  The command you want is:

```
sudo apt-get install xorg-dev

```

Works like a charm....

---

