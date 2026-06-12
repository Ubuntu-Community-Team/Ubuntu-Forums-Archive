---
title: "[SOLVED] keyboard backlight and brightness controls"
date: 2007-10-20
forum: Apple Intel Users
---

### Post by Monsoonx27 on 2007-10-20
I have Gutsy on my new macbook pro

The following are not working and I cannot find anything posted on how to fix them specifically. Only info on Feisty.

Backlight on the keyboard does not work cannot control it with F8-F9

Cannot control the brightness of the display with F1 and F2
 and it does not dim when in a dark area which means the light sensor isn't working.




They are not major issues but I would like to get them solves. Any ideas would be helpful.
I know its something to do with HAL and
 /usr/share/hal/fdi/policy/10osvendor/10-macbookpro-utils.fdi
but I dont know what to change.

---

### Post by [woodstock] on 2007-10-20
Did you already installed "pommed"? The function keys should work then. See /etc/pommed.conf for options.

---

### Post by Monsoonx27 on 2007-10-20
Thanks, it worked perfectly. I just didnt know about it.

---

