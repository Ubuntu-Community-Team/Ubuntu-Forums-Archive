---
title: "problems with wireless"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by debi on 2007-01-27
I have read a lot of the forums and see that a lot of people are having problems with wireless. I have a buffalo wireless usb, and i cant seem to get it to work. I dont know if i am downloading the wrong drivers. what ever i install it tells me that it is an invalid driver. although it is buffalo, it says i can use the linksys WUSB54G driver but that didnt work. I tried a driver from the windows cd, but honestly im not sure which one to install. has anyone had any luck with buffalo??

---

### Post by t341 on 2007-02-13
> **debi said:**
> I have read a lot of the forums and see that a lot of people are having problems with wireless. I have a buffalo wireless usb, and i cant seem to get it to work. I dont know if i am downloading the wrong drivers. what ever i install it tells me that it is an invalid driver. although it is buffalo, it says i can use the linksys WUSB54G driver but that didnt work. I tried a driver from the windows cd, but honestly im not sure which one to install. has anyone had any luck with buffalo??

I am going to try to use a Buffalo wli-u2-kg54-ai adapter with the
rt2570 drivers here:
[http://sourceforge.net/project/showfiles.php?group_id=107832](http://sourceforge.net/project/showfiles.php?group_id=107832)

If it works I'll post the results.

---

### Post by sardion on 2007-02-13
If that works, awesome, and please do post to let people know.

I think you may need to use the ndiswrapper driver (which lets you use the windows driver).  You should have a CD that came with the wireless card that has the windows driver but if not you can probably download it from the buffalo website.

Lots of people have explained ndiswrapper here so I won't.

---

### Post by t341 on 2007-02-13
> **sardion said:**
> If that works, awesome, and please do post to let people know.

I think you may need to use the ndiswrapper driver (which lets you use the windows driver).  You should have a CD that came with the wireless card that has the windows driver but if not you can probably download it from the buffalo website.

Lots of people have explained ndiswrapper here so I won't.


I read on the forums [http://rt2x00.serialmonkey.com/phpBB2/viewforum.php?f=4](http://rt2x00.serialmonkey.com/phpBB2/viewforum.php?f=4)
that the rt 2570 drivers I linked are Linux drivers and don't need a wrapper and that
they are supposed to support wpa/tkip encryption

The last post on this thread even has a patch to enable wpa/aes encryption.
[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3148&start=0&postdays=0&postorder=asc&highlight=](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3148&start=0&postdays=0&postorder=asc&highlight=)

I don't know what model Buffalo USB adapter the first post refers to,  but if it
compatible with a linksys WUSB54G then it must be a Ralink chipset like the
wli-u2-kg54-ai I have.

---

### Post by t341 on 2007-02-13
If anyone with a Buffalo wli-u2-kg54-ai reads this post and tries it, make 
sure you have the auto-driver install switch turned off on this adapter.

---

