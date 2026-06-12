---
title: "Ubuntu 9.10 hangs on IMac 27&quot; I7"
date: 2010-04-24
forum: Apple Hardware Users
---

### Post by kenoma on 2010-04-24
Hi, everybody,

I installed 9.10 and the graphic driver for the ATI video card.
After reboot all was ok.
Then I run a system update, it found almost 250 packages to update.
After installation, rebooted machine and it hangs on boot.
Any idea to discover what goes wrong.

Thanks.

Maurizio

---

### Post by jisaac on 2010-04-24
I had a similar problem. It was a very strange behavior because I don't know how I've solved it.

1) Try to boot on OSX then shutdown. Now try to boot Ubuntu again.
2) If 1) did not work, try to boot in a secure mode (when grub menu appears). At prompt, after login in text mode, try: startx

If the gnome session opens correctly try to reboot in a normal mode...

PS: I'm running 9.10 (full updated + ATI proprietary drivers) on an iMac 27" i7 too.

---

