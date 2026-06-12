---
title: "Dpkg help!"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by warbux on 2006-03-14
Guys, before I went to work the little update icon came up...so i went thru downloading everything...anyways i just let it run, i saw that it was still hung up on compiling the new kernel but the little light bulb was up telling me to reboot, so i did.

anyways, anytime i try to get new stuff from the repostitories im getting and error and it tells me to run dpkg --configure -a..at 6 pm PST I ran that command..and 4 hours later in the terminal it is still at the same spot..should I be concerned? Did I mess up my system? Nothing seems broken..I am so lost here guys. Here is my progress
```
dpkg --configure -a
Setting up linux-image-2.6.12-10-386 (2.6.12-10.30) ...

```

---

### Post by chimera on 2006-03-14
```

man dpkg

```
:mrgreen: 

btw, shouldn't you run

```

dpkg -i

```

instead of -a?

---

