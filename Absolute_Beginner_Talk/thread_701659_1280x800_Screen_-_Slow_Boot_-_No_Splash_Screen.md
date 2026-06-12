---
title: "1280x800 Screen - Slow Boot - No Splash Screen"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by neal.s on 2008-02-19
I could just remove the splash screen, but I'd rather not.

I read on UbuntuGuide.org that I should use the corresponding value from their table, but my screen's native resolution isn't on that list. I tried the value for 1024 x 768, which was "vga=791", but that didn't resolve anything when I rebooted. Still no screen and still a painfully long shutdown and boot.

Does anyone know the value for a 1280x800 screen? Should I just get rid of the splash?

---

### Post by uberlube on 2008-02-19
Try adding 'irqpoll' in the same line as 'vga=791' and see if that helps

---

### Post by mcdan on 2008-02-19
i had the same problem with gutsy when i first booted it up

[http://ubuntuforums.org/showthread.php?t=579684](http://ubuntuforums.org/showthread.php?t=579684)

try what orange2k recomended in post #9, it worked for me

---

### Post by neal.s on 2008-02-19
Neither of those worked. I'm thinking I'll just disable the splash.

---

### Post by neal.s on 2008-02-19
Weird! When I disabled the splash, the shutdown still went slowly, but I could see a distorted ghost image of the splash screen, while there was just NO splash screen before.

---

