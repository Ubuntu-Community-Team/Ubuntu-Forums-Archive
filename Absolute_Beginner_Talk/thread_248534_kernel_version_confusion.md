---
title: "kernel version confusion"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Charles Hand on 2006-09-01
Suppose I want the kernel headers for the currently-running kernel. I'm trying to install vmware, and it wants the kernel headers. It's expecting to find them in /usr/src/linux/include.

charlie@gemini:/usr/src/linux$ uname -r
2.6.15-26-386

So I apt-get linux-headers-2.6.15-26-386, and it gives me two new directories, 
/usr/src/linux-headers-2.6.15-26 and /usr/src/linux-headers-2.6.15-26-386

vmware is unhappy with both of these directories because they do not have a linux subdirectory.

So I figure I'll try to build an exact copy of my kernel. I get linux-source which gives me linux-source-2.6.15. I extract that and symlink it to /usr/src/linux and vmware complains that /usr/src/linux/include/linux doesn't have a version.h file. 

So I copy /boot/config-2.6.15-26-386 to /usr/src/linux/.config and do a make oldconfig, and make-kpkg kernel_headers, and now I have a version.h but it's not 2.6.15-26-386!!! It's 2.6.15.7-ubuntu1. And vmware complains that it doesn't match my running kernel.

Finally, if I build the kernel, which I expect to give me a duplicate of my running kernel, the wireless doesn't work.

What am I missing?

---

### Post by MrHorus on 2006-09-01
> **Charles Hand said:**
> Suppose I want the kernel headers for the currently-running kernel. I'm trying to install vmware, and it wants the kernel headers. It's expecting to find them in /usr/src/linux/include.

What am I missing?

Delete that /usr/src/linux tree that you created and then create a symbolic link like thus:

```
ln -s /usr/src/linux-headers-2.6.15-26-386 /usr/src/linux
```

Then vmware should find the kernel headers in that symbolicly linked directory /usr/src/linux/include

---

### Post by TFX360 on 2006-09-01
> **Charles Hand said:**
> Suppose I want the kernel headers for the currently-running kernel. I'm trying to install vmware, and it wants the kernel headers. It's expecting to find them in /usr/src/linux/include.

charlie@gemini:/usr/src/linux$ uname -r
2.6.15-26-386

So I apt-get linux-headers-2.6.15-26-386, and it gives me two new directories, 
/usr/src/linux-headers-2.6.15-26 and /usr/src/linux-headers-2.6.15-26-386

vmware is unhappy with both of these directories because they do not have a linux subdirectory.

So I figure I'll try to build an exact copy of my kernel. I get linux-source which gives me linux-source-2.6.15. I extract that and symlink it to /usr/src/linux and vmware complains that /usr/src/linux/include/linux doesn't have a version.h file. 

So I copy /boot/config-2.6.15-26-386 to /usr/src/linux/.config and do a make oldconfig, and make-kpkg kernel_headers, and now I have a version.h but it's not 2.6.15-26-386!!! It's 2.6.15.7-ubuntu1. And vmware complains that it doesn't match my running kernel.

Finally, if I build the kernel, which I expect to give me a duplicate of my running kernel, the wireless doesn't work.

What am I missing?

I installed

sudo aptitude install linux-headers-2.6.15-26

So without the -386 worked like a charm for vmware.


Hope it helps,

---

### Post by Charles Hand on 2006-09-01
That worked, Horus. I could have sworn I had tried that. Thanks, too, TFX.

-charlie

---

### Post by TFX360 on 2006-09-01
Your welcome. Happy VMwaring. Love the product. We at our company have ten DL380 with ESX installed. Gotta love it!

---

### Post by slyride on 2006-09-21
Hi all,
I am pretty new to this, but I just ran into the same thing when I was upgrading my vmware tools.  I just realized though that I had applied automatic updates the other day and one of them was the kernel version 2.6.15-27-386.  So I ran:
```
sudo apt-get install linux-headers-2.6.15-27-386
```
and then to remove the previous symbolic link for the linux-headers-2.6.15-26-386 :
```
sudo rm /usr/src/linux
```
and then to add the new symbolic link:
```
sudo ln -s /usr/src/linux-headers-2.6.15-27-386 /usr/src/linux
```
That worked great....
Hope this help someone else.

---

