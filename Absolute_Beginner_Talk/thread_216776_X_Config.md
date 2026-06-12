---
title: "X Config?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Lethrom on 2006-07-16
Hello all!

I'm brand new to Linux in general, so I decided to try Ubuntu as a starter OS because a friend recommended it. So I install it with the help of the aformentioned friend. When I start it up using the boot loader it goes to the normal loading screen, then when it's done, the screen just becomes white with a few other bright colors. When I asked my friend about this, he said I needed to configure xwindows (I believe this was the file). So basically I'm asking if xwindows is what I need to config, and how. Or if I need to do something else. Thanks!

-Lethrom

---

### Post by GuitarHero on 2006-07-16
Does it boot into ubuntu?  Does it give you a prompt.  You can configure your xserver with 

dpkg-reconfigure xserver-xorg

this allows you to select drivers, resolutions, etc.

---

### Post by aysiu on 2006-07-16
Shouldn't the command be this? ```
**sudo** dpkg-reconfigure xserver-xorg
```

---

