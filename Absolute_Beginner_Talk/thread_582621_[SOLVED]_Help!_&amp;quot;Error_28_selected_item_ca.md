---
title: "[SOLVED] Help! &amp;quot;Error 28: selected item cannot fit into memory&amp;quot;"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by pluisr on 2007-10-20
I have both systems in my machine Ubuntu7.04 and WinXP (Only cause I have to)

I recently installed an encryption software(Safe Guard Easy) for WinXP on my HD, before that installation everything worked fine, but now when I choose Ubuntu on GRUB, it says: "Error 28: selected item cannot fit into memory"

Can anyone help me fix this?

I need to make it work, Ubuntu, WinXP encrypted, is it possible?

*Note: Safe Guard changes the MBR

Thanks!

---

### Post by Arthur Archnix on 2007-10-20
Euch... safegaurd should get its dirty little paws off your MBR. Dmcrypt-lucks works, create an encrypted partition in ubuntu and then you can open it in windows with another program that can read dmcrypt partitions. A simpler solution is truecrypt. You'll find plenty of info on both on the forums.

---

### Post by pluisr on 2007-10-27
Thanks I already fix this by installing Encrypted Ubuntu with the alternate CD. I guess there was no choice for using XP encripted with SGE :confused:

---

