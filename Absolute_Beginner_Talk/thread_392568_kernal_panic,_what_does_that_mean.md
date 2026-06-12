---
title: "kernal panic, what does that mean?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by taco2 on 2007-03-24
Kernel panic


I always thought it had to do with when the fried chicken burnt.

I'm getting fustrated with trying to install the server on a AMD 1.6, 256 mb, machine, but I don't want to give up.

Can someone point me in the direction of a simple reference for what a panic kernal means ad what one does about a kernal who is panicking.

---

### Post by mikewhatever on 2007-03-24
[http://en.wikipedia.org/wiki/Kernel_panic](http://en.wikipedia.org/wiki/Kernel_panic)

---

### Post by taco2 on 2007-03-24
> **mikewhatever said:**
> [http://en.wikipedia.org/wiki/Kernel_panic](http://en.wikipedia.org/wiki/Kernel_panic)

But, how do I fix a panic.  The wiki says to call down the hall, and say reboot the machine, but no one is listenning

---

### Post by mikewhatever on 2007-03-24
I am not quite sure what caused kernel panic in your case or what does in general. The link was just an answer to what it is.  :-k

---

### Post by taco2 on 2007-03-24
> **mikewhatever said:**
> I am not quite sure what caused kernel panic in your case or what does in general. The link was just an answer to what it is.  :-k


I'm glad you sent me the link.  I learned.  I now associate panic as the same at the blue screen.   Maybe I was peeved by fustration

I'll do some more research, and if I find the answer, post it hear

---

### Post by taco2 on 2007-03-25
I'm switching to try to intall 7.04 beta instead.

Spent too long trying to solve this problem

---

### Post by igknighted on 2007-03-25
A kernel panic can come for very many reasons.  Basically, something very important to the kernel is missing or incorrect and it just stops working.  When do you get the issue?  Usually I only get them on boot, usually when testing out a custom built kernel that I forgot to include something required.  I have also gotten them when I boot without the noapic option.

If you give more information about you are doing and what you did since the last time it worked we might be able to help more.  The phrase kernel panic is like saying "it crashed".  Lots of things can cause it, we need more info to diagnose it.

---

### Post by taco2 on 2007-03-28
Hi,  Thanks for helping to solve this, and pushing my learning forward.

The kernel panic was on the first boot after an new install of version 6.10.   I followed a suggestion of trying version 7.04, and the problem went away, (although I did need the command about the power control)   My reading makes me think it was a pecularity with the motherboard/bios, but since the problem is now moot, or solved by version 7.04, I will never actually know.

I don't have experience with ubuntu, and this is the first install that didn't work by iteself.

Thanks all.

---

