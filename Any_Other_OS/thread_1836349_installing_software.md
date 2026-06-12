---
title: "installing software"
date: 2011-08-30
forum: Any Other OS
---

### Post by coolmego on 2011-08-30
I downloaded tarball for vlc , now i don't know how tom install it. please get me the step-by step procedure to do it..
am using FEDORA

---

### Post by mikewhatever on 2011-08-31
Why not ask at [http://fedoraforum.org/?](http://fedoraforum.org/?)
We support Ubuntu here.

---

### Post by kyletstrand on 2011-08-31
First off, this should maybe be moved to Other Distro section.

But anyways, open up a terminal and move to the location where your tar.gz file is.

Type and run ```
tar zxvf <yourfile.tar.gz>
``` which will unpack your file.

Then you need to change to the newly unpacked folder. ```
cd <folder of unpacked tar.gz>
```

Then you simply need to follow these three commands, letting each do their thing before typing the new one. 
```
./configure
make
make install
```

If you get an error for the last command, you may have to give root permission, which would simply be ```
sudo make install
```

Hope that helps!

---

### Post by madjr on 2011-08-31
isnt there an rpm for fedora?

---

### Post by beew on 2011-08-31
VLC is in the RPM fusion repo. Just add it and install it with Add/Remove (or Yumex if you have installed it :))

_[http://rpmfusion.org/Configuration](http://rpmfusion.org/Configuration)_

Fedora doesn't include software with non free components in its official repository and VLC has non free codecs so it wouldn't make it into there. RPM fusion is where all the good stuffs are. :)

---

### Post by coolmego on 2011-08-31
@kyletstrand: Thanks for your reply.I tried ./configure , it works after that other commands do not work 
 
 Here is the notification it shows : 

"[sd_coolmego@coolmego vlc-1.1.9]$ sudo make
make: *** No targets specified and no makefile found.  Stop.
"

"[sd_coolmego@coolmego vlc-1.1.9]$ make install
make: *** No rule to make target `install'.  Stop.
"

---

