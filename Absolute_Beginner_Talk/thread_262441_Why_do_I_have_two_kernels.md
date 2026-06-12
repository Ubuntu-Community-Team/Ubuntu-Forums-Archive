---
title: "Why do I have two kernels?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2006-09-21
After I installed Ubuntu and updated, on the restart I now have two kernels (I don't know that it matters, but they're "Ubuntu, Kernel 2.6.15-27-386" and "Ubuntu, Kernel 2.6.15-26-386"). I haven't noticed that this is causing any problems and I don't expect it to but I'm curious why I have them and if one of them has an advantage over the other.

---

### Post by benuski on 2006-09-21
You have two kernels because aptitude doesn't uninstall your old kernel after updating to the new one, in case there are problems with the new one so you can have a backup.  The newest one, the one with the higher number, is the most up to date version for Ubuntu, so its probably a good idea to use that, as it has the latest bug fixes and such.

---

### Post by tylerjames on 2006-09-21
It's because there was a kernel update released a few days ago. So now GRUB will show the new kernel and the old kernel. You might be tempted to get rid of the old kernel, but sometimes that's not wise as new kernel releases can often cause conflicts or problems with various programs/hardware. Usually it's a good idea to at least keep the next oldest version kicking around in case you have to fall back to it.

Cheers


Edit: Damn benuski!! Guess I was too slow.

---

### Post by mongooseman1128 on 2006-09-21
yeah, that's what I thought it might be but was confused why the old kernel wasn't deleted. That's definitely smart of them though to not delete it automatically. Thanks for the clarification guys

---

