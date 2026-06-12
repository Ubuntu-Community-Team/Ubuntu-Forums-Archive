---
title: "Installing App's on Linux ?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by id3379 on 2008-01-09
I notice whenever i download a folder its in a .tar.gz compressed folder, i uncompress it and open the folder and well i'm really used to the basic windows, and i'm not sure where the install file is, there are some files labeled install but they are just text files, and there is some configure file i opened but they just made more file and i have no idea on how to install it :( here is what the text file says which confuses me alot.

"1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

"



Do you have to compile your programs on linux or something ? they don't come pre compiled like a normal program ? Do you have to install things through Terminal ? Whats the deal ? I tryed searching but i didn't really find anything this basic so i must be pretty retarded.

---

### Post by taurus on 2008-01-09
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by OldGrey on 2008-01-09
Most applications you will need can be installed using the Add/Remove facility, or Synaptic (system /administration). Check out this for basic advice:

[https://help.ubuntu.com/7.10/add-applications/C/index.html](https://help.ubuntu.com/7.10/add-applications/C/index.html)

---

### Post by RavUn on 2008-01-09
> **taurus said:**
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

particularly
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by aeiah on 2008-01-09
that link is a great one. in summary, its easiest to use synaptic, then if not, use the .deb file if available, or thirdly go for compiling (from a tar.gz). most projects release .deb ubuntu installation files. these are very similar to windows .exe setup files in terms of usage.

a good place to look for them is [www.getdeb.net](www.getdeb.net), or google for the project's webpage

---

