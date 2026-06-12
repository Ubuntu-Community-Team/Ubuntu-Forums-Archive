---
title: "Tell you how to remove the old kernels after upgrading to Ubuntu Gutsy"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by huangweiqiu on 2007-09-15
I upgraded my Ubuntu 7.04 to 7.10 Test 5 just now,but I found my main partition lost almost 1G space.The reason is that upgrade system will not delete your old kernels automatically while upgrading Ubuntu. The old kernels take much space of partition and normally we seldom use those order kernels again,let's delete them in save way for freeing more space.


Firstly,we need to see how many older kernels in the Ubuntu,following command can list all kernels for you :~

edward@edward-laptop:~$ dpkg --get-selections|grep linux

You will see result like below once above execute is executed :~
libselinux1 install
libselinux1-dev install
linux-generic install
linux-headers-2.6.20-12 install
linux-headers-2.6.20-12-generic install
linux-headers-2.6.20-14 install
linux-headers-2.6.20-14-generic install
linux-headers-2.6.20-15 install
linux-headers-2.6.20-15-generic install
linux-headers-2.6.20-16 install
linux-headers-2.6.20-16-generic install
linux-headers-2.6.22-11 install
linux-headers-2.6.22-11-generic install
linux-headers-generic install
linux-image-2.6.20-12-generic install
linux-image-2.6.20-14-generic install
linux-image-2.6.20-15-generic install
linux-image-2.6.20-16-generic install
linux-image-2.6.22-11-generic install
linux-image-generic install
linux-libc-dev install
linux-restricted-modules-2.6.20-12-generic install
linux-restricted-modules-2.6.20-14-generic install
linux-restricted-modules-2.6.20-15-generic install
linux-restricted-modules-2.6.20-16-generic install
linux-restricted-modules-2.6.22-11-generic install
linux-restricted-modules-common install
linux-restricted-modules-generic install
linux-sound-base install
linux-ubuntu-modules-2.6.22-11-generic install
util-linux install
util-linux-locales install

--------------

Secondly,all right,as you see,all 2.6.20 kernels are old,we need to remove them :~

edward@edward-laptop:~$ sudo apt-get remove linux-image-2.6.20-16*

Just need to take 10 second,you will remove those old kernels safely!

Lastly,pls remember this useful command: uname -a ,this command can show what kernel you are using.

[http://www.linuxine.com/2007/09/tell-you-how-to-remove-old-kernels.html](http://www.linuxine.com/2007/09/tell-you-how-to-remove-old-kernels.html)

---

### Post by mocoloco on 2007-09-16
I didn't realize you can use wildcards with apt-get, very nice.  Quick and easy.

---

### Post by ramjet_1953 on 2007-09-16
The easy way to remove redundant kernel images is to go into Synaptic Package Manager and do a search on Linux Image.

This will list all kernel images that are loaded and you can just select the ones that you don't want and remove them.

It also automatically cleans up the GRUB listings.

Regards,
Roger 8)

---

### Post by mocoloco on 2007-09-16
See that's what I would always do, search through synaptic, and select packages one-by-one for removal.  This is much faster, only one command.  It's still apt, so it would still clean up GRUB and everything else.  Another example of where command line is so much more powerful than gui tools.

---

