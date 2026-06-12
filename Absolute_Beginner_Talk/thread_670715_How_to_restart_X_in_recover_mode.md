---
title: "How to restart X in recover mode?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by dswhite85 on 2008-01-17
I have Ubuntu 7.10, and I had an invidia graphics card in it until it got damaged, and i took it out and now i want to run ubuntu with my on-board graphics for a while until i can afford a new card. Only trouble is, ubuntu won't start up when I have it using my on-board graphics. As it starts up, it halts and the last message it displays is "*Running local boot scripts (etc/rc.local)   [OK]"
I was told to fix it, I need to restart X in recovery mode. So how do I do that? Thanks in advance!

---

### Post by Hospadar on 2008-01-17
when you're in that initial grub menu while the computer is booting, you need to go to the second option (I think it says recovery mode) your grub menu may be auto-hidden, if so, you'll see a little prompt that's like "press any key to enter grub menu... 3 (2, 1)" and if you hit something then it'll take you to the grub menu and you can choose recovery mode.

Also if you just need to edit your xorg.conf, you could always just boot off a livecd.

---

### Post by dswhite85 on 2008-01-17
> **Hospadar said:**
> when you're in that initial grub menu while the computer is booting, you need to go to the second option (I think it says recovery mode) your grub menu may be auto-hidden, if so, you'll see a little prompt that's like "press any key to enter grub menu... 3 (2, 1)" and if you hit something then it'll take you to the grub menu and you can choose recovery mode.

Also if you just need to edit your xorg.conf, you could always just boot off a livecd.
How exactly do I reconfigure Xorg.conf on the livecd cause that is exactly what I need to do, as restarting X in recovery mode solved nothing.

---

