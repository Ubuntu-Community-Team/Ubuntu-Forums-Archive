---
title: "[SOLVED] Grub vga options no longer work in Gutsy Gibbon"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-10-19
With Feisty Fawn, I added vga=0x317 aka vga=794 onto the Linux boot options in /boot/grub/menu.lst so that the console was in 1024.x768.  Now in Gutsy Gibbon I'm unable to get anything higher than the default 640x480.  If I choose higher resolution options, the screen is basically blank.

---

### Post by aegnor on 2007-10-19
yes, i habe the same problem :(

---

### Post by robodesign on 2007-10-20
I have the same problem.

For Feisty I configured my kernel parameters by removing the splash and the 'quiet' parameter (I like to see all the info). Also, I added vga=792, because I wanted a higher resolution for the consoles. Additionally, I removed the 'usplash' package.

In Gutsy, vga=792 no longer works. Anyone knows why? I tried other vga values which should work with my monitor. Nothing works - I always get the black screen.

---

### Post by aegnor on 2007-10-20
yes. it seems than the framebuffer modules are disabled by default in gutsy due instability.
i never had problems with this. but it seems than the hint in this thread doesn't help me.
[http://ubuntuforums.org/showthread.php?t=258484&highlight=framebuffer+gutsy&page=6](http://ubuntuforums.org/showthread.php?t=258484&highlight=framebuffer+gutsy&page=6)

---

### Post by Cyrus XIII on 2007-10-20
Yes, this fix ceased working with a newer Kernel revision. I wonder, if this is broken by design, why is there still an open bug (marked critical no less) on Launchpad?

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910)

---

### Post by dietrying on 2007-10-20
this is really annoying- because of this bug i'm not able to get ANY Console by using STRG+ALT+ F1-F11.......wich is unacceptable....is there any workaround?

---

### Post by kurbacik on 2007-10-20
Here is a fix from half way through the previous link: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910)

1. Add fbcon to /etc/initramfs-tools/modules
2. Update initrd.img
3. Restart

$ sudo sh -c "echo 'fbcon' >>/etc/initramfs-tools/modules"
$ sudo update-initramfs -u

The same solution is given here:

[http://ubuntuforums.org/showthread.php?t=454392&page=3](http://ubuntuforums.org/showthread.php?t=454392&page=3)

---

### Post by vbgunz on 2007-10-24
feel free to read the thread here but this link goes directly to the answer that solved this problem for me better than I had anticipated. [http://kubuntuforums.net/forums/index.php?topic=3087749.msg94991#msg94991](http://kubuntuforums.net/forums/index.php?topic=3087749.msg94991#msg94991)
good luck!

---

### Post by Takis on 2007-10-24
> **vbgunz said:**
> feel free to read the thread here but this link goes directly to the answer that solved this problem for me better than I had anticipated. [http://kubuntuforums.net/forums/index.php?topic=3087749.msg94991#msg94991](http://kubuntuforums.net/forums/index.php?topic=3087749.msg94991#msg94991)
good luck!

Worked perfectly for me, thanks!

---

### Post by AncientPC on 2007-10-26
These [instructions]("http://ubuntuforums.org/showpost.php?p=3486541&postcount=30") did not work for me, but [these]("http://kubuntuforums.net/forums/index.php?topic=3087749.msg94991#msg94991") did.

The only difference between the two was the 2nd one enabled vga16fb in addition.

---

