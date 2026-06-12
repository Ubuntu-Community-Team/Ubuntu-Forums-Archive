---
title: "Re: dpkg interrupted"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by kenono on 2007-10-31
I'm having trouble with this too, I'm new to Linux and I had to stop the terminal when it was installing the sun-java6.
Now when I try to install it again again I get the " dpkg was interrupted, you must manually run 'dpkg --configure -a'
The problem is it won't let me, even though I'm the administrator, it tells me I need "superuser privilege"

Could anyone help me out please :)

---

### Post by aysiu on 2007-10-31
The command should be ```
sudo dpkg --configure -a
```

---

