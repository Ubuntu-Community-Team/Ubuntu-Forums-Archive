---
title: "gnucap"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Teddy_P on 2007-06-04
I get an error when the kids try to play with GCompris. When they try to play with the electric part they get this
Screenshot-GCompris.png  
I went to the site and downloaded a gnucap-0.31.tar.gz file. I moved it from the tmp folder to the desktop. Right clicked and selected Extract here. I tried to drag the new folder to the /usr/local/bin/ directory. And could not.
from terminal I ```
teddy@kids1:~$ sudo mv -u /usr/bin/gnucap-0.31 /usr/local/bin/

```
It moved but it did not work and I have searched but can not find any information on making this work.

Do you know where I can look or know what I am doing wrong?


Thanks
Teddy_P

---

### Post by wgscott on 2007-06-05
Yo Teddy:

I think you just move all the source code and junk into your /usr/local/bin directory.

Don't do that.

In fact, it is already in upbuntu, so just install it:


```
sudo apt-get install gnucap
```

This tells you what you are dealing with:

```


 aptitude  show gnucap
Package: gnucap
State: installed
Automatically installed: no
Version: 1:0.35-1
Priority: optional
Section: universe/electronics
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 3576k
Depends: libc6 (>= 2.5-0ubuntu1), libgcc1 (>= 1:4.1.1-17ubuntu1), libncurses5 (>= 5.4-5), libreadline5 (>= 5.2),
         libstdc++6 (>= 4.1.1-17ubuntu1)
Description: GNU Circuit Analysis package
 GNUCAP is a general purpose circuit simulator.  It performs nonlinear dc and transient analyses, Fourier analysis, and
 ac analysis linearized at an operating point.  It is fully interactive and command driven.  It can also be run in batch
 mode or as a server. The output is produced as it simulates.  Spice compatible models for the MOSFET (level 1,2,3) and
 diode are included in this release.



```

---

### Post by Teddy_P on 2007-06-05
Thanks I will try it tonight.


Teddy

---

### Post by Teddy_P on 2007-06-05
It worked:
I will use the
Code:
aptitude show

command alot.


Thanks
Teddy

---

