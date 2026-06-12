---
title: "Boot time is very slow"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by sothacom on 2007-12-19
My computer : AMD 64 2.2Ghz , 1HDD 80Gb and 1HDD 20Gb, Ram 1Gb. I'm using Ubuntu 7.1 AMD64 and boot time very slow.Why is that? And what i can do to boot time became quickly. (I hope you can understand me because my English not good)

---

### Post by kool_kat_os on 2007-12-20
how many minutes does it take?

---

### Post by tech9 on 2007-12-20
> **sothacom said:**
> My computer : AMD 64 2.2Ghz , 1HDD 80Gb and 1HDD 20Gb, Ram 1Gb. I'm using Ubuntu 7.1 AMD64 and boot time very slow.Why is that? And what i can do to boot time became quickly. (I hope you can understand me because my English not good)

install bootchart and see what's going on

```
sudo apt-get install bootchart
```

---

### Post by njparton on 2007-12-20
Uninstall compiz. That alone speeded up gnome for me immeasurably.

---

### Post by evil316 on 2007-12-20
Sometimes the problem can be the splash screen resolution.  My wife's laptop had that problem.  Is the screen blank for quite a while?  Is so press ALT F2 to show the messages during boot.  If that fixes the problem then edit your /boot/grub/menu.lst file and find the line that starts with kernel and take out the end of the line where it says quiet splash.

---

