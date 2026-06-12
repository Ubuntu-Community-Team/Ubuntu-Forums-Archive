---
title: "Apple Cinema 30&quot; display"
date: 2008-04-09
forum: Apple Intel Users
---

### Post by mikepn on 2008-04-09
Hi everyone,
Due to department buying policies, I have an Apple Pro with a 30" Apple Cinema display that I am supposed to install Ubuntu on. The installation went just fine and it runs perfectly, except that I cannot get it to display at the proper resolution. (The Cinema display is a super-wide screen display.) There is another computer (set up by someone no longer in the department) that has the same monitor and graphics card and is working fine. I tried copying over the appropriate entries from xorg.conf, but Ubuntu clearly didn't like those configurations, and informed me that it is running in "Low graphics mode". (The display driver, fglrx, is installed.)

If anyone knows what to do, please let me know.

Thanks so much.

-Michael

---

### Post by plasmatonic on 2008-04-16
From the terminal run:```
fglrxinfo
``` and post the results.

It sounds like the fglx driver isn't actually installed. What method did you use to install the restricted module?

---

