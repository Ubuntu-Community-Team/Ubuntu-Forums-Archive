---
title: "Wireless Card is not being recognized in my Network Manager"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by climbjm on 2006-12-14
I have a D-Link DWL-G630 wireless card for my laptop.
When I was running Xubuntu Dapper, it recognized my card and I was able to connect just fine.
I then Installed Edgy Eft and it does not detect my card at all.

Any thoughts or ideas?

---

### Post by Henry Rayker on 2006-12-14
One thing I should point out is that Edgy's wireless support, for certain cards, seems to have degraded.

---

### Post by climbjm on 2006-12-14
Is there something I could try typing in the shell to see if xubuntu could detect it?
I have tried... ```
sudo /etc/init.d/networking restart 
```but that seems to not help.

---

### Post by Grim_n_Evil on 2006-12-24
Same problem with the exact same card. It was working fine under Dapper. It would be a shame to have to go back to Dapper only because of that.

---

### Post by hilltop_yodeler on 2007-01-27
I am running the same card (D-Link AirPlus DWL-G630) in Xubuntu - Edgy 6.10 on a Dell Inspiron 4150 (also successfully using the same card on an even older Dell Inspiron at work, which is also running Xubuntu 6.10).  No problems at all.  When I plug in the card, the OS detects it and usually will automatically establish connectivity.  The only issue that I have is that on occasion, if I had been previously connected via ethernet, then disconnect and insert my D-Link card, the card will be detected but no connectivity takes place; the easy fix is to take down eth0 and bring up ath0 manually.  The command I use to renew the ip is:
# sudo iwconfig ifdown ath0 && ifup ath0

However, I do also have a Belkin F5D7010 wireless-g card and the OS will NOT detect the card at all.  This card has worked fine for me with in the past in other flavors of Linux, but not in Xubuntu 6.10.  The D-Link card works great though.  Not sure why you would be having difficulties.  My understanding is that Xubuntu and Ubuntu are the same at the base OS level. 

Let me know if you want to look at any particular config files and I'll post them.  Good luck.

---

### Post by hilltop_yodeler on 2007-02-21
Here's something interesting.....
Recently, I used a colleague's D-Link card (DWL-G630) and found that my machine could not detect the card.  This was confusing since my wireless card is the exact same model.  ...Well, as it turns out, it's the same model, but it is an older version and is not supported by Ubuntu.  If you look at the back of the card, you will see a reference to A1, C1, C2, or possibly something else.  His card is an A1, which is an older model.  Mine is the C2, which is newer.  I've got two of the C2 cards and they both work great.  In order to use his A1 card, we had to use ndiswrapper -- works fine with ndiswrapper.

---

