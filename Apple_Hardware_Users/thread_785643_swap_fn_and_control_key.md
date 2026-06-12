---
title: "swap fn and control key"
date: 2008-05-07
forum: Apple Hardware Users
---

### Post by schtibe on 2008-05-07
Hello

I'd like to swap the fn key and control key on my macbook. However, xev doesn't show me any keycode for the fn key, so I can't use xmodmap to do it. Is there any other way?

I tried to set /sys/module/hid/parameters/pb_fnmode to 0x01 and 0x02, but it doesn't work either way.

I use kubuntu 8.04, 2.6.24-16-generic kernel.

cheers

---

### Post by rebelDNS on 2009-04-26
Hello,

I just got a Macbook Pro and installed 9.04, and this would be extremely helpful.  I really don't like the whole fn-ctrl layout and any solution would be greatly appreciated.

---

### Post by _mario_ on 2009-04-27
> **schtibe said:**
> Hello
I'd like to swap the fn key and control key on my macbook. However, xev doesn't show me any keycode for the fn key, so I can't use xmodmap to do it. Is there any other way?

I tried to set /sys/module/hid/parameters/pb_fnmode to 0x01 and 0x02, but it doesn't work either way.


the kernel doesn't output the FN-key as a key of its own, so you're probably out of luck without patching the driver. the pb_fnmode only changes the default behaviour of the function keys.

ciao,
Mario

---

### Post by WindPower on 2009-09-29
[DoubleCommand](http://doublecommand.sourceforge.net/features.html) allows the fn key to be used as a Ctrl key on OS X, so there has to be a way to do that in Ubuntu as well.

---

### Post by hotbdesiato on 2009-10-12
I hope as well there is a solution, since especially for emacs'ing I need that left ctrl key where the fn key is.

---

### Post by Pifilatakanemu on 2010-10-06
any news on this topic?


thanks!

---

### Post by disappearedng on 2010-12-10
Any new on this topic? I am really interested to find out too. 
My left pinky is killing me.

---

### Post by Pifilatakanemu on 2010-12-28
*push*


I would love to switch both keys. I get a cramp every time I want to þaste something in the terminal...

---

### Post by Lusse on 2011-01-18
I would also really like to swap my ctrl and fn keys, it should be possible thru the apple-hid kernel module.

In the meantime I use this Xmodmap-settings, it'll map the left apple-key to ctrl and the right apple-key to alt-gr. This allows for at least less pain in the fingers.

$ cat ~/.Xmodmap
```

remove mod4 = Super_R
add mod5 = Super_R

remove mod4 = Super_L
add control = Super_L
```

---

### Post by kilaka on 2011-03-14
Look here:
[https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard)

---

### Post by WindPower on 2011-03-14
> **kilaka said:**
> Look here:
[https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard)

That doesn't help inverting the "fn" and "control" keys :(

---

