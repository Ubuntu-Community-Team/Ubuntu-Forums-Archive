---
title: "Need Help C compiler"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by e30ernest on 2007-05-20
Hello!  I'm trying to install a few tarballs (Vive for example) but I am always getting an error message whenever I get to the "configure" command part.  When I enter:

```
./configure
```

I get the following:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
**checking for C compiler default output file name... configure: error: C compiler cannot create executables**

```

After that, I can't use the "make" command because it says:

```
make: *** No targets specified and no makefile found.  Stop.
```

I haven't been able to install any of the programs that need to be compiled using the make and make install commands because of this.  Am i missing something here?  Thanks!

---

### Post by Bachstelze on 2007-05-20
```
sudo apt-get install build-essential
```

---

### Post by e30ernest on 2007-05-20
Thanks that solved it! :)

---

### Post by zero-9376 on 2007-05-20
you might want to look at the app checkinstall, it will create an installable deb which is recognised by the systems (you will see it in synaptic). excellent peice of software for anyone who does source installs, you can even use the debs on other systems which saves time and downloads.

Personally I think checkinstall should be mentioned in any compile from source howto.

---

### Post by Bachstelze on 2007-05-20
While I agree that checkinstall is a useful thing, I don't think it should be mentioned everywhere. First, because not everyone thinks the same and then because it is absolutely not *required* for anything to work and the point of a howto is to make things work. No more, no less.

---

### Post by zero-9376 on 2007-06-13
While I agree that it is not essential and of course that not everyone thinks the same way, for new users the convinience of using synaptic/apt  makes the package worth a small mention even just a link to a site that tells the user about checkinstall.

Having a centralised way of managing software is one of the best things about using Linux. With ubuntu/debian the range of packages available from the repos means I rarely have to look outside but when I do having the package available for maintenance through that system is great.

This is of course just my opinion, I think new users should know about it, thats all.

---

