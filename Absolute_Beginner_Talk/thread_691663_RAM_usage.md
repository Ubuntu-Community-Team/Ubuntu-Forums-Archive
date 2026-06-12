---
title: "RAM usage"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-02-08
I typed the command ```
free -m
``` and got the following ```
             total       used       free     shared    buffers     cached
Mem:           502        488         14          0         36        195
-/+ buffers/cache:        256        245
Swap:         1160          0       1160

``` Is this normal or is something wrong?

---

### Post by macogw on 2008-02-08
That's normal.  It's cacheing a bunch of memory so that it can grab it and put it into use quickly when you need it.

---

### Post by scorp123 on 2008-02-08
> **intense.ego said:**
> Is this normal or is something wrong? Why do you ask? Looks normal. Only 256 MB are really used, the rest is used for buffering and caching. Swap is not used at all. Perfect. Exactly as Linux should behave. :)

---

### Post by intense.ego on 2008-02-08
Then what exactly is the swap for?

---

### Post by p_quarles on 2008-02-08
> **intense.ego said:**
> Then what exactly is the swap for?
It will be activated if the system has a need for more than your total phsyical memory. It's important for stability, but you will notice a system lag when it comes into use -- so not something you want to use most of the time.

---

### Post by scorp123 on 2008-02-09
> **intense.ego said:**
> Then what exactly is the swap for? Just in case ... It's better to have it and not need it than to need it and not have it. Besides: On laptops the swap area is used for hibernation too: All the RAM's contents get written to the swap area and when the laptop wakes up again the RAM contents are loaded back from swap into RAM ... So ideally your laptop and all the applications should resume with whatever they were doing before the hibernation.

---

### Post by OrangeCrate on 2008-02-09
Linux Memory Management or 'Why is there no free RAM?'

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

---

### Post by euler_fan on 2008-02-09
[Gusty Startup Programs]("http://ubuntuforums.org/showthread.php?t=619226")

If you turn a few off it'll knock down the amount of RAM you're using for programs.

---

