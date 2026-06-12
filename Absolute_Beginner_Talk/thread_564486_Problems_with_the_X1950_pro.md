---
title: "Problems with the X1950 pro?"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Simplechat on 2007-10-01
hey, i'm fairly new to ubuntu, i have an X1950pro with 256mb of ram on Pcie (ATI).

I've installed envy and ran it, and that then set up the restricted drivers for it, however i am having two problems:

1) No desktop effects. (not a major one, but still odd considering that its a fairly nice card on windows).

2) Unplayable on everything. (something between one fps and maybe 5). 

Have i missed a step in configuration?

---

### Post by elliotjreed on 2007-10-01
Try:

```
dpkg-reconfigure xserver-xorg
```

Select your driver, etc. 

It worked for me! By make a backup of your xorg.cpnf file first!

---

