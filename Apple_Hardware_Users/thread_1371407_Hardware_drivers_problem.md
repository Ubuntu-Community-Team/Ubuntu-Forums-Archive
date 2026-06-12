---
title: "Hardware drivers problem"
date: 2010-01-03
forum: Apple Hardware Users
---

### Post by Grayer on 2010-01-03
Hi, I finally managed to install ubuntu on my iMac and it works perfeclt, when I did syste>administration>hardware drivers, the graphics card and wifi drivers came up.  The problem is in my macbook pro 5,5 I do the same thing and it says there are no drivers available...when I haven't installed anything.  What can I do to make them appear?
Thanks...

---

### Post by linuxopjemac on 2010-01-04
did you connect via a cable to the internet and update the software? It might then come.

what does the following code give you ?
```

lspci -v | grep Network
```

---

