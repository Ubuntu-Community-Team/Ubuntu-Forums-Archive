---
title: "Macbook Pro 8 3 Precise 12.04 Video Issues"
date: 2012-09-09
forum: Apple Hardware Users
---

### Post by zmbmartin on 2012-09-09
Hey all,

I have scoured and read everything that I can find on this but can't seem to find a solution. I have a Macbook Pro 8 3 and can only get fbdev driver to work which gives me poor quality video. Here is some output:

[https://gist.github.com/3687747](https://gist.github.com/3687747)

Not sure what else to show. I tried installing the proprietary fglrx drivers and then X would not start. Anyone that can give me some insight on this would be great.

Thanks

On another note suspend also does not seem to be working for me if you have any thoughts on that.

---

### Post by zmbmartin on 2012-09-20
No one else has the same problem or any solution ideas?

Thanks

---

### Post by proycon on 2012-09-23
It seems you're booting in EFI mode rather than BIOS-compability mode? I didn't yet get the radeon card to work there. The built-in intel card should work in EFI-mode though though. Perhaps you need some extra boot parameters in your grub.cfg or you need to clear your xorg.conf? See [http://ubuntuforums.org/showthread.php?t=2061791](http://ubuntuforums.org/showthread.php?t=2061791)

---

