---
title: "Wine - Unreadable System Fonts"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by marklid on 2007-01-07
Hi,

I have Wine installed on Edgy and any time it needs to show the default Windoze fonts they are tiny and unreadable (see attached screehshot of winecfg for example).

I have tried purging Wine, deleting ~/.wine but still the problem remains.... does anyone know how to sort this one out ?

Cheers

Mark.

---

### Post by marklid on 2007-01-09
Anyone ?:confused:

---

### Post by emmet on 2007-01-26
Hello,

I had the same problem this afternoon. My wife commented that the fonts on the title and menu bars for Internet Explorer were way too small for her to read.

To change them, you need to run regedit under wine. 

Look at this key: 

HKEY_LOCAL_MACHINE > System > CurrentControlSet > Hardware Profiles > Current > Software > Fonts > LogPixels

If you change the value of LogPixels (in decimal) to something larger, then when you run windows applications under wine, then fonts will look bigger.

My original value was 96 (decimal) and now it is 140 and a lot easier to read.

I hope this helps, 

Best regards

Emmet

---

### Post by RomeReactor on 2007-01-26
Did you install msttcorefonts when you installed wine? If not, then

```
sudo apt-get install msttcorefonts
```

might help.

---

### Post by Patrick K on 2007-02-06
RomeReactor, how did you get the fonts to work in Wine? Can they just be dumped into Wine's Windows' font directory?

---

### Post by RomeReactor on 2007-02-06
> RomeReactor, how did you get the fonts to work in Wine?

I just installed them; didn't have to fiddle with winecfg or anything, IIRC.

> Can they just be dumped into Wine's Windows' font directory?

I don't know if dropping them there works. Might be worth a try...

---

### Post by marklid on 2007-02-06
Thanks for the replies to my original post. I managed to get the fonts working OK by copying the contents of the fonts folder from an XP installation to the fonts folder in the Wine C drive and all was OK.
Since then I had to do a complete reinstall (moral of the story, don't use the command line when half asleep first thing in the morning before work). When I installed wine this time all was OK from the start.

---

