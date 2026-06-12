---
title: "How to permanently ignore packages with Adept Updater?"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by funkiwan on 2006-10-30
I am running vmplayer, which only works with certain kernels. So I'm not interested in receiving notices of the generic packages of "linux-image-386" and "linux-restricted-modules-386". I've placed the packages on hold (see details below) but Adept Updater continues to show itself with the warning icon for those two packages. How can I get Adept Updated to permanently ignore them? 

System: 
Linux kubuntu 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
Kubuntu: 6.06

Details:
I've gone ahead and run the following command:
sudo dpkg --set-selections < my_selections

and can confirm the packages are currently on hold:
jgordon@kubuntu:~/downloads$ dpkg --list | grep ^hi
hi  linux-image-386                        2.6.15.24                              Linux kernel image on 386.
hi  linux-restricted-modules-386           2.6.15.24                              Restricted Linux modules on 386.

I've rebooted and Adept Updater still wants to tell me about them every time. Attached is the warning image which appears in the bottom right of my desktop.

---

### Post by nickburns on 2006-10-30
I had similar problems upgrading the kernel with vmware.  I have found a solution that I think will work for you too.

* vmware-config.pl fails to find the right kernel headers. It cannot find /usr/src/kernel/include and won't proceed to install or upgrade.

You have a updated kernel, but not the updated kernel headers. You can install them by executing Code:

sudo apt-get install linux-headers-`uname -r`

Now you can succesfully run Code:

sudo /usr/bin/vmware-config.pl

this will pull down the current header files and this will allow vmware to rebuild it self.  Then a kernel update will not effect your vmware.

 * You don't want to install the kernel headers manually each time there is an update.

There is a package called linux-headers-*** that automatically installs the latest kernelheaders, so you don't need to install them manually each time.

There are 4 flavours of this package: 386, 686, k7, server.

If you don't know wich one you need, execute Code:

uname -r

It will give you something like 2.6.15-26-k7 or 2.6.15-26-686

Now you know the right flavour, install it by Code:

sudo apt-get install linux-headers-***

Replace the * with 386, 686, k7 or server.

---

