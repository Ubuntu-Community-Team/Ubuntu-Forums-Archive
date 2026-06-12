---
title: "Compiling Clam Antivirus"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-04-25
I was compiling Clam Antivirus from source and after I ran ./configure, this line came out at the end of all of the many lines of output.

configure: error: Please install zlib and zlib-devel packages

I then used 

sudo apt-get install zlib zlib-devel

It put out

E: Couldn't find package zlib

Then these commands wouldn't work:

make
su
make install
exit

What am I not doing / doing wrong?

---

### Post by renzokuken on 2007-04-25
well you had the right idea but are probably using the wrong package names for zlib.

try the following instead

```
sudo apt-get install zlibg zlibg-dev build-essential
```

and then try compiling clamav again........also, in ubuntu the following commands should be used to compile from source

```

./configure
make
sudo make install

```

---

