---
title: "how will i know if my ati drivers installed"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by pcexpert2 on 2007-09-16
i have a radeon x1300 videocard

---

### Post by splintercellguy on 2007-09-16
What drivers did you install? To determine if you are using a proprietary driver and not the open-source one, type:

glxinfo | grep vendor

If the vendor is ATI Technologies, then you are using some form of restricted driver.

---

### Post by pacsum on 2007-09-16
on  a terminal type 
> fglrxinfo
and probably you will see this
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6747 (8.40.4)

If it doesn't says ATI Technologies then it's not correctly installed.

---

