---
title: "kernel update and wifi problem"
date: 2013-05-13
forum: Any Other OS
---

### Post by monkeybrain2012 on 2013-05-13
Recently had a kernel update to 3.8.1 on Debian sid and wifi stopped working at home (WEP encryption, don't ask me why, I rent and someone else set up the router) on my main laptop.  But it works in the coffee shop next door (which use WAP/WAP3 encryption) so it is not my wifi card's problem (uses ath5k)  Before the upgrade kernel 3.2 works everywhere and it still does.

I grab a kernel from Ubuntu's mainline, it works for Ubuntu (the same machine), but not on Debian (again only not at home, but works in coffee shop)

I thought maybe the Debian install is missing some firmware needed for the router but this is the real strange thing, I booted the Debian install (it lives on an external harddrive) off my friend's machine, same kernel but different wifi card and it works (some intel card which requires installing  iwlfifi to get it to work) I installed kernel 3.9 from Ubuntu's mainline ppa on Debian and boot it off my friend's machine again it works, but when booted into mine wifi stops working again (same kernel works for Ubuntu on same machine) So I reinstall the same kernel (3.9 from mainline) on Debian when booted into my machine, it still doesn't work.


So it seems that it is not that the wifi card is not supported (works with Debian in coffee shop, works with Ubuntu everywhere and all kernel versions), and it is not the router (works in my friend's machine for same hot spot) So what can the problem be? How can I begin to troubleshot?

---

### Post by monkeybrain2012 on 2013-05-18
bump!

---

