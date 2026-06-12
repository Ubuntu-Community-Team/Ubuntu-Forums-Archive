---
title: "Random freeze at boot with two loading bars"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by KIAaze on 2007-11-15
I'm currently experiencing some strange problems with my PC:

1)CD drive suddenly doesn't open anymore. Have to use a paper clip to open it. -> probably hardware problem since it's the same in Windows

2)When I boot into Ubuntu, the loading bar sometimes suddenly stops and a second similar one appears underneath it. The boot process stops completely and I have to press the power key to force reboot.
Usually, it works after a second reboot.

Has anybody had a similar problem?

How can I disable the loading bar to see the command-line output?
Is there a log file showing what happened at a previous boot attempt?

---

### Post by overdrank on 2007-11-15
> **KIAaze said:**
> I'm currently experiencing some strange problems with my PC:

1)CD drive suddenly doesn't open anymore. Have to use a paper clip to open it. -> probably hardware problem since it's the same in Windows

2)When I boot into Ubuntu, the loading bar sometimes suddenly stops and a second similar one appears underneath it. The boot process stops completely and I have to press the power key to force reboot.
Usually, it works after a second reboot.

Has anybody had a similar problem?

How can I disable the loading bar to see the command-line output?
Is there a log file showing what happened at a previous boot attempt?

To remove the splash, You can try and press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and then hit enter and then  b to boot. Hope this helps. Good luck!

---

### Post by KIAaze on 2007-11-15
Thanks. :)
I edited the /boot/grub/menu.lst file. That should do it.
Since the freeze is random, it's better that way.

---

