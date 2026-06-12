---
title: "Using Intel P-state without Grub"
date: 2014-08-14
forum: Apple Hardware Users
---

### Post by Derek_Parker on 2014-08-14
I'm running Ubuntu 14.04 on a 13" MBP retina, and I followed these instructions for installation: [http://randomtutor.blogspot.com/2014/01/installing-ubuntu-on-retina-macbook-pro_19.html](http://randomtutor.blogspot.com/2014/01/installing-ubuntu-on-retina-macbook-pro_19.html).

When I installed, I ran `ubiquity -b` to install without Grub. I'd like to use the Intel P-state driver alongside thermald to control CPU temps. Currently, just during normal browsing with Chrome, I'm easily hitting 58-65 Celsius. Everything I've found so far includes editing /etc/default/grub, but that won't work.

Any suggestions?

---

### Post by llamaswill on 2014-08-14
Yes!

Assuming you're using rEFInd to boot, run sudo ./mkrlconf.sh within the rEFInd folder. This will create the file /boot/refind_linux.conf where you can change the boot options - let me know if you need any more help :)

(I'm assuming you know how to run commands, download and unzip refind, and edit files as root)

---

### Post by Derek_Parker on 2014-08-14
That worked perfectly, thanks!

---

### Post by llamaswill on 2014-08-15
Glad I could help!

---

