---
title: "Xdtv"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Zaid on 2006-09-13
So I try to install xdtv but I get the error "Error: Dependancy is not satisfiable: xdtv  " Any help ? Thanks!

---

### Post by Den-Can on 2008-06-10
XDTV Installation ...

1- Install XDTV from xdtv web site ( deb package )
2- Install libxdtv from xdtv web site ( deb package )
3- Need libXaw3d.so.6: Parts in this package:
sudo apt-get install xaw3dg
4- Install libzvbi.so.0 from repos ( libzvbi in Synaptic )

Then open xdtv from the terminal or using Alacarte add this new application in your favorite menu section

( xdtv is in /usr/bin ... The Icons are in:/usr/share/xdtv/icons )

Note: To got XDTV menu rirgt click on your mouse

Xdtv does not keep previous setting you got to edit xdtvrc in your home folder ( show hidden file first ) /home/yourname/xdtv ...

#
# Global options
#
norm = NTSC ( or PAL or SECAM )
capture = grab
source = S-Video ( you input source )
subpage = 888
freqtab = ntsc-us-cable

( more info at the bottom of this file )
Save the file and BINGO ... Hope this help ...

---

