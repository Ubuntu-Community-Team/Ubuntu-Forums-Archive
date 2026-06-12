---
title: "Updating Linux Kernel"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by nite owl on 2006-12-13
Hi....Is updating the kernel allot like updating the firmware on a device...By that I don't mean you complete the same process to update them I'm just looking for some grounding on the issue..Like when theres a bug in my PMP(Portable media player) I look for firmware updates whereas on Linux would you look for Kernel updates??? Also would you recommend updating???

---

### Post by cilynx on 2006-12-13
To think about it from a Windows perspective, the kernel is "all of the hardware drivers"

On a complex OS like Linux, you need to see what part is messing up.  Sometimes it's userspace, sometimes it's kernel.  Often hardware problem go away (or get worse) with different kernel versions.  However, the quick and dry answer is:  If you have to ask what the kernel is, you're probably not ready to build your own.  The Ubuntu team does a good job of maintaining a kernel that Just Works for most of the population.  

Here's the current working draft of the kernel build howto from TLDP:

[http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html](http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html)

---

### Post by nite owl on 2006-12-13
Thanks cilynx..To my understanding the latest stable kernel is 2.6.19.1??? But the DVD that just shipped to me (dapper) was running 2.6.17??? Would it be a relativley easy process to go to kernel.org and download the latest stable version, then update it on my machine??? Is it recommended to update the Kernel??

---

### Post by nite owl on 2006-12-13
Oh and in regards to the user space and kernel space I have a basic understanding that it's Kernel space where the Kernel is run and its strictly for the kernel and user space is the memory area where all user mode applications work??? Could someone if at all possible link me to a page/tutorial/info..anything that futher clarifies this subject at a reasonably simple level

---

### Post by cilynx on 2006-12-13
Updating your kernel from source is generally a configuration nightmare.  You can always just copy the old config from your currently running kernel, but you still have to deal with any changes that were made between the versions.  The second problem when using a large distro like Ubuntu is that the apps expect specific kernels.  You can role you own, but your mileage may vary.  Personally, all of my Ubuntu boxen run stock distro kernels.  My Debian boxen are about half and half.

---

### Post by cilynx on 2006-12-13
As for user space and kernel space:

Check out Wikipedia:
[http://en.wikipedia.org/wiki/User_space](http://en.wikipedia.org/wiki/User_space)

For a little thicker discussion:
[http://biblioweb.sindominio.net/telematica/open-sources-html/node88.html](http://biblioweb.sindominio.net/telematica/open-sources-html/node88.html)

---

### Post by nite owl on 2006-12-13
thanks a lot cilynx for the info...:)

---

### Post by cilynx on 2006-12-13
No worries.  Have fun with it.  Be happy you have modern hardware at your disposal.  I learned to compile kernels on a 386 dx/25.  Any little configuration mistake was another 24 - 30 hours of compiling before being able to test it again.

---

