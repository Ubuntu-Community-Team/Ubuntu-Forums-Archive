---
title: "ubuntu 6.06 installer crashes"
date: 2009-12-22
forum: Apple Hardware Users
---

### Post by Mitch9654 on 2009-12-22
I boot up 6.06, a logo appears with text going underneath, and then the screen goes blank. I fixed it with configuring the xorg.conf file. Then, I log in, and there is a bonobo activation server problem. I found with 4.04 that I would have to ```
hwclock --set --date MM/DD/YY
hwclock --hctosys(or something like that)
```

Anyway, the GDM still works, but when I start the installer... It crashes and gives an error report...

---

