---
title: "installing from tar.gz"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by FISHERMAN on 2006-04-02
I trying to install a certain program but since I didn't found a *deb I tried to install it via tar.gz
When I do ./configure I get the following warning:> ... Package mono was not found in the pkg-config search path. 
Perhaps you should  add the directory containing `mono.pc' to 
the PKG_CONFIG_PATH environment varia ble No package 'mono' 
found
configure: error: Library requirements (mono >= 0.95
) not met; consider adjusting the PKG_CONFIG_PATH environment variable
 if your l ibraries are in a nonstandard prefix so pkg-config can find them.

What should I do?

---

### Post by siminone on 2006-04-02
have you got mono installed? This can be done through synaptic or apt.

Installing software from source is a pain in the backside. The best thing is to try to look a RPM version of the program and install it by:

sudo alien -k <rpm file>
sudo dpkg -i <deb file>

Where <rpm file> is the .rpm file you downoaded and <deb file> is the .deb file created from alien.

---

