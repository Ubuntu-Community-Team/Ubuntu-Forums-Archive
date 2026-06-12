---
title: "32 or 64 bit?"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by CookieOrc on 2006-02-18
I have currently installed the AMD64 bit ubuntu. I have herd that I should stick my tail in between my legs and run... Is there anyway I can make it 32bit instead. Or is 64bit really not that bad?

---

### Post by jjf on 2006-02-18
I gave up on my 64 bit install.  Too many things weren't supported.  Does it work to just install the 32 bit version on a 64 bit machine?

---

### Post by CookieOrc on 2006-02-18
Yea i can. I have a 
3800 Athlon64 X2
The 32 bit works just fine.  I had that before the 64 bit version I just accidently deleted that partition and so I have to start all over and I accidently used the 64 bit version. So would it be more work to reinstall the 32 bit version or to just stay with the 64 bit version.

---

### Post by nalmeth on 2006-02-18
You can create a 32-bit chroot environment within your 64-bit, if you don't mind doing this sort of thing. It's easier than it sounds, and works quite well.

[http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit)

follow this guide, but change *every single instance* of 'hoary' with 'breezy'. DON'T FORGET ANY!!

I eventually dumped the 64-bit, because it wouldn't use the i810 driver for my intel card, for some reason.

EDIT: No tail between legs for me, and I was brand new when I tried this out. Ubuntu 64 is quite good compared to other OS's 64-bit support. Its the applications from 3rd parties that haven't employed 64-bit support yet. Ubuntu is on top of the matter

---

