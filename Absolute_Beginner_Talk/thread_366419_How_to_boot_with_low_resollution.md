---
title: "How to boot with low resollution"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by jrd on 2007-02-20
What command do I pass with grub to make the system boot with low resolution? My problem is the res is too high for my monitor and so it just goes black after boot. 800x600 would be good.
Thanks in advance.

---

### Post by ed-j on 2007-02-20
Caution: Reply from Novice!

Try[COLOR="DarkOrange"] sudo dpkg-reconfigure xserver-xorg[/COLOR] either in a Terminal or press "esc" when the Grub is loading and go in through recovery mode. Either way, you will find the choices to restrict your resolution. Hope this helps!

---

### Post by overdrank on 2007-02-20
Well I had the same problem when I attached my lcd screen to a new installed ubuntu machine. So I was able to use another monitor to the machine and turn down the resollution. When I hooked back up to the lcd screen I recieved the same errror and then just waited and the systems video came up. Hope this will help a little. Just wait a few mins and let ubuntu try.

---

