---
title: "Setting up an advanced open with command?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by yaknowwat on 2007-12-30
cd '<directory name>' && chmod -x './<filename>' && gksudo sh './<filename>'

Is basically the shell command I want to set up for making *.bin ready for an auto install.

The other two things I'm wondering about is making it so that a terminal opens for these commands and the bin install.

Also making an Option called "Install..." below Create Archive or below Open With 'Default App'

Any help would be appreciated.  I probably plan to use the same concept to set it up so that rpm's and tarball's are changed into .deb's.

(I know it might not be the safest choice but, it makes things easier.)

---

### Post by nick_h on 2007-12-30
It sounds like you want to write a nautilus script.

Have a look at the [g-script](http://g-scripts.sourceforge.net/) website.  There maybe a script that already does what you want.  If not there are lots of examples to help you write one.

---

