---
title: "Problem installing Grsync"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Stephen_A on 2007-04-05
Whilst attempting to install Grsync, I followed the instructions in the Install file and got the following error message: 


checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.0.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

stephen@stephen-laptop:/tmp/grsync-0.5.2$ 

I would appreciate any advice on this. Thanks.

---

### Post by Roelski on 2007-04-06
It's your lucky day!  I tried the same yesterday.

In stead of using the command line, try Synaptic.  Look there for the package "grsync"

Worked fine with me on Edgy.  It should check all dependencies and suggest any additional packages needed.

Once it's installed, you can access it via Applications>Internet, although I must admit I moved it with A La Carte Menu Editor to Applications>System - seemed more intuitive to me.

Btw: grsync is absolutely a fabulous tool for weekly backups or your /home to a USB-drive.  Since most of us are coming from the Dirty Windows World, any GUI solution feels more natural to us than the command line... 

Hope this helps.



Roelski

---

### Post by Stephen_A on 2007-04-06
Thanks, Roelski, I'll give that a shot. 

Stephen.

---

