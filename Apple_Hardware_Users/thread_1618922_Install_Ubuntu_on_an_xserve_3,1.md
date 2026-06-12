---
title: "Install Ubuntu on an xserve 3,1"
date: 2010-11-11
forum: Apple Hardware Users
---

### Post by larsribe on 2010-11-11
Hi all Ubuntu wizards,
I have been trying to install Ubuntu on an xserve 3,1 for the last couple of days with no luck.
If I try to use the newest Ubuntu or Debian installer (64 bit), it stops quite fast.
The output of the last, relevant lines are approx:
List of all partitions:
No filesystem could mount root, tried:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)

The lines in grub.cfg is:
fakebios
linux/path/to/linux videofb=efifb noefi
initrd /path/to/initrd

I also tried without the noefi.
I have also tried with a slackware with the same result.
The kernel version for the Debian (which I tried the most) was 2.6.32.

The strange thing is that I have a net install from a Debian stable that starts up perfectly!! The kernel version is here 2.6.26-2. The problem with this one is that it has no working driver for the network :-(

So, has anyone a running version of Ubuntu on an xserve 3,1? Or any idea about how to circumvent the problems?

Please let me know if you need more info.


Best,

Lars

---

### Post by linuxopjemac on 2010-11-11
[https://help.ubuntu.com/community/Xserve1-1](https://help.ubuntu.com/community/Xserve1-1)
[https://help.ubuntu.com/community/Xserve2-1](https://help.ubuntu.com/community/Xserve2-1)
[http://blog.christophersmart.com/2009/07/23/linux-on-an-apple-xserve-efi-only-machine/](http://blog.christophersmart.com/2009/07/23/linux-on-an-apple-xserve-efi-only-machine/)

---

### Post by larsribe on 2010-11-11
Hi linuxopjemac
Thanks for a quick reply.
I have tried all of these, but with no luck. None of them describe the current hardware with the newest kernels.

---

### Post by metatechbe on 2010-11-11
Hi Lars,

The error message is very close to the error message that occurs with the latest Linux kernels in combination with grub 1.98.
Please try with grub-trunk, see instructions :
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

Regards,

metatech

---

### Post by larsribe on 2010-11-12
Hi metatech
 Thanks for the hint! I really don't get that I didn't see it myself :)
 Now, I have a different problem:
 I followed the instructions, but end up with "Error: no suitable mode  found" when trying the linux command in grub. Is that what can be expected if the framebuffer doesn't know  about my hardware? We never got the the ram disk, so I will have to  patch the c-file and compile a kernel, right?
 
 Best,
 Lars

---

### Post by larsribe on 2010-11-12
To ask this another way: Can I obtain a precompiled grub.efi expected to work on an xserve and a new kernel?

---

### Post by metatechbe on 2010-11-12
> **larsribe said:**
>  I followed the instructions, but end up with "Error: no suitable mode  found" when trying the linux command in grub. Is that what can be expected if the framebuffer doesn't know  about my hardware? We never got the the ram disk, so I will have to  patch the c-file and compile a kernel, right?
 
 Best,
 Lars

Hi Lars,
The solution for the error message can be found here :
[http://www.mail-archive.com/bug-grub@gnu.org/msg12651.html](http://www.mail-archive.com/bug-grub@gnu.org/msg12651.html)
It means grub cannot detect the graphics properties.
On my machine, it also reports it, but because the efifb.c has the correct FrameBufferBase value, it can be ignored : the kernel is able to display the console.

metatech

---

