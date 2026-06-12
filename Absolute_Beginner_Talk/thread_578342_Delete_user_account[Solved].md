---
title: "Delete user account[Solved]"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2007-10-17
Would someone be kind enough to show me how to delete a user account please. Thanks in advance.

---

### Post by expatCM on 2007-10-17
System / Administration / Users and Groups
highlight the user
click on Delete

---

### Post by oscarthefish on 2007-10-17
Thanks for the help expatCM

---

### Post by LowSky on 2007-10-17
how do you delete their files that it leaves in /home?

---

### Post by Dr Small on 2007-10-17
> **LowSky said:**
> how do you delete their files that it leaves in /home?
```
sudo rm -R /home/<username>
```

---

### Post by LowSky on 2007-10-17
> **Dr Small said:**
> ```
sudo rm -R /home/<username>
```

thanks Dr Small.. worked like a charm

I fgured others may ask as deleting a user's account doesn't delte their files.

---

