---
title: "did I break it"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by swashbuckl6oz on 2006-10-22
after tying to get my side buttons to work on my mouse, ubuntu would no longer boot into gui and now, after doing sudo /etc/init.d/gdm start i got the gui working but i got these errors
[[IMG]http://img108.imageshack.us/img108/1207/screenshotjp0.th.png[/IMG]](http://img108.imageshack.us/my.php?image=screenshotjp0.png)
[[IMG]http://img107.imageshack.us/img107/8992/screenshot1fi2.th.png[/IMG]](http://img107.imageshack.us/my.php?image=screenshot1fi2.png)
someone please help

---

### Post by Dr. Nick on 2006-10-23
Those 2 errors look like its booting into failsafe gnome, not regular gnome. click through them then do ctrl+alt+backspace to get to the login screen and select gnome from the session and login. Or restart if you have it set not to autologin.

---

### Post by tubasoldier on 2006-10-23
I did the same thing to my computer and got the same results. It seems that it did not work with xorg as it was said to. It may just be the hardware. I would reccomend replacing your current xorg with your backed up one. I assume you backed it up before you changed it? If not then you should follow the howto that you used to remove the changes.

---

