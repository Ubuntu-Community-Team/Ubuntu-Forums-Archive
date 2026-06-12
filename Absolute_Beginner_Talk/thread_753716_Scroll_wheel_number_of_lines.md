---
title: "Scroll wheel number of lines"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by flux_user on 2008-04-13
Hello,
I am having a small issue with changing the number of lines when I use the scroll wheel.  I have searched and found this entry for xorg.conf

Option "VertScrollDelta" "6"

However this entry doesn't seem to change the number of lines.   Any thought and opinions would be greatly appreciated.

---

### Post by Aphox on 2008-04-13
Well, I have no clue how to help you on this one, but if you want to change it for FireFox, type in about:config in the address bar, look for "mousewheel.withnokey.action" and set it to "1" and then look for "mousewheel.withnokey.numlines" and set the value to "6" or whatever your scroll speed preference is.

---

### Post by pbpersson on 2008-04-13
Don't forget that the XServer will not pick up the new values unless you stop and start it

---

### Post by thebigbluecan on 2008-04-13
> **Aphox said:**
> Well, I have no clue how to help you on this one, but if you want to change it for FireFox, type in about:config in the address bar, look for "mousewheel.withnokey.action" and set it to "1" and then look for "mousewheel.withnokey.numlines" and set the value to "6" or whatever your scroll speed preference is.

mmm That didn't work for me... It scrolls one page when it is set to one and the other six... I also tried changing the value to other #'s but no avail :(

---

