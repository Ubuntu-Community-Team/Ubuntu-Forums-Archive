---
title: "X-Server to Screen Resolution to Failed Login"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-03-14
Ok so on [this post]("http://www.ubuntuforums.org/showthread.php?t=384569") I went from last night switch my xorg to VESA due to myself making a mistake in the xorg file, to then having a default state of a lower resolution.  On the above mentioned post I went into xorg again and changed the refresh rate and resolution of my monitor in accordance to the monitor settings I found in the online manual.

Now, when I boot I get to the login screen, I enter my user name and password and the screen goes blank, appears to attempt a login and just goes back to the login screen.

Note:  I faintly remember this login screen saying it needs a lower screen resolution.

---

### Post by siciliancasanova on 2007-03-14
bump

---

### Post by siciliancasanova on 2007-03-15
bump

---

### Post by seshomaru samma on 2007-03-15
What you can do is boot into rescue mode and reconfigure X
```
dpkg-reconfigure xserver-xorg

```
you have a rescue mode in your grub menu when you boot (you might need to press esc to see the menu during boot)
if you don't know your specs - you shoudl either google or (the lazy ,yet time consuming method) download Knoppix - it's hardware detection is usually very good. It also prints your specs as it boots .
([http://www.knoppix.org/](http://www.knoppix.org/))
googling is the better option cause if for somereason knoppix fails you will be very frustrated, nevertheless ,knoppix is a great tool and downloading it is a wise move anyway.

---

### Post by siciliancasanova on 2007-03-15
Actually I have a copy of knoppix sitting in front of me, HOWEVER, I just decided to make the switch to Feisty Fawn.  So thank you for your response anyway :)

---

