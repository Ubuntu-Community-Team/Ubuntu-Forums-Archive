---
title: "Solution to loss of network on upgrade to Edgy"
date: 2006-12-18
forum: Apple PPC Users
---

### Post by beech on 2006-12-18
I have a Mac iBook G3 600MHz.  Initially I installed Ubuntu Dapper 6.06 which worked fine.  However on upgrading to Ubuntu Edgy 6.10 my network (wired ethernet) has not properly initialised itself on startup.  I have had to initialised it manually every time I restart the computer, which was a bit annoying.

I now appear to have found a solution to this problem (and perhaps others).  It appears that there is a bug (number 52679) which prevents the yaboot pointing to the newest kernel when the kernel is upgraded.  See: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/52679](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/52679)

The solution to this is to manually update the symbolic links in /boot to point to the latest kernel.  Once I had done this, my network connectivity was restored at startup and I was happy again.

This is how I did it.  Open up a terminal (Applications/Accessories/Terminal) and type the following (you may need to type in your password):

```

cd /boot
sudo rm vmlinux
sudo ln -s vmlinux-2.6.17-10-powerpc vmlinux
sudo rm initrd.img
sudo ln -s initrd.img-2.6.17-10-powerpc initrd.img

```

Please note that this is the most recent kernel at the time of writing, you will have to check which the latest numbered kernel is and change the numbers as appropriate (type 'ls /boot' and choose the highest number).  Presumably you will have to repeat this procedure every time the kernel is upgraded until this bug is fixed.

I hope this is of help to other users.

William

---

