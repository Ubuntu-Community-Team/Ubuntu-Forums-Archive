---
title: "Dell 4600 Sound"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by transdink on 2007-06-30
Have been running Feisty for several weeks.  My Dell 4600 has a Soundblaster Card the is not compatible with Linux, However, there is also an Intel chipset on the mother board which works fine.  When ever I boot up Ubuntu, it is a 50/50 chance which sound system loads, so I have to boot up several times to get the right one.  How can I lock the Intel system in Ubuntu to boot up every time???

---

### Post by Computer-Geek on 2007-07-01
You better remove Soundblaster card from ur motherboard when u boot LINUX or may be u can somehow power off Sound Blaster Sound Card. I'm also a newbie so i can tell u this only.

Thanks!

---

### Post by cotcot on 2007-07-01
Search how to edit /etc/modules.d/alsa-base. I think there you can edit the file in order to disable the Soundblaster without removing the card physically.

---

