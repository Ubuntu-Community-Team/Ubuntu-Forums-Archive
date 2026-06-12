---
title: "*** Cannot find kernel version in /lib/modules/2/6/20-16-lowlatency/build"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by k3lt01 on 2007-11-25
*** Cannot find kernel version in /lib/modules/2/6/20-16-lowlatency/build is the response I am getting when I am trying to get my iwireless internet working again. I have had to reinstall ndiswrapper and now want to get my network working properly again.

It does recognise my wireless card and the driver is still installed but I keep getting this, even when the PC does its forced check after 30 starts.

Is there a way to fix this or do I have to do a reinstall of Ubuntu?

---

### Post by elctb on 2007-11-26
That might be caused by using a windows driver, I assume. The kernel version should have dots instead of slashes. 

I would create the directories the driver/application is looking for and create a link to the real build directory, something like this:

```
cd /lib/modules
sudo mkdir -p 2/6/20-16-lowlatency
cd 2/6/20-16-lowlatency
sudo ln -s /lib/modules/2.6.20-16-lowlatency/build build

```

Maybe this works.

---

### Post by k3lt01 on 2007-11-26
sorry that was my typing, I kept getting the wrong key.

Thanks for the help, I decided to just re-install Feisty, as I didn't know how long it would be till someone reseponded. I did this cause I went lokking through the old posts and there are some that have not been replied to yet with the same issue.

---

