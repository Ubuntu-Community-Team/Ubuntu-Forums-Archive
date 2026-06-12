---
title: "Benq Scanner Help PLS"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by PILGU on 2007-05-09
Can somebody please explain to me How to be able to run my Benq 5000u Scanner with Xsane. I'm using Ubuntu 7.04 now and as with  Ubuntu 6.06 have'nt been able to scan anything. I have tried following the instructions on the Sane-Project site but could not understand.

---

### Post by intel on 2007-05-10
check the following site

[http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)

your scanner is supported i guess.

---

### Post by Ubimad on 2007-05-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/85488](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/85488) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				If it is a USB Scanner you may have to trouble with USB / Suspend bug in Feisty Ubuntu.

Their is for some a work around, in my case had to compile a new kernel to make my Canon scanner run.
Fix= disable "usb selective suspend/resume' in linux-source

This should not happen to Ubuntu.

---

### Post by matchstich on 2007-05-10
it does happen in ubuntu.
for me , xsane hangs,  have to force quit
xscanimage hangs --have to reboot
gimp hangs-- have to reboot.

my epson 1200 worked just fine till that set of updates came thru a while back

and i am not alone

---

