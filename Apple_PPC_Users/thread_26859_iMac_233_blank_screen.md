---
title: "iMac 233 blank screen"
date: 2005-04-14
forum: Apple PPC Users
---

### Post by xlello on 2005-04-14
hallo,

I've just installed Ubuntu 4.10 on my old iMac 233... everyhing went perfect since final restart...

Now my iMac starts, loads everything but when X starts video turn black... if I press ctrl*alt*f2 console starts and video turns back on....

If I enter user and password (with blank screen) I can ear intro music and so on... but wideo still stays off!!!  ](*,)
Any ideas??

Please help!!!!

Thanx!
    Marco

---

### Post by erkki70 on 2005-04-14
Hi,
Try  ```
sudo dpkg-reconfigure xserver-xfree86
```
Hope this helps.

Cheers,
Erkki

---

### Post by xlello on 2005-04-14
I tried to reconfigure X but after color depth configuration mask the proces quits... is it normal??

anyway I tryed few configurations but no one worked....

Thanx!

---

### Post by Coweater on 2005-10-29
Try checking the refresh rates for the monitor. I've had some trouble with the auto-config on my iMac DV, and just set the horizontal to 60, and vertical to 75-117 which I got from a config I found on google. I suspect it may just be the horizontal that needs changing though.

---

