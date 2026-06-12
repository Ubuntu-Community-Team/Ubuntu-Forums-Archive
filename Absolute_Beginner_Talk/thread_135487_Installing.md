---
title: "Installing"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by inovermyheadd on 2006-02-23
Hey,

I have this file  daimonin_client-BETA3-0966.tgz

Could someone please walk me through getting this game to work?

I'd really appreciate it!

Thanks,

Donald:)

---

### Post by joshuapurcell on 2006-02-24
You'll need to open up a terminal window.
First untar the package:```
tar xvzf daimon_client-BETA3-0966.tgz
```Once that's done you may need to navigate into the folder it was unpacked to (use the **ls** command to see what files are in the directory). Once you are in the same location as the unpacked files, then run you will possibly need to run these commands:```
./configure
make
sudo make install
```I say possibly because it's completely up to the package you are dealing with. This may be a binary install that doesn't require compilation, or the compilation may not require you to run ./configure as part of the setup. The only way to know for sure what you must do to install this package is to read the INSTALL or README files that should be included in the package:```
more INSTALL
```.

---

