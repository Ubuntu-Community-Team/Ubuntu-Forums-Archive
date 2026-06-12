---
title: "how can i uninstall a kernel"
date: 2007-08-18
forum: Apple PPC Users
---

### Post by jaskah on 2007-08-18
hello
i recently installed a real-time kernel but something went wrong and i would like to uninstall it and try again.
i installed using the following great tutorial:
[http://tinyurl.com/28dldt](http://tinyurl.com/28dldt)
can someone tell me how to uninstall the kernel i just installed?
thanks in advance for any help!

---

### Post by ChillMonkey on 2007-08-23
sure.

reboot to the original kernel(hit tab at the yaboot menu to see options), it's likely called 'Linux'
edit */etc/yaboot.conf* to remove the entry you created, run *sudo ybin -v*
then *sudo dpkg -r <name of the kernel deb files such as linux-headers-2.6.x linux-image-2.6.x>*

where *<name of the kernel deb files such as linux-headers-2.6.x linux-image-2.6.x> *is the name of the kernel you tried to install

hope that helps

---

