---
title: "Bricked MacBook Pro 3.1 with 11.04 Ubuntu"
date: 2011-08-22
forum: Apple Hardware Users
---

### Post by Paperfish on 2011-08-22
In the past I haven't had much luck with installing versions of Ubuntu, there's always been something missing. This time round, 11.04 seemed like it'd fit the bill.

I installed it in the correct way and everything was working fine over several reboots. Then I noticed that my wifi password was contained in the default keychain. For some gnome reason this meant I had to enter in the default keychain password everytime it wanted to connect to my wifi.

In looking how to disable/move this password to another keychain, or removed the keychain itself I read on some random forum that I could un-tick some keychain-related gnome tickboxes in a login options menu.

After rebooting the machine, I just get a black screen. It makes the MacBook "bong" when starting up, but holding the option key does nothing, although it does make the Ubuntu disk spin differently... I don't have access to a spare keyboard or anything. My MacBook is it.

I'm frustrated and saddened by this so if anyone could help it'd be hugely appreciated.

---

### Post by metatechbe on 2011-08-22
You are most likely hitting this well-known bug :
[https://bugs.launchpad.net/efibootmgr/+bug/774089](https://bugs.launchpad.net/efibootmgr/+bug/774089)
You can try to reinstall your firmware (see instructions in thread).

---

### Post by LinuxBill on 2012-01-27
Regarding this post this happened to me with my old Macbook. Rather disappointing but my fault for not checking about such bugs. Has this been ironed out in 11.10 and there have not been any other horror stories..?

Thanks
Bill

---

