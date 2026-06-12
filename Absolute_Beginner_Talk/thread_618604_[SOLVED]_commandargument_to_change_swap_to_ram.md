---
title: "[SOLVED] command/argument to change swap to ram"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-11-20
I had found and lost a simple command to change the swap file from a value of 60 to (I made it) 10. I can't find that again. Also, I want to make it permanent.

---

### Post by forestpixie on 2007-11-20
are you talking about swappiness, where the default is 60??

---

### Post by dstew on 2007-11-20
There are two ways to swap in Linux, a swap *partition* or a swap *file*. From your post, it appears you are talking about using a swap file. To use a swap file, you need to create a contiguous file in your root directory using the **dd** command, then designate it using the **mkswap** command. You can vary the size in either the dd or mkswap commands. After the mkswap command, you use the **swapon** command to use it. See the mkswap man pages, either in your terminal, or [here]("http://linux.die.net/man/8/mkswap").

---

### Post by Mark_in_Hollywood on 2007-11-20
Yes, and I located another version of the change:

[http://linux.wordpress.com/2007/03/28/tip-manage-the-use-of-swap-memory/](http://linux.wordpress.com/2007/03/28/tip-manage-the-use-of-swap-memory/)

The use of the swap memory by default on Kernel 2.6.xx is set to 60% that means that the system will use intensively the swap memory. This sounds good if we have a small amount of memory (around 512MB or less) and lot of load on our PC especially if it is working as server. But if we have plenty of RAM (at least 1GB), as I do which is 2GB, and we are using our PC as desktop machine for daily use, we can change the percentage of swap to be utilized. This setting will increase the performance of Linux experience.
This is valid for quite a lot os distributions inlcuding openSUSE, Debian, Fedora and CentOS.

On a Terminal do this as root (use sudo if running Ubuntu)

    cat /proc/sys/vm/swappiness

You should see 60. Now change it to 10

    sysctl -w vm.swappiness=10

Now is time to work for some minutes with some applications if you see that is better, you can make the changes permanent.

    vim /etc/sysctl.conf

and add this line at the end (let me know if it is better to insert this in other file for openSUSE distribution)

    vm.swappiness=10

This Ubuntu user made do with gedit for the editing of the file. On runing cat /proc/sys/vm/swippiness after the edit, I received a value of 10. On cold booting several hours later, the same day, I received a swappiness value of 10.

---

