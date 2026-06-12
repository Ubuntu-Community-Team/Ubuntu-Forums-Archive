---
title: "packet terminal (xarpm)"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by jeffinhedon on 2005-12-20
Does anyone know how to download and install this prog
I have a download on my desktop called xarpm_v.1.1.sh
How do I install it 
Or is the actual program somewhere else 
Any help would be very much appreciated
:confused:

---

### Post by davekh on 2007-09-02
Its not too difficult to install..

If you go back to where you downloaded the file from  - in a directory called Debian there is a lib file you will need to get it to work - you need to download and install this first. 

Here is the link if you can't remember
[http://gb7yfs.org.uk/~veysoft/public/xarpm/V1.3.0_Alpha/Debian/libstdc++_2.95.1_2.10.0-4_i386.deb](http://gb7yfs.org.uk/~veysoft/public/xarpm/V1.3.0_Alpha/Debian/libstdc++_2.95.1_2.10.0-4_i386.deb)

Open this with the file installer and it will install.

Then open a terminal screen (which should open in your home directory...
work your way to where the xarpm file is... 
probably by doing       c../Desktop
then type the following
sudo sh  xarpm_1.3.0.sh            (press enter, give your password  and the install process will begin)

When finished (one way to get it running is 
open a terminal 
type cd /VInstall
type sudo startup & 
(input password when asked) 
and it should run.

Join the Yahoo group for this as well.. (search on XARPM in Yahoo groups) and you should be able to ask the author Ian g6vey questions. 

Dave 
G0CER

---

### Post by davekh on 2007-09-02
Apologies 

when you start the Xarpm program its
()from the VInstall directory) 
sudo ./startup &


and not 
sudo startup &

the ./ is required 

Dave
G0CER

---

