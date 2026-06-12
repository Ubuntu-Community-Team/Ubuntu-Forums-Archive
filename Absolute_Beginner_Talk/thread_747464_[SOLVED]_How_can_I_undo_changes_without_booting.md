---
title: "[SOLVED] How can I undo changes without booting?"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by zot171 on 2008-04-06
My initial problem was that startx wouldn't detect any screens, so it wouldn't start. Ubuntu would still run, but only on runlevel 2.

I came to the forums and found a thread that solved a similar problem, [http://ubuntuforums.org/showthread.php?t=359879](http://ubuntuforums.org/showthread.php?t=359879), and reconfigured my own xorg file. 

Unfortunately, because I got it secondhand, I do not have any documentation for the video card I am using. I just saw "NVidia GeForce 2" stamped into one of the chips and figured that was all I needed to know to configure xorg. Well, that worked out in the worst possible way: my computer seems to think that it is correctly configured and that I have a functioning GUI, but all I get is a blank screen that I have no idea what to do with. While my computer used to boot and give me a text based interface that I can use, now it tries to start the x server and I can't do anything!

I tried to do a system recovery involving <esc> during GRUB startup, but I can't even get to the recovery screen!

Can I restore my original xorg file without reinstalling Ubuntu? I used unetbootin to install Ubuntu on that HDD and then transplanted it into another machine, and I don't have the LiveCD (though I have ordered it through launchpad) so I can't very easily reinstall it until those CDs arrive.

Any suggestions?

---

### Post by arochester on 2008-04-06
Reconfigure your xserver. It easier than you think in Ubuntu. See [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760) and  [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

---

### Post by zot171 on 2008-04-06
I tried, but cannot use Ctrl+Alt+F1 to access the text command environment.

---

### Post by InfinityCircuit on 2008-04-06
Boot into single-user mode by adding "1" to the end of your kernel line in grub.

If that fails as well add break=bottom and you can just do it all from the initramfs.

---

### Post by mcduck on 2008-04-06
> **zot171 said:**
> I tried, but cannot use Ctrl+Alt+F1 to access the text command environment.

Just do it in the recovery mode (accessible from the Grub boot menu).

---

### Post by ghost_ryder35 on 2008-04-06
live cd

---

### Post by zot171 on 2008-04-06
Thanks, I used single user mode and can now use the text environment (runlevel 1). I reconfigured xorg, but I am still receiving the "Fatal Server Error: No Screens Found" message.
Do you know where I can find the settings for a GeForce 2?

---

