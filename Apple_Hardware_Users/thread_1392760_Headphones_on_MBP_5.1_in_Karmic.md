---
title: "Headphones on MBP 5.1 in Karmic"
date: 2010-01-28
forum: Apple Hardware Users
---

### Post by Aybara on 2010-01-28
When I plug in my headphones Karmic doesn´t detect it. Sound is still playing on the internal speakers. I believe this is a known issue, but haven`t found the workaround/fix for it. Anyone know?

---

### Post by linuxopjemac on 2010-01-28
```
alsamixer
```

then unmute with "m" the channel responsible...

---

### Post by Aybara on 2010-01-28
I´ve gotten so far, and have sound. Now the only issue is jack detection. Sound plays both on my speakers and my headphones.

---

### Post by linuxopjemac on 2010-01-28
That's a bug I can't fix for you. There is some alsa patch on the way, which should take care of this.

[http://mac.linux.be/content/upcoming-kernel-updates-apple-products](http://mac.linux.be/content/upcoming-kernel-updates-apple-products)

[http://ubuntuforums.org/showthread.php?t=1379971](http://ubuntuforums.org/showthread.php?t=1379971)

---

### Post by Aybara on 2010-01-28
Ah. Great! Thanks for telling :)

---

