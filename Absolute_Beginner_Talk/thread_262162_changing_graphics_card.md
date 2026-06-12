---
title: "changing graphics card"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by rarstar on 2006-09-21
hi all

there are plenty of posts about getting graphics cards to work, installing drivers, etc for new installs but i can't find any about upgrading a graphics card

i've just ordered a new one... do i need to install drivers before i put it in.. or do i put it in and then try to set it up (presumably gnome will be broken due to the wrong drivers being installed)?

cheers,
rar

---

### Post by bodhi.zazen on 2006-09-21
Depends on the card. You should install the card and follow a how to if you use a nvidia card.

---

### Post by rarstar on 2006-09-21
yeah, it's an nvidia... will it try to autodetect it like it does when you install?

---

### Post by bodhi.zazen on 2006-09-21
You will likely get a display on your monitor after you change the card. You will need to install some software. You can try the open source drivers, but I just installed the nvidia driver as my card was not supported by the open source driver (which is unusual as most are).

Start here:

[How to install Nvidia driver](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

If that is not working:

[Nvidia drivers](http://www.nvidia.com/object/unix.html)

So then:[list=number][*]Install your new card.
[*]Leave your monitor connected to the old card.
[*]Install nvidia drivers with"Method 1".
[*]Shutdown, move monitor to nvidia card.
[*]Boot.
[*]If that does not work, use method 2 with my nvidia link to download driver.[/list]

---

### Post by b_martinez on 2006-09-21
> **rarstar said:**
> hi all

there are plenty of posts about getting graphics cards to work, installing drivers, etc for new installs but i can't find any about upgrading a graphics card

i've just ordered a new one... do i need to install drivers before i put it in.. or do i put it in and then try to set it up (presumably gnome will be broken due to the wrong drivers being installed)?

cheers,
rar

What kind of card do you have now? You may have to un-install any proprietary (i.e. Matrox, SIS, ATI,etc..)driver from your current kernel. If you already have an Nvidia card, you may only need to run a cofiguration command. It depends on the cards.
Bill

---

