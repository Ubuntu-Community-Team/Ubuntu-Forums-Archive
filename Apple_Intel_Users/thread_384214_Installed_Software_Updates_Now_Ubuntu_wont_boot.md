---
title: "Installed Software Updates Now Ubuntu wont boot"
date: 2007-03-14
forum: Apple Intel Users
---

### Post by AnthonyJK@gmail.com on 2007-03-14
After finally getting Ubuntu installed and bootable using lilo I installed the software updates and now it wont boot. after i click on linux in refit it goes the the screen that says LILO 22.6.1 Loading ubuntu ............................................................................................. the dots go for about 2 1/10 lines then it stops and the underscore just blinks I dont know what to do this is so frustrating! I spent all day trying to get it installed now this! I have a MacBook 2gHz Core Duo Any help would be appreciated thanks!

---

### Post by chipm on 2007-03-15
You need to boot into an Ubuntu LiveCD and then chroot to your hard disk. Once there, you can edit lilo.conf and rerun Lilo -v and it will work. You pretty much end up following the instructions you used to get Lilo working in the first place.

---

