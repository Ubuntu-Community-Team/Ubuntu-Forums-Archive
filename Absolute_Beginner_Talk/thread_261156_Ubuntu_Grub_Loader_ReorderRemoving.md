---
title: "Ubuntu Grub Loader Reorder/Removing"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by Viral on 2006-09-19
Hello!

I've just recently decided that I'd like to have the GRUB Loader have my Operating Systems in a different order.

I have like, 6 options on the list, and I only want 3. :P

Ubuntu, Safe Mode Ubuntu, and Windows XP

How do I remove?

And I also wanted to make it so when GRUB Loader comes up, the default option (highlighted option) is Windows XP, so it will boot WinXP automatically, if I don't press a key.

Thanks!

---

### Post by confused57 on 2006-09-19
Here's how to set the default OS to boot:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

Also, you can comment out any kernels you don't want displayed by placing a # in front of the line(s) in your menu.lst.  You might want to display the next oldest kernel, in case you're not able to boot the latest.

---

