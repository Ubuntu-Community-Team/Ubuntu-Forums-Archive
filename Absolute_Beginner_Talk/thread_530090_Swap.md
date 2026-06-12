---
title: "Swap"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Armman on 2007-08-20
All right I just have a few questions about swap, When using the guided installation how does it configure a swap partition?  And having 3gigs of ram, how large should I make the swap partition? And lastly, what is swap used for? Performance? Moving around files? Virtual Ram? I know its a lot so if you know the answer to any of them that would be great, thanks.

---

### Post by hyper_ch on 2007-08-20
If you want to use the hibernate function your swap should be at least equal the size of the ram...

---

### Post by heimo on 2007-08-20
> **Armman said:**
> All right I just have a few questions about swap, When using the guided installation how does it configure a swap partition?  And having 3gigs of ram, how large should I make the swap partition? And lastly, what is swap used for? Performance? Moving around files? Virtual Ram? I know its a lot so if you know the answer to any of them that would be great, thanks.

I don't know the formula for calculating how much installer will reserve for swap. I happen to also have 3GB of RAM and I've 1GB swap, which works fine. I think larger isn't needed, as it'd be horrible if my system ever wanter to swap even whole 1GB. However I'm not sure if larger swap is needed for some power saving states, like hibernate. Swap is usually used for extension of your RAM, if you run out of physical RAM, or just to swap less used stuff from memory so that it can be used more efficiently for programs which are in active use, or for disk buffers (improving performance).

EDIT: Ah, [hyper_ch]("http://ubuntuforums.org/member.php?u=122588") answered question about hibernate. That sound logical, as I believe hibernate puts your stuff to swap, so if you want to hibernate, you'd probably want same amount or a bit more than your RAM.

---

