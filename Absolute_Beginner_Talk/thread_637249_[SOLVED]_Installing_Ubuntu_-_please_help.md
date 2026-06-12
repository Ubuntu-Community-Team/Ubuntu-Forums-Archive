---
title: "[SOLVED] Installing Ubuntu - please help"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by dave00001 on 2007-12-10
I'm relatively new to linux - I am running a kubuntu distribution (fiesty fawn I think) on my pc and I want to switch it to ubuntu on a fresh install.  The problem is, I can't get the grub to boot from my installation cd, or even recognize it...  

Any help would be really appreciated!

---

### Post by nikoPSK on 2007-12-10
your computer might not handle it. Even though mine with 512 RAM and a 2.0 GHz processor does not like the live cd. I would suggest the alternate.

---

### Post by dave00001 on 2007-12-10
Sorry - I should have been more specific...  I really don't know how to configure the grub or how to boot from the installation cd, I've only been reading other threads and found nothing.. What I really could use is some advice on how to boot from my iso image on my cd - and fresh installing ubuntu

Thanks again, I hope someone can help me!

---

### Post by nikoPSK on 2007-12-10
op, sorry can't help you there...:(

---

### Post by akiratheoni on 2007-12-10
> **dave00001 said:**
> Sorry - I should have been more specific...  I really don't know how to configure the grub or how to boot from the installation cd, I've only been reading other threads and found nothing.. What I really could use is some advice on how to boot from my iso image on my cd - and fresh installing ubuntu

Thanks again, I hope someone can help me!

Oh, you'll need to configure your BIOS. When you turn on your computer, there will be something that says <F2> Setup or something like that. On most computers it's F1, F2, F10, or Del or something similar. Hit that hit and you'll go into the BIOS setup, then you can explore it and set priority to a particular boot device, in which case would be your CD-ROM drive.

---

### Post by dave00001 on 2007-12-10
I've tried this, but since I'm not running windows, I only get the grub loader, and it's not as straightforward when looking at the boot order..  I think the answer has something to do with my boot/grub/menu.lst file, but I'm not exactly sure...

---

### Post by fain on 2007-12-10
The BIOS is the basic input output system. not a part of an OS such as windows or ubuntu.
It shows up when you first turn on your computer before the grub loader.

what does it say when grub starts?

---

### Post by dave00001 on 2007-12-10
Actually I didn't know there was a BIOS setup here... but I eventually got in, and the installation went great!!!   Thanks for your help!

---

### Post by thelatinist on 2007-12-10
Glad you got your help.  Be sure to mark the thread [Solved] using the thread tools.

---

