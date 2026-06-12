---
title: "direct path to gaim plugin folder?"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by shuke on 2006-08-20
hey guys, im new here running ubuntu 5.10. Im trying to install a plugin called gfire which is basically xfire for gaim and it requires that i extract the compressed files to the gaim plugins folder which i am unable to locate. Could somebody help me out and give me some more information about installing non ubuntu-supplied programs along with some help finding the direct path to the plugins??

---

### Post by reptyle on 2006-08-23
> **shuke said:**
> hey guys, im new here running ubuntu 5.10. Im trying to install a plugin called gfire which is basically xfire for gaim and it requires that i extract the compressed files to the gaim plugins folder which i am unable to locate. Could somebody help me out and give me some more information about installing non ubuntu-supplied programs along with some help finding the direct path to the plugins??

The install documentation is not very good on the 0.5.x releases, as they were written with compiling gaim yourself in mind.  While the INSTALL docs say that... really you just need to unpack the tarball and run the configure script.  However we require that you have the gaim-dev package installed since we need the header files it includes.

install gaim-dev,

make a temporary directory in your home directory (I usually use 'src') cd into it.

unpack the archive.

tar xzf ../path/to/gaim-xfire-0.5.9.tar.gz

cd into the gaim-fire release folder that was created.

./configure --prefix=/usr

make 

sudo make install


if you are trying to install the new 0.6.0 releases, please note these are for gaim 2.0.0beta3(.1) only.  This release will not work on a gaim 1.5 install.

I don't have a breezy machine anymore otherwise I'd create a breezy package for 0.5.9.

Dapper users can install the gaim 2.0 beta packages from here:
[http://people.ubuntu.com/~seb128/deb/](http://people.ubuntu.com/~seb128/deb/)

The new 0.6.0 releases come with prebuilt dapper packages that are specifically designed to work with the aforementioned gaim 2.0 beta3 packages.

I released 0.6.0-gaim2.0b3-r2 just now .. 8/23/2006.

---

