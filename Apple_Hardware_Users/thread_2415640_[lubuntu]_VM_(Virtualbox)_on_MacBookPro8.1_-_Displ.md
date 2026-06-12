---
title: "[lubuntu] VM (Virtualbox) on MacBookPro8.1 - DisplayError"
date: 2019-03-29
forum: Apple Hardware Users
---

### Post by julian195 on 2019-03-29
Hello together, 

I,m new to unix systems!

I tried lubuntu in a vm. 
Host system is a mac with highsierra 2.7gh quadcore with 16gb ram and 500gb ssd

at the First Boot everything looks good - the system ask my for several settings- everything fine
at the Secend boot i just see stripes after the boot screen.

I my opinion the problem is caused by the graphik driver. 
is there a way to update the driver bevore the graphik interface is shown?

Any other solutions?

thanks
Julian

---

### Post by ajgreeny on 2019-03-29
In most cases the host is responsible for the graphics of a VM and if you have not enabled graphic pass-through of your graphic card, about which I know nothing, you would not normally see any problems.

If you have enabled 2D or 3D acceleration in the VM settings try disabling them and try it again; that can do strange things in some situations.

Tell us more of the graphic card in use by the host machine, and others who know more than I, may be able to help you more.

---

### Post by julian195 on 2019-03-29
solved

---

### Post by ajgreeny on 2019-03-29
> **julian195 said:**
> solved
That is not very helpful for others so can you please tell us how it was solved and then please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction.

It is a great help to other users searching the forum.

---

