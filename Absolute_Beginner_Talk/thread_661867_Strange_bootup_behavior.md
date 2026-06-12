---
title: "Strange bootup behavior"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by elaich on 2008-01-08
7.04 - about halfway through the process, Ubuntu changes into verbose mode, and I see the message "There are differences between the boot sector and it's backup."

Ubuntu finishes booting just fine, but I was wondering why this happens. I also see one "fail" but it flashes by too fast to read.

---

### Post by chuckyp on 2008-01-08
dmesg should show you what you where missing during the boot.  Also dmesg -c will clear the log so you can reboot and get a fresh one.  Try in a terminal
```

$ dmesg | more

```
or
```

$ dmesg | grep fail

```

---

