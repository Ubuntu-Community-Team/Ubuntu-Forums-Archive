---
title: "laptop boot problems"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2008-01-26
i have toshiba satelite m45-s305 laptop, it dual boots ubuntu/xp great, but i was trying to use my desktop screen with it, and apparently it isnt capable of dual screening, and i went to turn it on and it wont load the GUI and goes straight to the command line, after displaying a message saying "kinit image not found: doing normal boot"

how do i get my laptop back to how it was before i tried using the screen
(btw screen is a NEC accusync LCD223wxm)

---

### Post by mikeyphi on 2008-01-28
> **antisocialist said:**
> i have toshiba satelite m45-s305 laptop, it dual boots ubuntu/xp great, but i was trying to use my desktop screen with it, and apparently it isnt capable of dual screening, and i went to turn it on and it wont load the GUI and goes straight to the command line, after displaying a message saying "kinit image not found: doing normal boot"

how do i get my laptop back to how it was before i tried using the screen
(btw screen is a NEC accusync LCD223wxm)

Try this:
At the command line prompt enter:
sudo dpkg-reconfigure xserver-xorg

you will see several pages of text asking questions - accept the default option, unless you know better! Make sure to pay close attention about the screen option.

When it's finished you should be back to a command prompt - enter:
startx

Hopefully that will give you the screen back.

---

