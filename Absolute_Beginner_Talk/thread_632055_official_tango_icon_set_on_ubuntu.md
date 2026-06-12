---
title: "official tango icon set on ubuntu"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-12-05
I'd like to write a howto for tango icon set in Ubuntu, but first I need to know... how to...

Ok so, I need, according to the tango website,

    * GNU Automake 1.9.x and friends
    * ImageMagick version 5.5.7 or greater
    * pkgconfig version 0.19 or greater
    * XML::Simple Perl Module 

I need to do:
```
sudo apt-get install autoconf imagemagick
```

But how do I get  **XML::Simple Perl Module** and **pkgconfig**?

After getting all the requirements I download three tar.gz files from the tango website:

    *Icon Naming Utilities
    *Tango Icon Theme
    *Tango Icon Theme Extras

Then I extract the first icon naming utilities and type:
```
./configure
make
sudo make install
```

I need this icon-naming-utils because it allows the theme to work in the GNOME and KDE environments.
If its not installed then I get "configure: error: icon-naming-utils >= 0.8.2 is required to build and install tango-icon-theme"

On to the next folder! (All packages are extracted I presume) Do the same steps as you did with the namings utility. ./configure, make, sudo make install

and the same with the last one.


SO, thats it. **How do I get all the requirements?** I would appreciate ya'lls help :D

sv

---

### Post by mcduck on 2007-12-05
I just have to ask, what's wrong with the tango icon set you can get from  Ubuntu repositories?

---

### Post by staticvoid on 2007-12-05
ehehehehee....


woops.

new tutorial: go to synaptic and search for "tango" get the icon set for gnome and also the set for openoffice :D :blush:

---

