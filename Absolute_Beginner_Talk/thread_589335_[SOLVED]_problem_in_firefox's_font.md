---
title: "[SOLVED] problem in firefox's font"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-10-24
i have a problem firefox's font
when i installed 7.04, i found this post very useful
[http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)
because i have accustomed to the font of microsoft
but after i've upgraded to 7.10, the font become like this: (see the attachement)
so i do the same trick again. this time it works after i log out and log in. but when i restart the computer, the font return to it's ugly type again. 
anybody can help me about this?

---

### Post by forestpixie on 2007-10-24
have you tried changing the fonts in firefox - seems to work ok for me

And I use the same xml for mine

---

### Post by kerry_s on 2007-10-24
turn off bitmapped fonts
in terminal->
**sudo dpkg-reconfigure fontconfig-config**

---

### Post by afeasfaerw23231233 on 2007-10-24
forestpixie:
what does xml means? which font should i choose?

kerry_s:
i think  bitmapped fonts have been turned off before i ran this command. so i think it is not related to that ugly font. here's the screenshot

---

### Post by forestpixie on 2007-10-24
xml means -  Extensible Markup Language 

but that's beside the point - in the [thread]("http://ubuntuforums.org/showthread.php?t=208396") you found useful - did you follow the first post - because that's what I do.

as far as fonts go in firefox - this is what I have in screenshot

---

### Post by afeasfaerw23231233 on 2007-10-24
after i tried your setting and return to my own setting, the font becomes my desire one. really strange.but thanks anyway here's my screenshot

---

### Post by forestpixie on 2007-10-24
stranger things happen at sea :) glad you're ok anyway

---

