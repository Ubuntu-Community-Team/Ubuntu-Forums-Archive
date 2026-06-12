---
title: "[SOLVED] Blank screen after grub on T42 thinkpad - but eventually boots normally into"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-11-04
After grub, I see the first few lines of text, then just as I would expect the graphical UBUNTU with the orange grub under it, instead, the screen goes blank.

It is still booting, I can see HD activity, and can ctrl-alt-F1 to a text screen and watch it boot.

Even if I don't touch it, eventually X starts up, and I can log in normally.

So, is there any way to avoid the blank screen, by either making the graphic work, or telling it boot displaying the text boot messages by default?

---

### Post by ubnewbie2 on 2007-11-06
> **ubnewbie2 said:**
> After grub, I see the first few lines of text, then just as I would expect the graphical UBUNTU with the orange grub under it, instead, the screen goes blank.

It is still booting, I can see HD activity, and can ctrl-alt-F1 to a text screen and watch it boot.

Even if I don't touch it, eventually X starts up, and I can log in normally.

So, is there any way to avoid the blank screen, by either making the graphic work, or telling it boot displaying the text boot messages by default?


After a spot of googling, I found  Bug #25011. [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/25011](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/25011)

Removing the splash option on the kernel line works, in that it gives me text instead of the blank screen to watch.

 In the discussion, they mentioned putting

```
vga=791
```

"after grub's line", but I am not sure where they mean.  I tried putting it after the 'splash' option on the kernel line but that made it worse - nothing shows at all until X starts.

---

### Post by ubnewbie2 on 2007-11-07
Solved it !

I installed startupmanager and configured grub to use 1024x768 16 colours.

Now it all works as it was supposed to.

---

