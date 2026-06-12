---
title: "swap size?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-04-29
my memory always seems to be full (according system resources panel thingy). especially when running qemu w/ win2k. would increasing the swap size (512mb atm) increase performance?

btw, i have 1280mb ram

---

### Post by mikewhatever on 2007-04-29
Does your swap gets fully used? If yes then you should increase it's size.

---

### Post by supersonicdarky on 2007-04-29
as far as i can see, yes.

[IMG]http://img.photobucket.com/albums/v242/supersonicdarky/123.jpg[/IMG]

---

### Post by Metacarpal on 2007-04-29
> **supersonicdarky said:**
> my memory always seems to be full (according system resources panel thingy). especially when running qemu w/ win2k. would increasing the swap size (512mb atm) increase performance?

btw, i have 1280mb ram

In the system resources applet, is the memory used shown in two different colors?

If so, look at the Preferences/Settings for the memory display.  Odds are, you'll find that the color filling the top of your memory usage meter is the color for "Cache".

This is normal Linux behavior.  When Linux detects that you have free memory, it tries to determine what files, libraries, etc you'll probably need next, or have used recently, and pre-loads them into memory.  This is called caching, and it helps your system run (or at least respond) faster.

When processes need access to memory currently being used for caching, Linux will empty some of the cached memory, freeing it up for normal process use.

---

### Post by Metacarpal on 2007-04-29
Ah - you posted while I was typing.  Looking at your screenshot, it looks like you're using about 2/3rds of your memory.  The top third is cache - you don't need more swap space.  Your system is doing just fine.

---

### Post by mikewhatever on 2007-04-29
What does 'free' command gives?

---

