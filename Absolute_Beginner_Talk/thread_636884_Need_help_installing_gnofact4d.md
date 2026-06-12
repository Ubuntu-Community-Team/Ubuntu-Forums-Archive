---
title: "Need help installing gnofact4d"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2007-12-10
Hi.  I'm trying to install this fractal program (to make my own desktop backgrounds) and I am having some trouble.  

The file I downloaded is here: [http://gnofract4d.wiki.sourceforge.net/Installation](http://gnofract4d.wiki.sourceforge.net/Installation).  I used archive manager to pull out the folder from the tar file.  Then, I cd'd to the desktop (because thats where the folder is, and typed:
```
./setup.py build
```

I keep getting a  "error: command 'gcc' failed with exit status 1"  Their FAQ page says if I get that error, then **A:You have the C compiler installed, but not the C++ compiler. You need to install the g++ (sometimes called gcc-c++) package, which is required to build C++ programs.**

I installed g++ from synaptic, and I also got the build-essential and still I'm getting the same error.  Any ideas?

Here's the code I used to get the build essential library.
```

sudo apt-get install build-essential

```

---

### Post by meborc on 2007-12-10
if you look a bit down on that page you will see that they have an alternative method to install this on ubuntu... you have to use alien to install the rpm package... i think you will have better luck with that then to try to build it yourself :) it seems like this project is not very polished yet

install alien (sudo apt-get install alien), then > 1) Download the RPM file for your architecture (i386 or x86_64)
2) Convert it to a Debian package: sudo alien gnofract4d-python25-3.5-.rpm
3) Install it: sudo dpkg -i gnofract4d-python25-3.5--2.deb

---

### Post by spiderbatdad on 2007-12-10
probably need build-essential from synaptic package manager as well

---

### Post by spiderbatdad on 2007-12-10
opps sorry. not paying attention

---

### Post by 3rr0r on 2007-12-10
let me try that.  i tried the command with alien but it said unrecognized.  I didn't know alien was something i had to install.

---

### Post by meborc on 2007-12-10
alien is a program that lets you change .rpm packages to .deb packages (red hat packages to debian ones)

pretty useful at times, all though nowdays you can get most programs in debs as well as rpms

---

### Post by 3rr0r on 2007-12-10
Thanks, that worked great!

---

### Post by catenary on 2008-01-13
By the way a native Ubuntu package for Gnofract 4D is now available.

---

