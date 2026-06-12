---
title: "[SOLVED] How do I take control of my external HD?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by victor9098 on 2007-07-25
Hello All,

I installed Ubuntu last week and I am loving it. I am still completely lost when it comes to using terminal commands...GUIbuntu anyone? ;)

Anyway, have a problem with my external HD. I used it with my previous OS for my music, video, back-up collections and anything I did not need to keep on the laptop. Now I am no longer free to use it, root is the only owner and group allowed to access it!

Is there any way for me to have it as accessible as my "Home" folder??

Thank you.

---

### Post by logos34 on 2007-07-25
**sudo chown -R username:username /media/disk**

replace 'username' and 'disk' with yours

---

