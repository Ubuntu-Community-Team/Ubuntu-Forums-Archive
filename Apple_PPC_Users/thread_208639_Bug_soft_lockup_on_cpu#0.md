---
title: "Bug: soft lockup on cpu#0"
date: 2006-07-03
forum: Apple PPC Users
---

### Post by RHTopics on 2006-07-03
I am getting this error message occasionally on my slot loading iMac G3 350 mhz with 384MB RAM:

Bug: soft lockup on CPU#0

The computer then needs to be completely shut down to get it to boot up.

The last time when it occurred, I was rebooting the computer because the CD drive would not accept a CD when trying to insert it.

I have seen other reports of this problem message showing up on x86 laptops using Dapper.

Has anyone else experienced this problem with their Mac?

Is a memory test available for the Mac version of Dapper?

---

### Post by slux on 2006-07-04
Unfortunately my only contribution to this topic is to tell you that no, there is no memory test in the PPC version since memtest86 which is not really in any way Linux-specific is x86-only.

Never seen the message on my iBook G3 300MHz, sorry.

---

### Post by RHTopics on 2006-07-04
slux,

Thanks for the reply.

I guess as alternative to memory test software, I have read that compiling source code does a good job of detecting memory problems.  I will give that a try to test my RAM chips.

After doing some googling, it appears this problem is with the 2.6.15 kernel and not just with Ubuntu.  From what I found so far, the "Bug: soft lockup message on CPU" message is issued by the kernel when some type of scheduling delay by CPU has occurred.  I have not been able to determine what might cause scheduling delays that are long enough to generate this message.

---

