---
title: "Re install grub"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by waltervalderrama on 2007-04-03
Hi. I use ubuntu in my pc, but I share my PC with my brother who uses Windows. He is about to upgrade to vista but i don't know how it's going to affect my ubuntu installation. I 've heard that in case a windows is reinstalled, i need to re install grub. How is it performed??

---

### Post by Rui Pais on 2007-04-03
hi,
[here is an howto]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub").

edit: and yet a better one:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

hth

---

### Post by mikewhatever on 2007-04-03
Hopefully, your trouble will be to only reinstall grub
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

good luck

---

### Post by Doug11 on 2007-04-04
> **waltervalderrama said:**
> Hi. I use ubuntu in my pc, but I share my PC with my brother who uses Windows. He is about to upgrade to vista but i don't know how it's going to affect my ubuntu installation. I 've heard that in case a windows is reinstalled, i need to re install grub. How is it performed??


I just did that upgrade myself and Rui Pais's second link is the easiest. It took a couple of tries for me but what worked was when your in the grub at your terminal,,when you go to type the step > setup (hd0,x) < x being the number the previous cammand spit out,,I just typed
> setup (hd0) < and that let me have my grub menu back of which OS I wanted to boot. Some people say that grub will not recognize vista but for me it was no problems. Good luck.

---

