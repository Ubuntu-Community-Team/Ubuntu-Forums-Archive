---
title: "How to Remove a Driver"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by reslider on 2007-08-03
Im trying to install my wireless card, When I tried to install it the first time I didn't have the right .sys file in. So Now it doesn't recognise my wireless card.

When I try to install it, it tells me its already installed, So I want to remove the driver and re-install with the correct .sys file.

Thanks, tyler

---

### Post by dca on 2007-08-03
sudo ndiswrapper -r
 
ndiswrapper -help

---

### Post by reslider on 2007-08-03
simple enough, thanks for the help

---

