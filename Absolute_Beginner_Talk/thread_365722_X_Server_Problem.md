---
title: "X Server Problem"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by ravikumar on 2007-02-20
Hi,

I am facing a strange problem...I installed ubuntu dapper in my dell m/c...Every thing works fine..But when i log out..then it goes to blank screen...same problem with fedora core 2. 

looking forward useful help...thanks.

---

### Post by PartisanEntity on 2007-02-20
If you have an nvidia graphics card try installing the latest driver (version 9746).

I had a similar problem, my screen would turn off completely, **not** when I logged out, but whenever I shut down the X server. This too was on dapper on an Asus laptop. When I upgraded to the latest nvidia drivers this problem went away.

Perhaps this might help you too.

---

### Post by 3rdalbum on 2007-02-20
Do you, by any chance, have an ATI graphics card?

The version of the ATI driver that "shipped" in the Dapper repositories has a nasty bug that causes the machine to freeze on logout or on switching to a virtual terminal. This is only present on some cards.

Try installing the latest ATI driver from the ATI website.

If you don't have an ATI graphics card, ignore this post.

---

