---
title: "possible bug while loading ubuntu 7.04"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by cypry on 2007-08-25
With the live CD, when I select Start or Install Ubuntu, right when the progress bar should appear, my screen is filled with odd vertical lines. It might be a problem while detecting the resolution, because when I set it to 1024x768(F4 in the boot screen), it worked fine. After I installed it, the problem persisted, but it was somehow random. Sometimes everything worked fine, sometimes the vertical bars appeared again. I think the OS was loading, because although I couldn't see anything on the screen, I heared the Ubuntu sound after a while.
I fixed this by removing "quiet splash" from /boot/grub/menu.lst.
The system loads fine now, but i'm wondering what's causing this problem.
I have an MSI laptop, with a Geforce Go 6100 video card.
I also have to mention that I used Kubuntu 6.06 before(now I have Ubuntu 7.04) and had no such problem.
Thanks.

---

### Post by tdrusk on 2007-08-25
> **cypry said:**
> With the live CD, when I select Start or Install Ubuntu, right when the progress bar should appear, my screen is filled with odd vertical lines. It might be a problem while detecting the resolution, because when I set it to 1024x768(F4 in the boot screen), it worked fine. After I installed it, the problem persisted, but it was somehow random. Sometimes everything worked fine, sometimes the vertical bars appeared again. I think the OS was loading, because although I couldn't see anything on the screen, I heared the Ubuntu sound after a while.
I fixed this by removing "quiet splash" from /boot/grub/menu.lst.
The system loads fine now, but i'm wondering what's causing this problem.
I have an MSI laptop, with a Geforce Go 6100 video card.
I also have to mention that I used Kubuntu 6.06 before(now I have Ubuntu 7.04) and had no such problem.
Thanks.

I have the same problem. I think it's just a loading thing. I tried removing quiet splash and it's a lot smoother and i only get about .5 seconds of vertical lines, which is enough to live with. I have witnessed this on 2 laptops while coming out of hibernate.

---

