---
title: "Macbook Wireless not working"
date: 2008-07-14
forum: Apple Hardware Users
---

### Post by WinterWeaver on 2008-07-14
Hi there,

I followed the Ubuntu Macbook wiki to set up my macbook wireless, but with no success. I've tried both the MadWifi and Windows Drivers.

Currently I have NdisWrapper with the NET5416 drivers (as the wiki indicated), but the NdisWraper tool indicates that the hardware is not present

Does anyone have any ideas what to do?

I have a Macbook 4.1, running Ubuntu 8.04 (Hardy)

Thanks for any help.

WW

---

### Post by apaukalypse on 2008-07-14
Take a look through this thread and see if it helps you out.

[http://http://ubuntuforums.org/showthread.php?t=800265]("http://http://ubuntuforums.org/showthread.php?t=800265")

-apauko

---

### Post by guzzos on 2008-07-14
> **WinterWeaver said:**
> Hi there,

I followed the Ubuntu Macbook wiki to set up my macbook wireless, but with no success. I've tried both the MadWifi and Windows Drivers.

Currently I have NdisWrapper with the NET5416 drivers (as the wiki indicated), but the NdisWraper tool indicates that the hardware is not present

Does anyone have any ideas what to do?

I have a Macbook 4.1, running Ubuntu 8.04 (Hardy)

Thanks for any help.

WW


I have exactly the same problem as yours.  I tried everything even compiling new kernels without luck.  Mine is a Macbook 4,1 with the broadcom 43xx rev 3 running Ubuntu Hardy.  Also I am unable to hear anything from the speakers.  If you find a solution please let me know.

---

### Post by WinterWeaver on 2008-07-15
I found the solution.

running the command lspci, I discovered that I have a broadcom network card.

So I decided to try and use the Bootcamp Broadcom XP driver, and voila!

Wireless is now working.

Give that a go Guzzos ^_^

ta

WW

---

### Post by cyberdork33 on 2008-07-15
Yes, atheros was only in early macbooks. You wiki page is here:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

