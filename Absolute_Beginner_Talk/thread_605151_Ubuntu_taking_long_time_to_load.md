---
title: "Ubuntu taking long time to load"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by 01steven on 2007-11-06
Installed Ubuntu a couple of days ago.
Seems to take a long time to load.
Grub loader kicks in quickly, but then blank screen for approx. 3-4 minutes before the Ubuntu log-in screen appears.
Seems a very long time.
Any suggestions?

---

### Post by Pumalite on 2007-11-06
Memory?

---

### Post by Daveski on 2007-11-06
Try dmesg to see the messages generated at boot. Alternatively try CTRL-ALT-F1 when the Ubuntu splash screen shows up. CTRL-ALT-F8 or CTRL-ALT-F7 usually kicks me back to the text messages scrolling up the screen during boot. This should show you where the delay is.

---

### Post by john262 on 2007-11-06
It's a bug in version 7.10. A lot of people have raised this issue.

---

### Post by davidsotl on 2007-11-06
if you don't see the splash while booting, (the big Ubuntu logo with a progress bar under it)then you probably have the same problem I had, I'm sure someone posted a solution but I just can't find it. so this is what I did to solve the problem: 

the system won't start properly because you had the wrong resolution for the splash . changing one of the configuration file can solve the problem but I don't know which one, so instead, I installed "startup manager" from the package manager, from there you can choose the correct resolution for you monitor, restart, you should see the difference.

if you didn't use the guided installation while install Gusty, make sure your windows partition ( I assume most of you have one or more) are not mounted automatically, because that's another reason for the slow booting. 

hope this helps

---

### Post by Bigbird999 on 2007-11-06
[http://ubuntuforums.org/showthread.php?t=579684&page=2&highlight=splash+screen](http://ubuntuforums.org/showthread.php?t=579684&page=2&highlight=splash+screen)

This thread has the fix
BB

---

