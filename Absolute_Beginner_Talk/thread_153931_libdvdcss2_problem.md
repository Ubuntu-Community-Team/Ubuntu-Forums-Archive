---
title: "libdvdcss2 problem"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by ariodante on 2006-04-02
I have just moved to Ubuntu from Windows XP.  I am trying to play DVDs.  I have looked through the other threads but not found any that reflect the same problem.  Perhaps because I do not have libdvdcss2 installed, none of the DVD players (mplayer, ogle, xine etc.) seem to work on machine (Dell Inspiron 1000).  However, when I type:

sudo apt-get install libdvdcss2, I get the following error message:

Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

Could someone please tell me what I can do to install libdvdcss2?  I suspect that this might give me more of a chance of running some of the programs that might play my DVDs.  Many thanks.

---

### Post by siminone on 2006-04-02
Does anyone know of an apt repistory that has libdvdcss?

Alternatively, you can download libdvdcss from the developers site: 

[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/)

then install it from console.

sudo dpkg -i libdvdcss2_1.2.9-1_i386.deb

---

### Post by linear on 2006-04-02
Not in the Ubuntu archive, but a method for getting it is given here: [DVDRippingandEncoding]("https://wiki.ubuntu.com/DVDRippingandEncoding").

---

### Post by Sutekh on 2006-04-02
[Ubuntu Wiki - Restricted Formats](wiki.ubuntu.com/RestrictedFormats) has some info too

```
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

---

