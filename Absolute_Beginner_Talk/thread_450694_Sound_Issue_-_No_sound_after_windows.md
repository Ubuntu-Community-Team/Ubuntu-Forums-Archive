---
title: "Sound Issue - No sound after windows"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Acglaphotis on 2007-05-21
Hi

I have some issues with sound. Every time i reboot/shutdown/hibernate or anything from windows (vista)  and then i boot back to Ubuntu i don't have sound. Not even a restart will fix it, the only way to fix it is to enter the Dapper (Yes. Dapper, not feisty) live cd, let it boot, and then boot back to Feisty. 

I have an:

Hp pavilion dv2000 series. (DV2225nr)
Amd 64 x2 (dual core)
Nvidia Geforce Go 6150 (288mb shared video memory)
**MCP51 NVIDIA Sound Card**
120 gb hd.

Any help would be appreciated.

-Acgla

---

### Post by Acglaphotis on 2007-05-21
*bump* (Drowned by a lot of posts)

---

### Post by Dan334477 on 2007-05-22
I have the exact same problem and don't know what's causing it (Linux n00b here), but I found a workaround if you haven't seen it yet:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108392](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108392)

Essentially, boot up from the battery and not the power adapter.  After you boot up, sound should work (it did for me, at least).  You can plug the power adapter back in once the machine boots up from the battery.

Hope this works for you at least until a true fix is found.

Edit: PS - it doesn't work if you do a restart.  Do a full boot up from shut down.

---

### Post by lexarrow on 2007-05-26
check out this [howto]("http://ubuntuforums.org/showthread.php?t=455147").maybe it can help

---

### Post by lchiner on 2008-03-25
Many thanks for the solution, I was almost resigned to work without sound and looks really a surrealist solution but it works.

---

