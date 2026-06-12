---
title: "x64 gusty 7.10 / support for sata raid"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by redroad55 on 2008-03-06
Hello I'm new to linux ..I just finished my x64 build ...Intel board Dq965GF with a pentium d processor has EM64t ..c1 stepping..I'm looking to 1st F6 (raid ready) I know this process in windows xp with floppy ..How is it done in linux ..how do I bring to raid readt in gusty 7.10?? Thanks any help would be appreciated:)

---

### Post by redroad55 on 2008-03-07
In 7.10 What are the possibilities for RAID or where can I go to find out???...thanks

---

### Post by njparton on 2008-03-07
Software raid (raid built into your motherboard or the cheaper PCI/PCI-E cards) may or not be supported (most likely it's not) - check out you motherboard manufacturers website for a driver.  If one doesn't exist you're out of luck.

The cheapest way to get raid in that case would be to buy something like a highpoint raid card as they have linux drivers available for most of their cards.

However if you could afford it go for hardware raid and something like a 3ware card - highly recommended.

Also search this forum for "fakeraid" for other options.

---

### Post by redroad55 on 2008-03-07
intel has a redhat driver but it is 2006 version would that work????..THANKS for your reply:)

---

### Post by njparton on 2008-03-07
It depends on which kernel it supports.

Ubuntu uses a 2.6.x kernel, the driver from 2006 may only be for 2.4.x?  Check.

You'll probably need to compile it if it does support 2.6.x.  It should come with a readme file telling you how.

---

### Post by redroad55 on 2008-03-07
This link is my board and available OS and drivers is there something here that might work??   The board has hardware raid can be configured to raid 10

---

### Post by redroad55 on 2008-03-07
oops! forgot the link [http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2372](http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2372)

---

### Post by njparton on 2008-03-07
Not that I can spot after a quick look.  You may have to purchase a cheap highpoint card or have you search for fakeraid yet?

---

