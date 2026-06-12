---
title: "USB device will not accept address"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by darklyndsea on 2007-02-21
I'm installing Edgy (previously I was using Dapper, until I broke it in several interesting ways), and haven't yet made it to the GUI because in trying to install my USB devices it keeps getting errors:
> [a long number with a decimal] usb 4-2:device not accepting address #, error -110
# is 2 at the first error message, and increases by one in each error message until it reaches 127, and then it starts over.  So, how do I break it out of the loop, preferably with the USB device working?
I think I had this problem the last time I had Ubuntu installed on my computer, but that installation was mainly managed by my brother.

---

### Post by capdog on 2007-02-22
I'm new too but had a similar experience. Let's just confirm your exact steps: By 'installing' your USB devices, you mean you are booting off the live CD, and it's not getting past the splash screen?

So, then tried to boot with the splash screen and 'quiet' mode turned off, and you're seeing those messages? 

If this is not the case, elaborate on what exactly you mean by 'installing' devices?

---

### Post by darklyndsea on 2007-02-28
If anybody else has this problem, I fixed it by adding 'irqpoll' to the boot options.

---

