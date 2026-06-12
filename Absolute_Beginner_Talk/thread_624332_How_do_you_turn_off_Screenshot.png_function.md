---
title: "How do you turn off Screenshot.png function?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by dolecannery on 2007-11-26
I would like to turn off the automatic screenshot function.  I installed ubuntu 7.04 on a Compaq Presario 2100 laptop, when I download updates, repetitive screenshot.png messages appear not permitting me to cancel and ultimately freezing the laptop.   How can I turn off the automatic screenshot function before I install the updates.

---

### Post by Nano Geek on 2007-11-26
Do you mean the take screenshot function. That shouldn't go off by itself.
Maybe your button got jammed. If it isn't then I will try to find instructions for disabling it.

---

### Post by jordanmthomas on 2007-11-26
A quick (and not probably the best) solution is to make gnome-screenshot not executable.
```
sudo chmod -x `which gnome-screenshot`
```
If you ever want to re-enable, just change -x to +x

Also, look in your keyboard shortcuts and try turning it off there.  
system --> preferences --> keyboard shortcuts

---

