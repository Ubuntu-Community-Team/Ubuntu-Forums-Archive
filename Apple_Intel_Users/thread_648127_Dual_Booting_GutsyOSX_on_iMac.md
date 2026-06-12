---
title: "Dual Booting Gutsy/OSX on iMac"
date: 2007-12-23
forum: Apple Intel Users
---

### Post by mattr01 on 2007-12-23
Hi.  I have purchased a 20in iMac (mid-range model, not here yet), and I want to dual boot either Kubuntu or Ubuntu Gutsy (haven't decided yet) and Mac OSX.

I have a few questions regarding this:

[LIST=1]
[*]Can I run 64 bit Ubuntu on the iMac?
[*]If yes, is there any benefit to doing so?
[*]Should I use Boot camp to dual boot the two OSes?
[*]Can I choose how big the Ubuntu partition is with Boot Camp?
[*]Are there any specific things that I need to do during installation?
[*]How do I get wifi, isight, apple remote and any other important iMac hardware working in gutsy?
[*]What screen resolution should I choose in gutsy on the iMac?
[/LIST]

---

### Post by Zaff on 2007-12-23
> 
   1. Can I run 64 bit Ubuntu on the iMac?

Imac run 64bits processors as far as I know, so I would say yes but you might wanna make sure.
> 
   2. If yes, is there any benefit to doing so?

The benefit as far as i know is not exactly noticeable (I'm not running 64 so I can't really judge) and it depends on what you're going to use you imac for. 
> 
   3. Should I use Boot camp to dual boot the two OSes?

Yep, I guess you could use gparted but bootcamp is integrated in Leopard now so it makes sense to use it.
> 
   4. Can I choose how big the Ubuntu partition is with Boot Camp?

Yes, Bootcamp asks you the size of partition you want.
> 
   5. Are there any specific things that I need to do during installation?

Dunno but I'm guessing it's just the regular Mac installation. There's a FAQ on this forum, check it out. Read about rEFIt if you wanna dual boot. Also I would advise you to do the windows driver cd when bootcamps asks you, that way if you need to use ndiswrapper you'll have the wifi driver on the disk.
> 
   6. How do I get wifi, isight, apple remote and any other important iMac hardware working in gutsy?

The apple remote worked natively for me. If it doesn't (but I see no reason why) check out keytouch and keytouch editor. They're utilities to configure particular keys.
Otherwise wifi should be easy to set up (if it doesn't activate by itself). Check out ndiswrapper if it doesn't work natively (don't forget to burn the windows driver cd).
The isight should work now if you follow this how-to : [http://ubuntuforums.org/showthread.php?t=491381&highlight=isight](http://ubuntuforums.org/showthread.php?t=491381&highlight=isight)
> 
   7. What screen resolution should I choose in gutsy on the iMac?

I would say the native resolution. Not sure why you're asking this though, just use the resolution you feel more comfortable with.
[QUOTE]

Finally I would say I haven't used an iMac so you might wanna ask someone who has but there should be no problem for most of it. The only issue you may come across is wifi not natively supported so make sure you have an ethernet connection handy for set up.

---

### Post by krymphus on 2007-12-23
If you are able to it would be interesting to find out.

---

