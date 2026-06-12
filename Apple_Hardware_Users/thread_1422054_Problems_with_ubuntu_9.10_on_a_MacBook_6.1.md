---
title: "Problems with ubuntu 9.10 on a MacBook 6.1"
date: 2010-03-04
forum: Apple Hardware Users
---

### Post by trx902001 on 2010-03-04
Hi all,

        I'm new here and earlier today i finished triple booting my MacBook 6.1 with Mac OS, Windows 7 Ultimate, and ubuntu 9.10. After I Installed I tried a few things out and when I got to the wireless internet, it didn't work. So all day I have been searching through forums and the os website and google and found solutions but none of them have come to work. The one I thought would've been a sure thing was downloading the 802.11 Linux STA driver, since it supports my wireless card (broadcom  14e4: 4353). I went through the read me a few times, following both the instructions for installing the driver, and activating it if it was already built in. Both went unsuccessful, when I try to update it gives me 15 items that couldn't update, and when I try to install the driver following the step by step instructions, some error codes come up saying that it can't be installed cause the destination is locked. Also, the driver wasn't already built in, it had a different mcbwl one that I couldn't do anything with. So after countless hours of searching for how to do it I figured I would post this on here. I'm sorry if this has been asked already elsewhere, but I've tried everything I've found. I'm not sure if I went wrong in the install of ubuntu, but I am in need of some serious help. So whether I missed a little simple thing to make this work, or I'm going about this the completely wrong way, any help at all will be greatly appreciated.
 
                                                                                                                   Thanks in advance,
                                                                                                                   Ryan

---

### Post by alexmurray on 2010-03-05
Try installing the bcmwl-kernel-source package instead (load Synaptic Package Manager and search for it).

---

### Post by trx902001 on 2010-03-07
Oh wow. That worked perfectly thank you soooo much

---

