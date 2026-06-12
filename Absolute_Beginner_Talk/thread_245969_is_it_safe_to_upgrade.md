---
title: "is it safe to upgrade?"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by ezek on 2006-08-28
Hey, ever since the crash last week, ive been scared to upgrade ubuntu. is it safe to upgrade now>?

---

### Post by benfindlay on 2006-08-28
absolutely, as long as the x version you see in the update list has 10.4 at the end, you're good to go!

---

### Post by anaconda on 2006-08-28
What is safe?

I don't upgrade kernel wery often, because updating kernel screws some things.. eg. VMWare and Grub..

---

### Post by taurus on 2006-08-28
You don't have to upgrade your kernel every time a new one comes out!!!

---

### Post by davebgimp on 2006-08-28
That whole crash business was a non-issue for me. I just booted the previous kernel until the problem was fixed. An inconvenience of about five minutes at most. On top of this, the problem itself was fixed by the time I awoke the next day. As long as you keep one stable previous kernel, you always have a fall-back till things are set. This is one of the things I really like about Linux-based OS. Options.

---

### Post by Otto-C on 2006-08-28
How to find the previous kernal to boot and how to set it.
tia
Otto-C
*********
That whole crash business was a non-issue for me. I just booted the previous kernel until the problem was fixed. An inconvenience of about five minutes at most. On top of this, the problem itself was fixed by the time I awoke the next day. As long as you keep one stable previous kernel, you always have a fall-back till things are set. This is one of the things I really like about Linux-based OS. Options.
*********

---

### Post by L_o_N_e_R on 2006-08-28
i think its in the GRUB boot loader

there are 4 ubuntu entries pick one that doesnt have recovery mode in it

---

### Post by az on 2006-08-28
> **anaconda said:**
> What is safe?

I don't upgrade kernel wery often, because updating kernel screws some things.. eg. VMWare and Grub..

If you compiled a vmware kernel yourself, you will have to recompile it every time you update your kernel.  Vmware player is in the repos, you know.  That will solve that problem for you since it comes witha vmware-player-kernel-modules package that gets upgraded, too.

Updating your kernel should never screw up grub.  If you edit the grub entries improperly, when grub updates the list, your changes will be lost.  You should read the comments in the menu.list file to see how to change the entries so that they get refreshed the way you want.  You need to add your arguments to the commented lines.

---

### Post by az on 2006-08-28
> **taurus said:**
> You don't have to upgrade your kernel every time a new one comes out!!!

If you are saying that when a new linux-image package is available in the updates or security-updates repo, you should ignore it, that is bad advice.

The kernel can get patched for security vulnerabilities and bugs - you most certainly *should* install those updates.

---

