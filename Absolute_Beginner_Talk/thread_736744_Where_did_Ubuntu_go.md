---
title: "Where did Ubuntu go?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by CloudFX on 2008-03-26
Hi there
I'm running Ubuntu 7.10, on a stock Dell Inspiron 1521, dual booting Vista.  I just reformatted it, and now when my computer loads, it loads directly into Vista, instead of allowing me to choose an operating system like it regularly did.  What can I do to load Ubuntu?  I know that it's still there because when I load the Live CD, I can see my Ubuntu Partition, and access the files.  My BIOS version is A02.

Thanks, CloudFX

---

### Post by jken146 on 2008-03-26
If you just reinstalled Windows, you need to reinstall GRUB.  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Joeb454 on 2008-03-26
Sounds like you need that link **jken146** posted, if you reinstall Windows, you have to reinstall GRUB, it's annoying, but not the end of the world, it's pretty easy to do :)

---

### Post by kbless7 on 2008-03-26
Also after you reinstall grub, the menu most likely won't have an option to boot into vista. You just have to add that into your boot list then (/boot/grub/menu.lst)

---

### Post by woaiwojia on 2008-03-26
If you just reinstalled Windows, you need to reinstall GRUB

---

### Post by CloudFX on 2008-03-26
That makes sense.  Thanks guys.

---

### Post by Joeb454 on 2008-03-26
> **kbless7 said:**
> Also after you reinstall grub, the menu most likely won't have an option to boot into vista. You just have to add that into your boot list then (/boot/grub/menu.lst)

Actually when I reinstalled GRUB, it automagically added Vista back into my menu.lst :) I was actually very surprised that it had anyway, I'd made backups of it just in case it didn't :p

---

### Post by talsemgeest on 2008-03-27
Yeah, when you reinstall the grub it keeps your old menu.lst

---

### Post by marckie on 2008-03-27
> **talsemgeest said:**
> Yeah, when you reinstall the grub it keeps your old menu.lst

Yeah it really does.. had a problem like this before... though at first i opted to use EasyBCD as I am using Vista...

---

