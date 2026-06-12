---
title: "MacBook - Kubuntu not booting"
date: 2007-03-22
forum: Apple Intel Users
---

### Post by xnyhps on 2007-03-22
Hello,

Yesterday I decided to put Kubuntu on my MacBook Core2Duo 2.0 GHz, so I followed these instructions: [http://blog.mobiledude.com/articles/2006/08/20/apple-macbook-dual-booting-ubuntu-linux](http://blog.mobiledude.com/articles/2006/08/20/apple-macbook-dual-booting-ubuntu-linux) . I downloaded and installed Boot Camp, and made a 10 GB partition for 'windows'. Then I downloaded and installed rEFIt, and everything went fine.
I booted from a kubuntu 7.04 herd 5 , and started the installation. Apart from some errors with ubiquity (that I solved by doing a sudo apt-get install ubiquity first) everything went fine.
Then I chrooted into my ubuntu partition and installed lilo. My lilo.conf looks like this:

```
boot=/dev/sda3
default=Ubuntu

map=/boot/map
delay=20
image=/vmlinuz initrd=/initrd.img
append="root=/dev/sda3"
root=/dev/sda3
label=Ubuntu
read-only
```

I rebooted, synchronized the tables in rEFIt, and then tried to start Kubuntu. But I get a lot of errors about files not being found:

```

....
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
Done.
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
FATAL: Could not load /lib/modules/2.6.20-9-generic/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.20-9-generic/modules.dep: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.1.3 (Debian 1:1.1.3-ubuntu2) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) _
```

And then noting happens, and the keyboard doesn't work...

I'm sure that kubuntu was installed on /dev/sda3, I can see the files when I boot from the liveCD. I tried a lot of things, I tried different options in lilo.conf, I used a different kernel, but I keep getting these errors.

Anybody knows what's wrong?

---

### Post by xnyhps on 2007-03-22
Nevermind, I got it to work. I don't really know what happend, but a reinstall did the trick.

---

