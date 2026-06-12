---
title: "[SOLVED] Disable MIddle Click Past Function"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by amrclutch1 on 2007-07-16
How can I disable the middle click paste function on my mouse wheel, sometimes I accidentally press it and it pastes things. It gets pretty annoying. I hate it with a great passion.

---

### Post by wolfen69 on 2007-07-16
what kind of mouse is it?

---

### Post by amrclutch1 on 2007-07-16
The mouse is a Logitech G7 Gaming Mouse (Wireless) ;)

---

### Post by wolfen69 on 2007-07-16
unfortunately, this may be something that you have to live with. after some research, i was unable to find any answers. anyone else?

---

### Post by amrclutch1 on 2007-07-16
I would imagine there would be a way that you just don't know. After all it is open source but I won't compile ubuntu just to remove that. No big deal, if someone else knows great, but if not oh well. :)

---

### Post by yabbadabbadont on 2007-07-16
If you just want to disable it while using firefox, then go to Edit->Preferences->Advanced (tab) and enable the "Use Autoscrolling" option.

---

### Post by amrclutch1 on 2007-07-16
Thanks! The only part that bothered me was the part in firefox really. Again, thanks alot! :D

---

### Post by bodhi.zazen on 2007-07-16
Edit /etc/X11/xorg.conf

In the device section for your mouse add (modify) these lines :

>     Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 3"

Restart X (log out and back in)

---

### Post by Al3xK3aton on 2007-07-16
You can get a new mouse, one with a scroller that is harder to click. Some trackballs make in very difficult to press by accident.

---

### Post by amrclutch1 on 2007-07-16
This one is hard to click it is just that the scroll wheel moves left and right easily and that presses it. I have the problem fixed, thanks for all of your suggestions :)

Actually I will take out the modified stuff from xorg.conf, now I can't middle click links to open them in a new tab, I do that often, unless there is a fix for that too.

---

