---
title: "Compiling from source..."
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by PriceChild on 2005-10-23
Hey, trying the "/configure, make, make install combo" as i've seen it called. however, there seems to be no compiler on my ubuntu so how can i do this?

I also have a debian package of the file i'm wishing to install, please could someone help me get this going instead?

(computer has no internet so no synaptic, tis what i'm trying to get working in the first place)

---

### Post by stoffe on 2005-10-23
sudo dpkg -i package.deb

---

### Post by darth_vector on 2005-10-25
to get a C compiler

sudo apt-get install gcc

then run

./configure
make
sudo make install

you missed the "." in the "./configure"

---

### Post by Peter76 on 2005-10-25
[QUOTE=darth_vector]to get a C compiler

sudo apt-get install gcc

then run

./configure
make
sudo make install

you missed the "." in the "./configure"[/QUOTE]

You need more than only gcc;
sudo apt-get install build-essential

this will install most of the gnu compiler tools for you.
Also you'll need the header files associated with various libs on your system, wich are not instaaled by default. Look at the output of ./configure, or configure.log in the build directory, for missing files. If it says a lib is missing, install it including it's dev-files, if it says something about pk-config files missing install the dev-files.

---

