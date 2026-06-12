---
title: "Anyone else having this problem?"
date: 2009-04-28
forum: Apple Hardware Users
---

### Post by WA_Garrett on 2009-04-28
Has anyone else recently used the Update Manager on Hardy Heron only to restart their macbook and have no wireless? 

For me, this problem is only isolated to Ubuntu, wireless still works with OS X. I have been using the Mad Wifi drivers for wireless in Ubuntu. 

Thanks for reading.

---

### Post by cyberdork33 on 2009-04-28
> **WA_Garrett said:**
> Has anyone else recently used the Update Manager on Hardy Heron only to restart their macbook and have no wireless? 

For me, this problem is only isolated to Ubuntu, wireless still works with OS X. I have been using the Mad Wifi drivers for wireless in Ubuntu. 

Thanks for reading.
when the kernel is upgraded you have to recompile any drivers linked against it.

---

### Post by WA_Garrett on 2009-04-29
> **cyberdork33 said:**
> when the kernel is upgraded you have to recompile any drivers linked against it.

Shi-!!! Okay, I was thinking I might have to do that, but I wasn't sure. I'll go ahead try recompiling the wireless drivers. Thanks.

---

### Post by daveWilliams on 2009-05-15
Yes, I have the same problem and thanks to cyberdook, I've fixed it. 

Thank you so much.

---

### Post by iveand on 2009-05-16
Newbie question: how does one recompile the wifi drivers?

Thanks,

iveand

---

### Post by WA_Garrett on 2009-05-16
> **iveand said:**
> Newbie question: how does one recompile the wifi drivers?

Thanks,

iveand

I'm using Hardy and I used the instructions on this page
[https://help.ubuntu.com/community/MacBook2-1/Hardy]("https://help.ubuntu.com/community/MacBook2-1/Hardy")

There are a few ways to do it. I used Madwifi drivers because I had issues with ath9k. 
It might be a little different for you depending on your computer/ distro.

---

### Post by cyberdork33 on 2009-05-16
> **iveand said:**
> Newbie question: how does one recompile the wifi drivers?

Thanks,

iveand
if you haven't compiled them before you may not need to recompile them (or compile them at all). Please determine your hardware version and follow the appropriate documentation here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

