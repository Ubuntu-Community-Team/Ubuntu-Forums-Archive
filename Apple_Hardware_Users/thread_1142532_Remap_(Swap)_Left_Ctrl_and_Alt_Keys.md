---
title: "Remap (Swap) Left Ctrl and Alt Keys"
date: 2009-04-29
forum: Apple Hardware Users
---

### Post by vb.bajpai on 2009-04-29
I am used to using the command key, which is positioned at the alt key location. On Ubuntu, I would like to swap the left ctrl and alt keys to get a better mac user experience. I have searched the forum for a similar post, but it was quite old and suggested to use 'xmodmap' to remap the keymaps. I am wondering if its now possible directly from the keyboard preferences, since I see the viable option to choose a Apple Keyboard, but cannot find a option to swap the keys. (I am on Intrepid Ibex).

---

### Post by mercurysquad on 2009-04-30
You're doing it wrong. You should remap the keys in OS X keyboard preferences so that Ctrl = Cmd and Alt = Option. That way you can do Ctrl+C, Ctrl+V etc. on any OS &#8212; even if you use someone else's computer which is not customized to your tastes.

---

### Post by mail2vita on 2010-10-09
Well, IMO there is actually a good reason behind Apple's decision to place Cmd key where they placed it and having most of the functionality bound to that key - and that is the ergonomics. It's soooo much easier to press the Cmd key (or Alt key on standard PC keyboard) with your your left-hand's thumb than trying to reach the Ctrl key, which is usually hidden under your palm.

Anyway, I don't  care that much about others tastes and definitely don't want to advocate my taste. But I would really appreciate if somebody could actually answer the original question, please.

Thanks a lot!

---

### Post by inphektion on 2010-10-09
i've used xmodmap with no issues in the past and i think its still a valid way.  This [http://linuxtidbits.wordpress.com/2008/04/19/apple-keyboards-in-linux/](http://linuxtidbits.wordpress.com/2008/04/19/apple-keyboards-in-linux/) seems to say you can do in xorg.conf as well.  I assume use xev to get the name.  maybe try xorg first and if it doesn't work out xmodmap would be the only other way i can think of.

---

