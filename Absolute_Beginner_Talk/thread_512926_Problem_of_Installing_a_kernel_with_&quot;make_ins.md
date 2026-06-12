---
title: "Problem of Installing a kernel with &quot;make install&quot;"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Hxsrmeng on 2007-07-29
I'd like to install a kernel.

I downloaded the source code from kernel.org and unzipped it to:
/home/linux/linux-2.6.22.1

I have already configured and built it with "make defconfig", and "make".

But when I try to install it with "make install" or "sudo make install", I got the message: 
make: *** No rule to make target `install'.  Stop.

I didn't built any modules, so I don't think I need "make modules-install"

Thanks.

By the way, I have initramfs-tools package installed.

---

### Post by machoo02 on 2007-07-29
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=311158") in the Tutorials and Tips sub-forum on how to compile a kernel.

---

### Post by Hxsrmeng on 2007-07-29
Sorry for the Newbie's question.
I should use "sudo make install" in the folder "/home/linux/linux-2.6.22.1" Thanks.

---

### Post by Hxsrmeng on 2007-07-29
> **machoo02 said:**
> Check out [this thread]("http://ubuntuforums.org/showthread.php?t=311158") in the Tutorials and Tips sub-forum on how to compile a kernel.

Thanks! It's helpful! Great information!

---

