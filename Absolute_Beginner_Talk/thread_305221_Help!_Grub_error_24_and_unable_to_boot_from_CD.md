---
title: "Help! Grub error 24 and unable to boot from CD"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by jigantor on 2006-11-23
I've been running Dapper for about 6 months now without any probs. Today I tried to restart my desktop (thankfully after backing up a heap of stuff) and instead of happily loading grub I get an 'Error 24'. According to the Grub [FAQ]("http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors"), that means either a corrupt filesystem or a corrupt grub. In the hope that my entire filesys might not be wrecked, I tried to boot from the Live CD to reinstall grub. Yet even when I do that, I get either exactly the same error or (depending on which CD drive I use)
```
ISOLINUX 3.11 Debian-2006-03-16 isolinux: Image checksum error, sorry...

Boot failed: press a key to retry...
```

What's going on here? If anyone has any hints on how I might save my comp, I'd love to hear them!

Cheers,
Tim

---

### Post by phidia on 2006-11-23
Have you tried selecting rescue system from the desktop or alternative cd?
I think dapper had that option-I know edgy does.
BTW the error message you quoted seems to indicate that the cd you were using has a problem/wasn't burned correctly.

---

### Post by jigantor on 2006-11-23
My cruddy internet connection means downloading the desk/alt cd images isn't really an option for me, so I'm just running off the Dapper ShipIt CDs. And like I say, I can't get anywhere near a menu anywhere to try to rescue the system or anything. I need some way to circumvent GRUB altogether, I think.

---

