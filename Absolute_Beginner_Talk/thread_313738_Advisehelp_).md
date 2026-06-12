---
title: "Advise/help :)"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by DUNC4N on 2006-12-06
Well I've recently installed ubuntu DD. I went from 32 to 64bit version because of an error with trying to install nvidia driver. (only one day on the 32bit version) I'm wondering if I should stick with the 64bit version? 

MY system;
AMD 4000
2gb ram
7900gt
Secondly, 

I've tried easyubuntu, to re-install the nvidia driver, and it dosen't seem to be working. I followed the process in the ubuntu desktop guide, but was unsuccessful.

I'd would like to print up a cheat-sheet of basic ubuntu comands, like the important ones. (I couldn't even figure out how to get back to desktop enviroment)

Thanks for the help.

-noob

---

### Post by igknighted on 2006-12-06
> **DUNC4N said:**
> Well I've recently installed ubuntu DD. I went from 32 to 64bit version because of an error with trying to install nvidia driver. (only one day on the 32bit version) I'm wondering if I should stick with the 64bit version? 

MY system;
AMD 4000
2gb ram
7900gt
Secondly, 

I've tried easyubuntu, to re-install the nvidia driver, and it dosen't seem to be working. I followed the process in the ubuntu desktop guide, but was unsuccessful.

I'd would like to print up a cheat-sheet of basic ubuntu comands, like the important ones. (I couldn't even figure out how to get back to desktop enviroment)

Thanks for the help.

-noob

Have you tried installing through apt yet?  Just type this into a terminal window:
```
sudo aptitude install nvidia-glx
```

If you need a 9xxx series driver (mainly only for AIGLX) you may need to add another repository to get it, but if this is the case post back and I can find out which one.

---

### Post by tommytom on 2006-12-06
I had issues with the NVIDA drivers too when i installed Ubuntu 64. Tried downloading them from NVIDIA and i had loads of dependecy issues which in my lameness i couldn't fix. So i got Automatix and they just worked :)

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

