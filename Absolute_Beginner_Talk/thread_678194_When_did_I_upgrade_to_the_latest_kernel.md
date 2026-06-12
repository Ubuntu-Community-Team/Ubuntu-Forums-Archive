---
title: "When did I upgrade to the latest kernel?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2008-01-25
I saw on phoronix that the 2.6.24 kernel was released yesterday, and I was going to download it today, but it seems as if I'm already running it.  Does it upgrade automatically without me telling it to?
Also: Lately I tried out PClinuxOs, and it had a couple hardware features Ubuntu doesn't have, like my scroll wheel's left/right scroll was recognized (xev reads nothing) and it fully shuts down, whereas in ubuntu it wouldn't power off the machine. Does the kernel have anything to do with this, or is it the OS?

---

### Post by Bachstelze on 2008-01-25
1) If you're running Feisty and didn't compile a new kernel yourself, you're running kernel 2.6.20. The command *uname -r* can tell you which kernel vrsion you're currently running.

2) Yes, the kernel is the most important part of the system regarding hardware detection. If your PCLOS detected more hardware than your Ubuntu, that's most probably because it runs a more recent version of the kernel.

---

### Post by Romanus81 on 2008-01-25
Sorry, I forgot to update my profile. Right now I'm running gutsy, and uname -r says I'm running the 2.6.24 kernel, but I never remember updating, or asking it to update, did it do it automatically?

---

### Post by rosegarden78 on 2008-01-25
I've seen kernel upgrades happen automatically my grub has like two or three old kernels in the menu and I didn't put them there myself - one way to get rid of it is a fresh install of Ubuntu GG I know it sounds pedantic but it's true.  I use a setup described [here]("http://ubuntuforums.org/showthread.php?t=677959") and [here]("http://ubuntuforums.org/showthread.php?t=385981").

---

### Post by Bachstelze on 2008-01-25
If you have a 2.6.24, then you're running Hardy. Gutsy has a 2.6.22 and the kernel version never changes for a given release.

---

### Post by Majorix on 2008-01-25
Wheel problem is a config issue. You can configure it to run properly in xorg.conf I think, though I have never used a mouse with side-scrolling feature so can't confirm.

The other (comp not shutting down) is I believe an issue with Ubuntu. I see it around these forums from time to time, but haven't read a fix yet.

---

