---
title: "[SOLVED] not able to log in ubuntu!!!"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by codec_123 on 2007-07-21
hi ppl.. am a newbie.. i had installed ubuntu in my system and later upgraded my windows with windows xp..now am not able to find ubuntu..i need to work in ubuntu..how to access it..kindly help..thanks

---

### Post by lisati on 2007-07-21
It is possible that Windows "re-worked" the boot process. If you're lucky, Ubuntu will still be on its own partition. Are you able to check this?

---

### Post by Mornedhel on 2007-07-21
Windows usually rewrites the MBR from scratch, and only includes other MS OSes. Ubuntu is most likely still there. You only need to reinstall GRUB (
unfortunately, I never did this and have no idea how to proceed).

---

### Post by nitro_n2o on 2007-07-21
This page helps you restoring GRUB [http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/) unless your accidentally deleted your ubuntu partitions
use the liveCD to do this

---

### Post by antoz on 2007-07-21
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) 

this link gives a lot of information about Grub

---

### Post by codec_123 on 2007-07-21
hi
if i type the commands in the above link.that is..first i typed "sudo grub"..i got a grub command prompt..then if i type the rest of the commands .it s saying "unrecognized command"..how to proceed.pl help

---

### Post by por100pre1 on 2007-07-21
You can also use Easy BCD to add Ubuntu to your Windows bootloader.

---

### Post by bodhi.zazen on 2007-07-21
See this link :
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

You can also try supergrub : [http://supergrub.forjamari.linex.org](http://supergrub.forjamari.linex.org)

---

### Post by codec_123 on 2007-07-21
thanks a lot to all the above who hav replied!!!

---

