---
title: "Brightness control error"
date: 2011-06-22
forum: Apple Hardware Users
---

### Post by ishueli on 2011-06-22
Hello There,

I have iMac 2.4GHz with rEFIT installed. I installed Unity on one of the partition. Kernel is still 2.6.38.8. I am getting error message when I run the command 
sudo gedit /etc/x11/xorg.conf

The error message is

(gedit:2139): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.AC7YXV': No such file or directory

(gedit:2139): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

How can I resolve the error

---

### Post by mateo14 on 2011-06-22
1. First you have to install 2.6.39 Linux Kernel

[http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0](http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0)

2. sudo gedit /etc/X11/xorg.conf

3. "To enable brightness control in X, append 'Option "RegistryDwords" "EnableBrightnessControl=1"' to the Device-Section of xorg.conf, orginal source"

[http://www.thinkwiki.org/wiki/Category:W510](http://www.thinkwiki.org/wiki/Category:W510)

4. Reboot Your Computer

---

### Post by ishueli on 2011-06-24
Thanks for responding. I tried up upgrade the kernel to 2.6.39.0 but I keep on getting error on FGLRX. I can only get the system to boot with 2.6.38.8 kernel. Note that I am using ATI/AMD proprietary graphics driver.

---

### Post by mateo14 on 2011-06-28
> **ishueli said:**
> Thanks for responding. I tried up upgrade the kernel to 2.6.39.0 but I keep on getting error on FGLRX. I can only get the system to boot with 2.6.38.8 kernel. Note that I am using ATI/AMD proprietary graphics driver.

Try this:

[http://www.mindwerks.net/2011/04/ubuntu-11-04-natty-with-fglrx-and-2-6-39/](http://www.mindwerks.net/2011/04/ubuntu-11-04-natty-with-fglrx-and-2-6-39/)

---

