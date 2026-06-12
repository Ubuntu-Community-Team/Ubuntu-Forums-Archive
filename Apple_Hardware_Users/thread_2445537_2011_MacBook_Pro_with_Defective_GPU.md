---
title: "2011 MacBook Pro with Defective GPU"
date: 2020-06-15
forum: Apple Hardware Users
---

### Post by aaronjgarcia on 2020-06-15
My MacBook Pro 2011 is known for having a defective GPU. Apple recalled this GPU, but the recall has expired. I've bypassed the GPU by booting into recovery mode and using failsafex. I must do this every time with Ubuntu 18.04. I installed 14.04, because that was the disc I had and 20.04 wouldn't work with out booting into a safe mode. From 14.04, I upgrade to 16.04 and then to 18.04, which is where the trouble started. 

My goal is to upgrade again to 20.04, but I would like for the laptop to boot using the integrated graphics by default. Also when I close the laptop cover, the laptop does not go to sleep. 

Thank you in advance for your help!

---

### Post by kevin160 on 2020-06-26
Typing on that machine now.  I can't guarantee that Ubuntu 20.04 is exactly the same (I'm checking out PopOS right now), but I was running Ubuntu 19.10 until a couple weeks ago.  Have you added this to your grub?

```
set gfxmode=${GRUB_GFXMODE}
 outb 0x728 1
 outb 0x710 2
 outb 0x740 2
 outb 0x750 0
 load video
```

and added "radeon.modeset=0" to your kernel command line in /etc/default/grub?  

See [https://wiki.archlinux.org/index.php/MacBookPro8,1/8,2/8,3_(2011)](https://wiki.archlinux.org/index.php/MacBookPro8,1/8,2/8,3_(2011)) and [https://gist.github.com/ciphertxt/d446ae620e6bf52b198f724c5766f07f](https://gist.github.com/ciphertxt/d446ae620e6bf52b198f724c5766f07f)

---

