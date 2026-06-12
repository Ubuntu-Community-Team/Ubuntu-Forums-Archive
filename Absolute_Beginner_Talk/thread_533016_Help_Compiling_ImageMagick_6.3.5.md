---
title: "Help Compiling ImageMagick 6.3.5"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by nathanziarek on 2007-08-23
I'd like to use IM 6.3.5, as the version using **apt-get** is pretty old and doesn't work well with PDFs.

I've downloaded the Source and compiled it, and IM will work for its internal graphic format (.mpc) but it will not work for JPG, PNG, etc.

Does anyone have any advice for getting the entire suite to work?

Thanks,

Nate

---

### Post by LarsBT on 2007-08-31
Well I had the same problem. After some digging I found this web-page [http://www.ducea.com/2006/12/21/install-imagemagick-557-on-debian/]("http://www.ducea.com/2006/12/21/install-imagemagick-557-on-debian/")

He wanted to compile and  *older* version. However, I found it to work fine for me.

Basically, Imagemagick doesn't necessarily *need* all libraries to compile, but jpeg and png sure is nice to have.

You have to pretend to compile the default ubuntu package and apt-get the build-dependencies for the current build (wich is 6.2 or something). So 

```
apt-get build-dep imagemagick
```

Then try and ./configure and see the output to have the support for the image formats you need.  I haven't looked at the PDF-support perhaps you need a special library for that in addition.

 Then make and make install and it should work.

Regards
Lars

---

