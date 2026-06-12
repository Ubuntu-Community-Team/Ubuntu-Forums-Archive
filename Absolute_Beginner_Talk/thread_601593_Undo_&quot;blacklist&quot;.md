---
title: "Undo &quot;blacklist&quot;"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by tashmooclam on 2007-11-03
I am still fooling with wireless.
I had some wireless function, then I tried to use Ndiswrapper but I could not install it.
I did a "blacklist" of the broadcom in the terminal. Now it's not going to work either.
How does one undo "blacklist" of something in terminal?

---

### Post by nick_h on 2007-11-03
Remove the line that you added to the file /etc/modprobe.d/blacklist
```
gksudo gedit /etc/modprobe.d/blacklist
```

---

### Post by tashmooclam on 2007-11-03
Thank you for your reply to my post.
Regards
AKS

---

