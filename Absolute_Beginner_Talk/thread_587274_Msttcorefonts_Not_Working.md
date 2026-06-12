---
title: "Msttcorefonts Not Working"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by khan Singh on 2007-10-22
I install the Msttcorefonts using the Synaptic Package manager, it downloads normally, but when it goes to install them, I get this message:


Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use the fonts provided by this package under the X Window System, you must configure it to use defoma fonts.

The easiest way to do so is to use the x-ttcidfont-conf package. For more information, install the x-ttcidfont-conf package and consult its documentation under /usr/share/doc/x-ttcidfont-conf.

For uses of msttcorefonts not related to the X Window System (e.g. printing) this is not required.


I reboot, and the Msttcorefonts  still are not working.  I have reinstalled it several times and I get the same message everything.  The Msttcorefonts worked just fine for me in Ubuntu 7.04. Any ideas?

Thanks 
Khan

---

### Post by radovan01 on 2007-10-22
install x-ttcidfont-conf package

---

### Post by khan Singh on 2007-10-22
x-ttcidfont-conf  has already been installed.

---

### Post by bigboy_pdb on 2007-10-22
When I installed the fonts in Fiesty and Edgy, I noticed changes in my fonts in a variety of places. In this edition I didn't notice the changes. However, I opened Open Office and found that the Microsoft fonts were all listed in the "Font Name" drop down menu. Also, the packages that were necessary for using msttcorefonts were installed with the installation of Gutsy.

The information about the fonts that were installed and the dependencies can be found here:
[http://packages.ubuntu.com/gutsy/x11/msttcorefonts](http://packages.ubuntu.com/gutsy/x11/msttcorefonts)

I'm guessing that there might have been a change in the default fonts across versions and that the message that showed up shouldn't have appeared.

On the other hand, I had booted my system using the Live CD in order to try to fix another problem and I had opened Open Office and I noticed that the "Times" font looked identical to the "Times New Roman" font. I took a screen shot in order to compare the two and it appeared that they were identical. This means there could be a problem with msttcorefonts or one of its dependencies or that the two fonts are very similar. Perhaps someone else will have more information regarding this issue.

---

