---
title: "Can't see my new dard hd that i Gparted"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by jpates20 on 2008-02-20
I just Gparted a new hd every thing was working for a while, but now i can see but can't use it, error: could not execute pmount.....thanks

---

### Post by jpates20 on 2008-02-20
I just Gparted a new hd every thing was working for a while, but now i can see it, but can't use it, error: could not execute pmount.....thanks

---

### Post by PmDematagoda on 2008-02-20
Please do not start duplicate threads since it is not allowed on Ubuntu Forums, if you want help on an issue then one single thread on that particular issue would suffice.

---

### Post by Duck2006 on 2008-02-20
What is the error?

---

### Post by Therion on 2008-02-20
Try adding yourself to the plugdev group:

```
sudo adduser <your_username> plugdev
``` Then log out, log back in and try it again.

---

