---
title: "HDTV BIG Problem (ATi)"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by WickedSkin on 2007-04-22
Hi!

Now I have a problem. My Ubuntu desktop won't show up after I've installed the driver.

1. I installed Ubuntu and every thing worked fine. 

2. Then I installed the ATi driver. And everything works until I edit my xorg.conf (as you are supposed to) and set "fglrx" in Driver section (instead of "ATI" you know). Now I will only see the Ubuntu loadscreen on bootup but the Login Screen never showes up.

3. I plugged in my friends monitor and it works! I could even run beryl no problem. But when I use my Samsung 27" HDTV as my screen it doesn't. I can revert my xorg.conf to the backup and it works but not when I run fglrx.

So Linux works fine on PC monitor but not on my HDTV. Windows XP works no problem. I need help sins I'd rather run Ubuntu.

---

### Post by nonewmsgs on 2007-05-06
does thew xorg wizard help anything?  also please post the two xorg.conf files.

---

### Post by freebird54 on 2007-05-06
Do you have the specifications of the big Monitor?  What settings does XP use when using it?  (especially vertRefresh and resolution).  With those we can probably create an xorg.conf that will match up OK...

EDIT:  I had another thought - how is it being hooked up?  The 'composite' out is not functioning in the fglrx drivers...

---

