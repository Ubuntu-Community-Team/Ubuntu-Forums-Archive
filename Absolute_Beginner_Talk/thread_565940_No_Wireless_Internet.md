---
title: "No Wireless Internet"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Palixia on 2007-10-02
Today I installed Ubuntu on my other computer (A Dell w/ Intel, and Generally Windows XP), and when I went to open up Firefox,it told me I had no wireless internet connection. I would really like some help on either getting internet, or getting back to Windows XP.

Thanks if possible,
Palixia.

---

### Post by jimrz on 2007-10-02
> **Palixia said:**
> Today I installed Ubuntu on my other computer (A Dell w/ Intel, and Generally Windows XP), and when I went to open up Firefox,it told me I had no wireless internet connection. I would really like some help on either getting internet, or getting back to Windows XP.

Thanks if possible,
Palixia.

think we are going to need a bit more info in order to try to help.

 - please post your computer specs, model# / wfi card model and chipset

 - did you tell the installer to use the entire drive, or did you manually partition the drive during install?

---

### Post by anewguy on 2007-10-02
Go to a terminal window (applications/accessories/terminal) then type in the following  and copy/paste the output back in to a reply here.  We'll have an idea of what we are looking at then.:)

lspci


Then type the following in and copy/paste the output back into the same post:

ls /boot



Wireless is usually one of those things which doesn't work "out of the box" but the solution is usually quite simple and fast.:)

---

