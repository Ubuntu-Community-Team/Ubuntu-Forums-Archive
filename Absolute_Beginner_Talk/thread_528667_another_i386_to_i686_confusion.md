---
title: "another i386 to i686 confusion"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Backharlow on 2007-08-18
This is a bit vague- although nothing dire...
I moved from i386 to the i686 kernel a while back. I am just wondering when/how/if I should start moving to i686 software. My source list still shows everything as being i386, but I'm not sure how to go about changing this, if it's even possible. Also, in grub, nothing visibly changed from i386 to i686. For example:

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1de4ba86-9882-49ad-8da7-697a26c156bf ro splash
initrd		/boot/initrd.img-2.6.20-16-generic

This shows the kernel version and type, but not class as in i383, i686? Something is elluding me here.

---

### Post by insane_alien on 2007-08-18
ubuntu uses the generic kernel now. 

this automatically loads the i686 optimisations on the fly. there isn't much difference between i386 and i686. any performance enhancement is minimal. 

if you run 'uname -a' from the command line it will tell you you are using i686

---

