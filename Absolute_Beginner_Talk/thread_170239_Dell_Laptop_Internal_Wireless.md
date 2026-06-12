---
title: "Dell Laptop Internal Wireless"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by Asherael on 2006-05-04
I've a Dell Inspiron 8500 notebook with the internal wireless card.  How do I find out what it is so I can find drivers / get it working? 

What packages might I need to use it?

PS:  Ubuntu has the most fantastic balance of the ease of the synaptic package manager and the makes-me-feel-smart-itude of the shell!

I finally feel like I'm not "settling for Linux" I'm fully functional and "kickin' tail with Linux"

---

### Post by Jagot on 2006-05-04
Have a look at this site for your model:

[http://www.linux-on-laptops.com/dell.html](http://www.linux-on-laptops.com/dell.html)

It appears you have a Broadcom chip, so you will need to use ndiswrapper in Breezy.  Ndiswrapper is available in the repositories and there are plenty of instructions around these forums to show you how to use it.

You should be able to get your drivers from Dell.com.

---

### Post by mjm115 on 2006-05-04
Most Dell laptops love the Intel PRO Wireless or Broadcom chipset for their laptops.  Most of the Intel cards work with the default install.  In the event that it isn't working, you can use ndiswrapper with the appropriate drivers to get it working

---

