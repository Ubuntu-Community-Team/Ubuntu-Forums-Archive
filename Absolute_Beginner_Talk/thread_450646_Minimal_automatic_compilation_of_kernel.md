---
title: "Minimal automatic compilation of kernel?"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Ziriax on 2007-05-21
I'm completely new to Linux/Ubuntu, but have 25 years of experience with Windows, Amiga, etc... I'm giving Feisty a shot on my laptop, and overall I'm very impressed.

But, as other users have complained about, it boots very slowly on my Dell C840 laptop.

Now, I can compile the kernel, but I manually have to select which devices I want. Basically I want to boot once, have the system record  all my onboard unremovable devices, and then optimize the kernel so it does not have to check all these again at the next boot.

Is this possible?

---

### Post by ruy_lopez on 2007-05-21
Your system only uses the kernel modules it needs, the rest remain on-disk. So if you want to gain a performance boost by compiling your own kernel, it doesn't matter about the unused kernel modules. You'll get the performance boost just by compiling because it builds the kernel optimised for your hardware. I just use the config that's in the boot directory. The difference between that and going through all the options in xconfig is negligible. The main thing is doing the compile, instead of relying on the one that came with the distro.

---

