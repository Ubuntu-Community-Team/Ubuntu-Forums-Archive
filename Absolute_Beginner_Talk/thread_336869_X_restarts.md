---
title: "X restarts"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by h4m574h on 2007-01-12
Hello!

I don't know what is happening, but all of the sudden my Ubuntu Edgy Eft restarted (like if I used shutdown -r now) and now, it restarts X at random moments. First I tought it's just when trying to run an OpenGL application, but now I see it restarts just like that. Does anyone have the solution to my problem?

---

### Post by kj1h234lkj1234 on 2007-01-12
What does /var/log/Xorg.0.log say?

I had a problem with "random" X11 reboots after installing XGL a few months ago. Because of the weird stuff it did with the keymap, shift + backspace became the equivalent of control-alt-backspace for some reason. :mad:

I haven't had any problems lately though. (plus I'm using beryl now, since it's better) :)

---

### Post by h4m574h on 2007-01-12
I have neither Xgl nor Beryl.

Since it's a rather long file I uploaded it here [C-L-I-C-K]("http://h4m574h.50webs.com/Xorg-0.log")

---

### Post by h4m574h on 2007-01-12
Solved the problem with a simple reinstall of the driver.

---

