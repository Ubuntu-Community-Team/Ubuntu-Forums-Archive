---
title: "Add on CD problems"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by Daneel42 on 2006-10-03
I have 56k internet right now so if at all possible I like to install programs via cd. I tried to use a ubunu add on cd that I downloaded and my power cut off in the middle of the install. Now whenever I try to complete it it says that dpkg was interrupted and that I need to run dpkg --configure -a to fix the problem. I have not been able to find this program nor do I know how to run it if I do.

---

### Post by jISh on 2006-10-03
Run that command in a terminal. Applications -> Accessories -> Terminal. You'll need sudo for it, so:
```
sudo dpkg --configure -a
```

---

### Post by Daneel42 on 2006-10-04
Thanks

---

