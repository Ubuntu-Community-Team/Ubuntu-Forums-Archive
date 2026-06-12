---
title: "SRST failed - i cant install ubuntu in my imac"
date: 2008-08-27
forum: Apple Hardware Users
---

### Post by Applinux on 2008-08-27
I am trying to install ubuntu in my imac, but when i click on "install" or when i choose "try ubuntu without any change to your computer" all i get on both options is the following error:

(initramfs) [179.327060] ata3: SRST failed (errno=-16) 

What does it mean? I have no idea what that error means :confused: Will i be able to install ubuntu as i want on my imac? please help me! ; )

ps. i dont know if this is too important but if it is relevant because graphics card or ram, my imac is the latest intel imac, 3.06 ghz, 4 Ghz ram, 1TB HD, NVIDIA GeForce 8800 GS with 512MB memory.

any ideas or tips highly appreciated! :wink:

---

### Post by cyberdork33 on 2008-08-27
did you run a check on the disc? The option is available at the boot menu.

---

### Post by Applinux on 2008-08-27
Cyberdork33, the cd is okay - i even used it as a test to install ubuntu on a macbook pro, but on the imac that i want to use with ubuntu, as i said unfortunately : ( is only showing that error, any other tips or ideas ? ; )

---

### Post by cyberdork33 on 2008-08-28
> **Applinux said:**
> Cyberdork33, the cd is okay - i even used it as a test to install ubuntu on a macbook pro, but on the imac that i want to use with ubuntu, as i said unfortunately : ( is only showing that error, any other tips or ideas ? ; )
Well, I am guessing that you replaced the Hard Drive in your iMac (since it is 1TB). I think that drive is the issue. There is a recent bug on this:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/220706](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/220706)

I would first make sure that no USB block devices are connected on bootup (iPods, thumbdrives, etc). Since your internal drive is SATA, you cannot switch it between master / slave / cable select so that solution is out of the question. I would try using 'irqpoll' as suggested in the bug report. This can be done on the Live CD by hitting one of the suggested F-keys (F6?). It will show the kernel line at the bottom and you can add 'irqpoll' to the end.

---

