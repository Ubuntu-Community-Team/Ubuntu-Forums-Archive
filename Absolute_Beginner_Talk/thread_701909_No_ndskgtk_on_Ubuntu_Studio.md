---
title: "No ndskgtk on Ubuntu Studio"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by beebeeee on 2008-02-19
Reading the help to get a wireless lan adapter working, the help gives clear instuctions to use synaptics to install ndisgtk to allow you to "wrapper" a .inf file from windows.

Sadly Ubunto Studio does not have this package.

I would have thought tools to get an internet connection working would be mandatory to be on a ubuntu studio install Disc?

here's the link for anyone else looking for it:

[http://security.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.8.1-2ubuntu1_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.8.1-2ubuntu1_i386.deb)

---

### Post by beebeeee on 2008-02-19
Well after having to jump back and forth from ubuntu to windows. I managed to get all the dependancies for ndisgtk.

ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb
ndiswrapper-common_1.18-1ubuntu2_all.deb

Now I've pointed ndisgtk  to my netcom NP5430 .inf file, and the harware looks good in ndisgtk.

Sadly when you go to configure the network, all that is there is an option to configure a modem. eth0 and wlan0 have been removed.

What do I do now?

---

