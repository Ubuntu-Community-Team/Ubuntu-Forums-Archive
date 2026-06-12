---
title: "problem with nm-applet"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by StephUb on 2007-12-03
Hi there,

I am pretty new to ubuntu.
I have Gusty on my laptop with integrated wireless and was wondering were i can find the status of the connection and found that nm-applet should do it.

Well, it doesn't

I have the two ugly screen right now whereas i am connected to my wireless router.
If i clic on it i have just unclicked wired network and manual configuration appearing.

So what is wrong here or what i did wrong?
Most importantly what can i do to have ot worked as i have seen on screenshots?

Thanks

---

### Post by x64Jimbo on 2007-12-03
Have you made sure to remove your interfaces' names from the /etc/network/interfaces file? If your interfaces are listed in that file, nm-applet will ignore them.

---

